---
title: "Gestire il caricamento di progetto in una soluzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "soluzioni, la gestione di caricamento progetto"
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Gestire il caricamento di progetto in una soluzione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Soluzioni di Visual Studio possono contenere un numero elevato di progetti. Il comportamento di Visual Studio predefinito consiste nel caricare tutti i progetti in una soluzione al momento che dell'apertura della soluzione e non consentire all'utente di accedere a tutti i progetti fino al completamento del caricamento di tutti gli elementi. Quando il processo di caricamento progetto durerà più di due minuti, viene visualizzato un indicatore di stato che mostra il numero di progetti caricati e il numero totale di progetti. L'utente può scaricare progetti mentre si lavora in una soluzione con più progetti, ma questa procedura presenta alcuni svantaggi: non vengono generati i progetti scaricati come parte di un comando Ricompila soluzione e le descrizioni di IntelliSense dei tipi e membri di progetti chiusi non vengono visualizzati.  
  
 Gli sviluppatori possono ridurre i tempi di caricamento soluzione e gestire il comportamento di caricamento tramite la creazione di un carico soluzione responsabile di progetto. Il carico di gestione di soluzioni possa impostare progetto diverso, il caricamento di priorità per progetti specifici o tipi di progetto, assicurarsi che i progetti vengono caricati prima di avviare una compilazione in background, ritardare il caricamento in background fino al completamento di altre attività in background ed eseguire altre attività di gestione di carico.  
  
## Caricamento di priorità di progetto  
 Visual Studio definisce i quattro livelli di priorità di progetto diversi caricamento:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> \(predefinito\): quando viene aperta una soluzione, i progetti vengono caricati in modo asincrono. Se questo livello di priorità è impostata su un progetto scaricato dopo la soluzione è già aperta, il progetto verrà caricato al successivo punto di inattività.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: quando viene aperta una soluzione, i progetti vengono caricati in background, consentendo all'utente di accedere ai progetti come vengono caricati senza attendere che tutti i progetti vengono caricati.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti vengono caricati quando vi si accede. Un progetto viene eseguito quando l'utente espande il nodo del progetto in Esplora soluzioni, quando viene aperto un file che appartengono al progetto quando si apre la soluzione perché è nell'elenco documento aperto \(persistente nel file della soluzione user\) o quando un altro progetto che è sottoposto il server presenta una dipendenza del progetto. Questo tipo di progetto non viene caricato automaticamente prima di avviare un processo di compilazione. il carico soluzione di gestione è responsabile di garantire che tutti i progetti necessari siano stati caricati. Questi progetti devono essere caricati anche prima di avviare una ricerca e sostituzione in file attraverso l'intera soluzione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: i progetti non devono essere caricati, a meno che l'utente richiede in modo esplicito. Questo avviene quando i progetti vengono scaricati in modo esplicito.  
  
## Creazione di un carico soluzione manager  
 Gli sviluppatori possono creare un carico soluzione manager implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> e Visual Studio che informa che il carico di gestione di soluzioni è attiva.  
  
#### L'attivazione di un manager di carico soluzione  
 Visual Studio consente un solo manager carico soluzione in un determinato momento, pertanto è necessario informare Visual Studio quando si desidera attivare il carico soluzione manager. Se un secondo gestore carico soluzione è attivato in un secondo momento, la gestione del carico soluzione verrà interrotte.  
  
 È necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> del servizio e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà:  
  
```c#  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution; object objLoadMgr = this;   //the class that implements IVsSolutionManager pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### Implementazione di IVsSolutionLoadManager  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> viene chiamato durante il processo di apertura della soluzione. Per implementare questo metodo, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> servizio per impostare la priorità di carico per il tipo di progetto che si desidera gestire. Ad esempio, il codice seguente imposta i tipi di progetto c\# per il caricamento in background:  
  
```c#  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}"); pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> viene chiamato quando Visual Studio viene arrestato o quando un pacchetto diverso ha assunto come la gestione del carico soluzione attiva chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> con la <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> proprietà.  
  
#### Strategie per diversi tipi di gestione di carico soluzione  
 È possibile implementare gestori carico soluzione in modi diversi, a seconda dei tipi di soluzioni che sono utilizzati per la gestione.  
  
 Se il carico di gestione di soluzioni deve gestire soluzioni di caricamento in generale, può essere implementato come parte di un package VS. Il pacchetto deve essere impostato su autoload aggiungendo il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> su VSPackage con un valore di <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Il carico di gestione di soluzioni può quindi essere attivata la <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
> [!NOTE]
>  Per ulteriori informazioni sui pacchetti di caricamento automatico, vedere [Caricamento VS](../extensibility/loading-vspackages.md).  
  
 Poiché Visual Studio riconosce solo la gestione di carico soluzione ultimo da attivare, gestioni carico soluzione generale devono sempre rilevare se esiste un gestore di carico esistente prima di attivare stessi. Se la chiamata a GetProperty\(\) sul servizio soluzione per <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> restituisce `null`, non è disponibile alcun gestore carico soluzione attiva. Se non restituisce null, controllare se l'oggetto è quello utilizzato per la gestione del carico soluzione.  
  
 Se il carico di gestione di soluzioni deve gestire solo alcuni tipi di soluzione, VSPackage possibile sottoscrivere gli eventi di caricamento della soluzione \(chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>\) e utilizzare il gestore dell'evento <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> per attivare la gestione del carico soluzione.  
  
 Se il carico di gestione di soluzioni deve gestire solo le soluzioni specifiche, è possono rendere persistenti le informazioni di attivazione come parte del file di soluzione. A tale scopo, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> per la sezione di pre\-soluzione.  
  
 Gestori di carico soluzione specifica verrà disattivato nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> gestore di eventi, in ordine non in conflitto con altri gestori di carico soluzione.  
  
 Se è necessario un gestore di carico soluzione solo per mantenere le priorità di caricamento progetto globale \(ad esempio, proprietà impostate nella pagina Opzioni\), è possibile attivare la gestione del carico soluzione nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> gestore eventi, mantenere l'impostazione di proprietà della soluzione, quindi disattivare il carico di gestione di soluzioni.  
  
## Gestione degli eventi di carico soluzione  
 Per sottoscrivere gli eventi di caricamento della soluzione, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> quando si attiva la gestione del carico soluzione. Se si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, è possibile rispondere a eventi correlati al progetto diverso priorità di caricamento.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: Viene generato prima dell'apertura di una soluzione. Consente di modificare il progetto di caricamento di priorità per i progetti nella soluzione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: Viene generato dopo che la soluzione è completamente caricata, ma prima di background inizio nuovamente il caricamento del progetto. Ad esempio, un utente potrebbe avuto un progetto la cui priorità di carico è LoadIfNeeded o il carico di gestione di soluzioni potrebbero essere state modificate una priorità di caricamento progetto per BackgroundLoad, che avvia un caricamento in background del progetto.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Viene generato dopo una soluzione è inizialmente completamente caricata, se è disponibile un gestore di carico soluzione. Viene inoltre attivato dopo il caricamento o richiesta di caricamento ogni volta che la soluzione è stata caricata completamente. Allo stesso tempo, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> viene riattivato.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: Viene generato prima del caricamento di un progetto \(o progetti\). Per assicurarsi che gli altri processi in background vengono completati prima che i progetti vengono caricati, impostare `pfShouldDelayLoadToNextIdle` a **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: Viene generato quando un batch di progetti sta per essere caricato. Se `fIsBackgroundIdleBatch` è true, i progetti devono essere caricati in background; se `fIsBackgroundIdleBatch` è false, i progetti devono essere caricati in modo sincrono in seguito a una richiesta dell'utente, ad esempio se l'utente espande un progetto in sospeso in Esplora soluzioni. È possibile implementare questo metodo per operazioni costose che in caso contrario sarebbe necessario eseguire <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: Viene generato dopo il caricamento di un batch di progetti.  
  
## Rilevamento e la gestione di soluzioni e caricamento progetto  
 Per rilevare lo stato di caricamento dei progetti e soluzioni, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> con i valori seguenti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` Se la soluzione e tutti i progetti vengono caricati, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` Se un batch di progetti vengono attualmente caricate in background, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` restituisce `true` Se un batch di progetti vengono attualmente caricati in modo sincrono a causa di un comando dell'utente o altri carico esplicito, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` restituisce `true` Se la soluzione attualmente viene chiuso, in caso contrario `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` restituisce `true` Se una soluzione attualmente viene aperto, in caso contrario `false`.  
  
 È inoltre possibile garantire che i progetti e soluzioni vengono caricate \(indipendentemente dalle priorità di caricamento progetto\), chiamando uno dei metodi seguenti:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: questo metodo forza i progetti in una soluzione di caricamento prima che il metodo restituisce.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: questo metodo forza i progetti in `guidProject` caricare prima il metodo restituisce.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: questo metodo forza il progetto in `guidProjectID` caricare prima il metodo restituisce.  
  
> [!NOTE]
>  . Per impostazione predefinita solo i progetti con la richiesta di caricamento e vengono caricate le priorità di caricamento in background, ma se il <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flag viene passato al metodo, verranno caricati tutti i progetti ad eccezione di quelle che sono contrassegnati per caricare in modo esplicito.