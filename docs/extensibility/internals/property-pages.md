---
title: "Pagine delle propriet&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opzioni di configurazione, la modifica delle proprietà"
  - "proprietà (pagine)"
  - "pagine delle proprietà, modificare le opzioni di configurazione"
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Pagine delle propriet&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli utenti possono visualizzare e modificare il progetto configurazione\-dipendente e \- proprietà indipendenti tramite pagine delle proprietà.  Un pulsante di **Pagine delle proprietà** è stato attivato nella finestra di **Proprietà** o nella barra degli strumenti di Esplora soluzioni per gli oggetti che forniscono una visualizzazione della pagina delle proprietà dell'oggetto selezionato.  Le pagine delle proprietà vengono creati nell'ambiente e sono disponibili per le soluzioni e i progetti.  Possono, tuttavia, anche essere resi disponibili per gli elementi di progetto che utilizzano le proprietà dipendenti dalla configurazione.  Questa funzionalità può essere utilizzata quando i file contenuti in un progetto richiede le impostazioni delle opzioni del compilatore diversi di compilare correttamente.  
  
## Utilizzando le pagine delle proprietà  
 Se una pagina delle proprietà già visualizzare e le modifiche di selezione, ad esempio da una soluzione a un progetto\), le informazioni visualizzate le modifiche delle pagine per visualizzare le proprietà della nuova selezione.  Se non esistono proprietà sull'oggetto che supportano le pagine delle proprietà, la pagina delle proprietà è vuota.  
  
 Se più oggetti sono selezionati, la pagina delle proprietà visualizzerà l'intersezione delle proprietà per tutti gli elementi selezionati.  Se l'elemento selezionato non contiene le proprietà di distribuzione e il pulsante di **Pagine delle proprietà** sulla barra degli strumenti di Esplora soluzioni si fa clic su, cambia lo stato attivo sulla Finestra Proprietà.  Per ulteriori informazioni prevista la Finestra Proprietà e la selezione, vedere [Estensione delle proprietà](../../extensibility/internals/extending-properties.md).  
  
 Se vengono visualizzate le proprietà di più oggetti e modificare un valore in una pagina delle proprietà, tutti i valori per gli oggetti impostati sul nuovo valore anche se era inizialmente diversi e la pagina era spazio vuoto quando le proprietà di un oggetto dell'utente.  
  
 Esistono due tipi di carattere generale su finestre di dialogo di **ProgettoPagine delle proprietà** disponibili in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Nel primo, per i progetti di Visual Basic., ad esempio, le pagine delle proprietà visualizzate tramite un formato di campo, come illustrato nel seguente schermata.  Nel secondo, illustrato più avanti in questa sezione, la pagina delle proprietà contiene una griglia delle proprietà simile a quella presente nella Finestra Proprietà.  
  
 ![Pagina delle proprietà di Visual Basic](../../extensibility/internals/media/vsvbproppages.png "vsVBPropPages")  
Finestra di dialogo pagine delle proprietà del progetto con il formato e la struttura ad albero di campo  
  
 La struttura ad albero nella finestra di dialogo pagine delle proprietà non viene sviluppata utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.  L'ambiente, in base al nome del livello passato da <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> e interfacce di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> , lo compila.  
  
 Sono solo due categorie di primo livello disponibile per le pagine delle proprietà di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] :  
  
-   Proprietà comuni, che visualizza informazioni dell'configurazione\-indipendente per l'oggetto o gli oggetti selezionati.  Pertanto, quando una delle sottocategorie delle proprietà comuni è selezionata, le opzioni di configurazione, e di piattaforma di Configuration Manager alla parte superiore della finestra di dialogo non sono disponibili.  
  
-   Proprietà di configurazione, contenente le informazioni di distribuzione per quanto riguarda debug, ottimizzazione e i parametri di compilazione della soluzione o il progetto.  
  
 Non è possibile creare alcune categorie di primo livello aggiuntive, ma è possibile scegliere di non visualizzare una o l'altra implementazione di `IVsPropertyPage`.  Se, ad esempio, non si dispone di alcune proprietà dell'configurazione\-indipendente da visualizzare per un oggetto, è possibile scegliere di non visualizzare la categoria proprietà comuni.  Visualizzare le proprietà comuni se `ISpecifyPropertyPages` viene implementato dall'oggetto di esplorazione dell'elemento e le proprietà di configurazione quando si distribuisce `ISpecifyPropertyPages` nell'oggetto di configurazione \(l'oggetto che implementa `IVsCfg`, `IVsProjectCfg`e le interfacce correlate\).  
  
 Ogni categoria sotto una categoria di primo livello rappresenta una pagina delle proprietà separata.  Le voci di sottocategorie e delle categorie disponibili nella finestra di dialogo sono determinate dall'implementazione di `ISpecifyPropertyPages` e di `IVsPropertyPage`.  
  
 `IDispatch` oggetti per gli elementi nel contenitore di selezione che dispongono di proprietà da visualizzare nel centro `ISpecifyPropertyPages` pagine delle proprietà per enumerare un elenco di ID classe.  La classe ID viene passata come variabili a `ISpecifyPropertyPages` viene utilizzata per creare istanze delle pagine delle proprietà.  L'elenco di classe ID viene passato a `IVsPropertyPage` per creare la struttura ad albero a sinistra della finestra di dialogo.  Le pagine delle proprietà viene quindi passa le informazioni dell'oggetto di `IDispatch` che implementa `ISpecifyPropertyPages` e inserisce le informazioni per ogni pagina.  
  
 Le proprietà dell'oggetto di esplorazione vengono recuperate utilizzando `IDispatch` per ogni oggetto nella casella di selezione.  
  
 Implementare `Help::DisplayTopicFromF1Keyword` nel package VS fornisce la funzionalità per il pulsante?.  
  
 per ulteriori informazioni, vedere `IDispatch` e `ISpecifyPropertyPages`in MSDN library.  
  
 Il secondo tipo di pagine delle proprietà visualizzate negli esempi ospita un form della griglia delle proprietà, come illustrato nel seguente schermata.  
  
 ![Pagina delle proprietà di VC](../../extensibility/internals/media/vsvcproppages.png "vsVCPropPages")  
Finestra di dialogo pagine delle proprietà con la griglia delle proprietà  
  
 Le interfacce `IVSMDPropertyBrowser` e `IVSMDPropertyGrid` \(dichiarati in vsmanaged.h\) vengono utilizzate per creare e popolare la griglia delle proprietà di una finestra di dialogo o di una finestra.  
  
 L'architettura dei progetti è stata notevolmente dalle versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  In particolare, la nozione di cui progetti è attivo è cambiato.  In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], non esiste alcun concetto di un progetto.  Negli ambienti di sviluppo precedenti, il progetto è il progetto che compila e i comandi di distribuzione impostano il valore predefinito indipendentemente dal contesto.  Ora, la soluzione controlla ed arbitra compilati e i comandi di distribuzione si applicano ai progetti.  
  
 Qual è stato precedentemente un progetto viene acquisito in tre modi diversi:  
  
-   Il progetto di avvio  
  
     È possibile specificare un progetto o i progetti dalla pagina delle proprietà della soluzione che verrà inclusa in movimento quando l'utente preme F5 oppure selezionare l'esecuzione dal menu di compilazione.  Questo funziona in modo simile al progetto precedente nel senso che il nome viene visualizzato in Esplora soluzioni con il grassetto.  
  
     È possibile recuperare il progetto di avvio come proprietà nel modello di automazione chiamando `DTE.Solution.SolutionBuild.StartupProjects`.  In a VSPackage, you call the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> or the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> methods.  `IVsSolutionBuildManager` è disponibile come servizio da `QueryService` su SID\_SVsSolutionBuildManager.  Per ulteriori informazioni, vedere [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md) e [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md).  
  
-   Configurazione della build della soluzione attiva  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dispone di una configurazione di soluzione attiva, disponibile nel modello di automazione di distribuzione `DTE.Solution.SolutionBuild.ActiveConfiguration`.  Una configurazione di soluzione è una raccolta che contiene una configurazione di progetto per ogni progetto nella soluzione \(ciascun progetto può disporre di più configurazioni, su più piattaforme, con i nomi inoltre\).  Per ulteriori informazioni relativi alle pagine delle proprietà della soluzione, vedere [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md).  
  
-   progetto attualmente selezionato  
  
     Implementare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> per recuperare la gerarchia del progetto e l'elemento di progetto o gli elementi selezionati.  Dall'oggetto DTE, utilizzare i metodi di `SelectedItems.SelectedItem.ProjectItem` e di `SelectedItems.SelectedItem.Project` .  È presente codice di esempio nelle intestazioni nei documenti principali di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md)