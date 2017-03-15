---
title: "Procedura: implementare progetti annidati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti annidati, implementazione"
  - "nidificazione di progetti [Visual Studio SDK]"
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura: implementare progetti annidati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si crea un tipo di progetto annidato esistono numerosi passaggi aggiuntivi che devono essere implementati.  Un progetto padre assume le stesse responsabilità che la soluzione è per i progetti \(figlio\) annidati.  Il progetto padre è un contenitore dei progetti simili a una soluzione.  In particolare, esistono numerosi eventi che devono essere generati dalla soluzione e i progetti padre compilare la gerarchia dei progetti annidati.  Questi eventi sono descritti nel seguente processo di creazione dei progetti annidati.  
  
### Per creare progetti annidati  
  
1.  L'ambiente di sviluppo \(IDE\) integrato \(IDE\) carica le informazioni del file di progetto e di avvio del progetto padre chiamando l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> .  Il progetto padre viene creato e aggiunto alla soluzione.  
  
    > [!NOTE]
    >  In questa fase, è troppo presto nel processo per il progetto padre creare il progetto annidato perché il progetto padre deve essere creato prima che i progetti figlio possono essere creati.  Attenendosi a questa sequenza, il progetto padre possibile applicare le impostazioni ai progetti figlio e i progetti figlio possono acquisire le informazioni dei progetti padre se necessari.  Questa sequenza viene se è necessaria sui client come controllo del codice sorgente \(SCC\) e Esplora soluzioni.  
  
     Il progetto padre deve attendere il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> da chiamare dall'IDE prima di poter creare il proprio progetto o progetti annidati \(figlio\).  
  
2.  L'ide chiama `QueryInterface` nel progetto padre per <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>.  Se la chiamata ha esito positivo, l'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> padre per aprire tutti progetti annidati per il progetto padre.  
  
3.  Il progetto padre chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> per aggiornare i listener che i progetti annidati stanno per essere creati.  Lo SCC, ad esempio, ascoltano tali eventi per sapere se i passaggi della soluzione e nel processo di creazione di un progetto si verificano nell'ordine.  Se i passaggi seguenti si verificano verificato un errore, la soluzione potrebbe non essere registrata con controllo del codice sorgente correttamente.  
  
4.  Il progetto padre chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> o il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> su ciascuno dei relativi progetti figlio.  
  
     Passare <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> al metodo di `AddVirtualProject` per indicare che il progetto \(annidato\) virtuale deve essere aggiunto nella finestra di progetto, escluso dalla compilazione, aggiunto al controllo del codice sorgente, e così via.  `VSADDVPFLAGS` consente di controllare la visibilità del progetto annidato e indicare che la funzionalità è associata.  
  
     Se si ricarica un progetto figlio in precedenza esistente con un GUID del progetto memorizzato nel file del progetto padre, il progetto padre chiama `AddVirtualProjectEx`.  The only difference between `AddVirtualProject` and `AddVirtualProjectEX` is that `AddVirtualProjectEX` has a parameter to enable the parent project to specify a per instance `guidProjectID` for the child project to enable <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> and <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> to function correctly.  
  
     Se non c " è GUID disponibile, ad esempio quando si aggiunge un nuovo progetto annidato, la soluzione viene creato uno per il progetto quando viene aggiunto al padre.  È responsabilità del progetto padre mantenere il GUID del progetto nel file di progetto.  Se si elimina un progetto annidato, il GUID per tale progetto può anche essere eliminati.  
  
5.  L'ide chiama il metodo di `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` in ogni progetto figlio del progetto padre.  
  
     Il progetto padre deve implementare `IVsParentProject` se si desidera annidare i progetti.  Tuttavia il progetto padre non chiama mai `QueryInterface` per `IVsParentProject` anche se include progetti padre.  La soluzione gestisce la chiamata a `IVsParentProject` e, se viene distribuita, chiama `OpenChildren` per creare progetti annidati.  `AddVirtualProjectEX` viene sempre chiamato da `OpenChildren`.  Non deve essere mai chiamato dal progetto padre mantenere gli eventi di creazione della gerarchia in ordine.  
  
6.  L'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> nel progetto figlio.  
  
7.  Il progetto padre chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> per aggiornare i listener che i progetti figlio per l'elemento padre sono stati creati.  
  
8.  L'ide chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> nel progetto padre dopo tutti i progetti figlio sono stati aperti.  
  
     Se non ne esiste già, il progetto padre crea un GUID per ogni progetto annidato chiamando `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid` è un'api COM chiamato quando un GUID deve essere creato.  Per ulteriori informazioni, vedere `CoCreateGuid` e i GUID in MSDN Library.  
  
     Il progetto padre archivia il GUID nel file di progetto da recuperare la prossima volta che viene aperto nell'IDE di.  Vedere il passaggio 4 per ulteriori informazioni sulla chiamata di `AddVirtualProjectEX` per recuperare `guidProjectID` per il progetto figlio.  
  
9. Il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> viene quindi chiamato per il ID voce padre che per convenzione delegate nel progetto annidato.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera le proprietà del nodo a annidare un progetto in cui si desidera delegare quando viene chiamato il metodo sul padre.  
  
     Poiché i progetti padre e figlio viene creata un'istanza a livello di codice, è possibile impostare le proprietà per i progetti annidati in questa fase.  
  
    > [!NOTE]
    >  Non solo si ricevono le informazioni sul contesto dal progetto annidato, ma è anche possibile chiedere se il progetto padre dispone di una qualsiasi contesto per tale elemento di <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  In tal modo, è possibile aggiungere attributi aggiuntivi e le opzioni di menu della Guida dinamica specifici dei progetti annidati utente.  
  
10. La gerarchia è compilata per la visualizzazione in Esplora soluzioni con una chiamata al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> .  
  
     Passare la gerarchia all'ambiente con `GetNestedHierarchy` per compilare la gerarchia per la visualizzazione in Esplora soluzioni.  In questo modo, la soluzione corrente che il progetto esiste e può essere gestito per compilare dal gestore di compilazione, oppure può consentire i file nel progetto sia inserito nel controllo del codice sorgente.  
  
11. Quando tutti i progetti annidati per Project1 vengono creati, il controllo viene passato alla soluzione e il processo viene ripetuto per Project2.  
  
     Questo stesso processo per creare progetti annidati si verifica per un progetto figlio con un figlio.  In questo caso, se BuildProject1, che è un elemento figlio di Project1, era progetti figlio, verranno create dopo BuildProject1 e prima di Project2.  Il processo sono ricorsivi e la gerarchia viene compilata dall'alto verso il basso.  
  
     Quando un progetto annidato viene chiuso perché l'utente ha chiuso la soluzione o il progetto specifico stessa, l'altro metodo su `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, viene chiamato.  The parent project wraps calls to the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> method with the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> and the <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> methods to notify listeners to solution events that the nested projects are being closed.  
  
 I seguenti argomenti riguardano di diversi altri concetti da considerare quando si distribuiscono progetti annidati:  
  
 [Considerazioni per scaricare e ricaricare progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Supporto per progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementazione di gestione dei comandi per progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Il filtro nella finestra di dialogo AddItem per progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## Vedere anche  
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Procedura guidata \(. File vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)