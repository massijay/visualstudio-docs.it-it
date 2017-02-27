---
title: "Rendere disponibili i comandi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menu [Visual Studio SDK], comandi"
  - "procedure consigliate, i comandi di menu e barra degli strumenti"
  - "barre degli strumenti [Visual Studio], procedure consigliate"
  - "comandi di menu, le procedure consigliate"
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 35
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 35
---
# Rendere disponibili i comandi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando più VSPackage vengono aggiunti a Visual Studio, l'interfaccia utente \(UI\) può diventare saturi con i comandi. È possibile programmare il pacchetto per ridurre questo problema, come indicato di seguito:  
  
-   Il pacchetto di programma in modo che venga caricato solo quando un utente richiede.  
  
-   Il pacchetto di programma in modo che i comandi vengono visualizzati solo quando potrebbero essere necessari nel contesto dello stato corrente dell'ambiente di sviluppo integrato \(IDE\).  
  
## Caricamento ritardato  
 Il metodo tipico per abilitare il caricamento ritardato è progettare VSPackage in modo che i comandi vengono visualizzati nell'interfaccia utente, ma non è possibile caricare il pacchetto stesso finché un utente fa clic su uno dei comandi. A tale scopo, nel file vsct, creare i comandi che non dispongono di alcun flag di comando.  
  
 Nell'esempio seguente viene illustrata la definizione di un comando di menu da un file vsct. Questo è il comando che viene generato per il modello di pacchetto Visual Studio quando il **comando di Menu** selezionata nel modello.  
  
 [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
 Nell'esempio, se il gruppo padre, `MyMenuGroup`, è un figlio di un menu di primo livello, ad esempio il **strumenti** il comando sarà visibile nel menu, menu, ma il pacchetto che esegue il comando non verrà caricato finché non si seleziona il comando da un utente. Tuttavia, se il comando per l'implementazione di programmazione il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, è possibile abilitare il pacchetto da caricare quando viene espanso il menu che contiene il comando.  
  
 Si noti che il caricamento ritardato può anche migliorare le prestazioni di avvio.  
  
## Contesto corrente e la visibilità dei comandi  
 È possibile eseguire comandi VSPackage per essere visibile o nascosto, a seconda dello stato corrente dei dati VSPackage o le azioni che sono attualmente rilevanti. È possibile abilitare il package VS impostare lo stato dei comandi, in genere tramite un'implementazione di <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodo il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia, ma è necessario il VSPackage da caricare prima di poter eseguire il codice. È invece consigliabile abilitare l'IDE gestire la visibilità dei comandi senza caricamento del pacchetto. A tale scopo, nel file vsct, associare i comandi di uno o più contesti dell'interfaccia utente speciale. Questi contesti dell'interfaccia utente sono identificati da un GUID noto come un *contesto del comando GUID*.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Controlla le modifiche risultanti da azioni dell'utente, ad esempio il caricamento di un progetto o dalla modifica di compilazione. Quando si verificano modifiche, viene automaticamente modificato l'aspetto dell'IDE. La tabella seguente illustra quattro principali contesti dell'IDE di modifica che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Monitor.  
  
|Tipo di contesto|Descrizione|  
|----------------------|-----------------|  
|Tipo di progetto attivo|Per la maggior parte dei tipi di progetto, questo `GUID` valore corrisponde al GUID del package VS che implementa il progetto. Tuttavia, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti utilizzano il tipo di progetto `GUID` come valore.|  
|Finestra attiva|In genere, questo è l'ultima finestra di documento attivo che definisce il contesto dell'interfaccia utente corrente di tasti di scelta rapida. Tuttavia, è possibile inoltre una finestra degli strumenti con una tabella di tasti che è simile al browser interno. Per finestre di documento più schede, ad esempio l'editor HTML, ogni scheda ha un contesto diverso comando `GUID`.|  
|Servizio di linguaggio Active|Il servizio di linguaggio che è associato il file è attualmente visualizzato in un editor di testo.|  
|Finestra degli strumenti attiva|Una finestra degli strumenti è aperto e ha lo stato attivo.|  
  
 Un'area principale contesto quinta è lo stato dell'interfaccia utente dell'IDE. Contesti dell'interfaccia utente sono identificati dal contesto del comando attivo `GUID`s, come indicato di seguito:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionBuilding>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Debugging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_Dragging>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_FullScreenMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_DesignMode>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_NoSolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_CodeWindow>  
  
 Questi GUID sono contrassegnati come attivo o inattivo, a seconda dello stato corrente dell'IDE. Più contesti dell'interfaccia utente possono essere attivi nello stesso momento.  
  
### Nascondere e visualizzare i comandi in base al contesto  
 È possibile visualizzare o nascondere un comando pacchetto nell'IDE senza caricare il pacchetto stesso. A tale scopo, definire il comando nel file vsct del pacchetto tramite il `DefaultDisabled`, `DefaultInvisible`, e `DynamicVisibility` comando flags e aggiungere uno o più [VisibilityItem](../../extensibility/visibilityitem-element.md) elementi per il [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione. Quando un comando specificato del contesto `GUID` diventa attivo, il comando viene visualizzato senza caricamento del pacchetto.  
  
### GUID di contesto personalizzato  
 Se un contesto di comando appropriato che GUID non è già stato definito, è possibile definire uno nel pacchetto Visual Studio e quindi programmare in modo che sia attivo o inattivo in base alle esigenze per controllare la visibilità dei comandi della. Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> su:  
  
-   Registrare i GUID di contesto \(chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> \(metodo\)\).  
  
-   Ottenere lo stato di un contesto `GUID` \(chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> \(metodo\)\).  
  
-   Contesto di attivazione `GUID`s e disattivare \(chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> \(metodo\)\).  
  
    > [!CAUTION]
    >  Assicurarsi che il pacchetto Visual Studio non influiscono sullo stato di qualsiasi contesto esistente GUID perché altri package VS potrebbe dipendere da essi.  
  
## Esempio  
 L'esempio seguente di un comando VSPackage illustra la visibilità di un comando che è gestito da contesti di comando senza caricare il package VS dinamica.  
  
 Il comando è impostato per essere abilitato e visualizzata ogni volta che esiste una soluzione. vale a dire, ogni volta che uno del contesto del comando seguente GUID è attivo:  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>  
  
-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>  
  
 Nell'esempio, si noti che ogni flag di comando è un oggetto separato [comando Flag](../../extensibility/command-flag-element.md) elemento.  
  
 [!CODE [DynamicVisibility#01](DynamicVisibility#01)]  
  
 Notare anche che ogni contesto dell'interfaccia utente deve essere specificato in un oggetto separato `VisibilityItem` elemento, come indicato di seguito.  
  
 [!CODE [DynamicVisibility#02](DynamicVisibility#02)]  
  
## Vedere anche  
 [Confronto tra oggetti MenuCommand e OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi in VS](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Aggiunta dinamica di voci di Menu](../../extensibility/dynamically-adding-menu-items.md)