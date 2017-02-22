---
title: "Procedura dettagliata: Aggiunta di funzionalit&#224; in un Editor personalizzato | Microsoft Docs"
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
  - "editor [Visual Studio SDK], personalizzato - aggiunta di funzionalità"
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 38
caps.handback.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Aggiunta di funzionalit&#224; in un Editor personalizzato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo aver creato un editor personalizzato, è possibile aggiungere più funzionalità.  
  
### Per creare un editor per un VSPackage  
  
1.  Creare un editor personalizzato utilizzando il modello di progetto Package Visual Studio.  
  
     Per altre informazioni, vedere [Procedura dettagliata: Creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decidere se si desidera che l'editor per supportare una singola visualizzazione o più viste.  
  
     Un editor che supporta il **nuova finestra** comando o dispone di visualizzazione form e visualizzazione codice, richiede gli oggetti dati documento separato e oggetti di visualizzazione documento. In un editor che supporta una sola visualizzazione, l'oggetto dati di documento e l'oggetto visualizzazione documento possono essere implementati nello stesso oggetto.  
  
     Per un esempio di più visualizzazioni, vedere [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementare una factory editor mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia.  
  
     Per altre informazioni, vedere [Factory editor](../extensibility/editor-factories.md).  
  
4.  Decidere se si desidera che l'editor di utilizzare l'attivazione sul posto o per gestire la finestra di oggetto visualizzazione documento di incorporamento semplificato.  
  
     Finestra dell'editor di incorporamento semplificato ospita una visualizzazione di documenti standard, mentre una finestra dell'editor di attivazione sul posto ospita un controllo ActiveX o un altro oggetto come relativa visualizzazione documento attivo. Per altre informazioni, vedere [Incorporamento semplificato](../extensibility/simplified-embedding.md) e [Attivazione sul posto](../misc/in-place-activation.md).  
  
5.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per gestire i comandi.  
  
6.  Fornire la persistenza di documento e di risposta alle modifiche di file esterno effettuando le operazioni seguenti:  
  
    1.  Per mantenere il file, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> nell'oggetto dati di documento dell'editor.  
  
    2.  Per rispondere alle modifiche di file esterno, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> nell'oggetto dati di documento dell'editor.  
  
        > [!NOTE]
        >  Chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> per ottenere un puntatore a `IVsFileChangeEx`.  
  
7.  Coordinare gli eventi di modifica di documenti con controllo del codice sorgente. Per eseguire questa operazione:  
  
    1.  Ottenere un puntatore a `IVsQueryEditQuerySave2` chiamando `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Quando si verifica il primo evento di modifica, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo.  
  
         Chiede all'utente di estrarre il file se non si è già estratto. Assicurarsi di gestire una condizione di "file non estratti" per evitare errori  
  
    3.  Analogamente, prima di salvare il file, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metodo.  
  
         Questo metodo richiede all'utente di salvare il file se non è stata salvata o se è stata modificata dall'ultimo salvataggio.  
  
8.  Abilitare il **proprietà** finestra per visualizzare le proprietà per il testo selezionato nell'editor. Per eseguire questa operazione:  
  
    1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ogni selezione di testo ora viene modificato, passando nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servizio per ottenere un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Consentire agli utenti di trascinare gli elementi tra l'editor e **della casella degli strumenti**, o tra gli editor esterni \(ad esempio Microsoft Word\) e **della casella degli strumenti**. Per eseguire questa operazione:  
  
    1.  Implementare `IDropTarget` in un editor di avvisare l'IDE che l'editor è una destinazione di rilascio.  
  
    2.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaccia per la vista in modo l'editor è possibile abilitare e disabilitare gli elementi di **della casella degli strumenti**.  
  
    3.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> e chiamare `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> servizio per ottenere un puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfacce.  
  
         In questo modo, il pacchetto Visual Studio aggiungere nuovi elementi per il **della casella degli strumenti**.  
  
10. Decidere se si desidera che tutte le altre caratteristiche facoltative per l'editor.  
  
    -   Se si desidera che l'editor per supportare ricerca e sostituzione dei comandi, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Se si desidera utilizzare una finestra degli strumenti Struttura documento nell'editor, implementare `IVsDocOutlineProvider`.  
  
    -   Se si desidera utilizzare una barra di stato nell'editor, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> e chiamare `QueryService` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> per ottenere un puntatore a `IVsStatusBar`.  
  
         Ad esempio, un editor può visualizzare riga o informazioni di colonna, la modalità di selezione \(stream \/ casella\) e modalità di inserimento \(insert \/ overstrike\).  
  
    -   Se si desidera che l'editor per supportare il `Undo` comando, il metodo consigliato consiste nell'utilizzare il modello di gestione di annullamento OLE. In alternativa, è possibile configurare l'handle di editor di `Undo` comando direttamente.  
  
11. Creare informazioni, inclusi i GUID per il package VS, i menu, l'editor e altre funzioni del Registro di sistema.  
  
     Di seguito è un esempio di codice che si dovrà inserire nello script di file con estensione RGS per illustrare come registrare correttamente un editor generico.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. Implementare il supporto della Guida sensibile al contesto.  
  
     In questo modo è possibile fornire supporto F1 Guida in linea e la finestra Guida dinamica per gli elementi nell'editor. Per altre informazioni in merito, vedere [Procedura: fornire il contesto per gli editor](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md).  
  
13. Esporre un modello di oggetti di automazione da editor mediante l'implementazione di `IDispatch` interfaccia.  
  
     Per altre informazioni, vedere [Che contribuiscono al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## Programmazione efficiente  
  
-   L'istanza dell'editor viene creato quando si chiama l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo. Se l'editor supporta più viste, `CreateEditorInstance` vengono creati i dati del documento e gli oggetti di visualizzazione documento. Se l'oggetto dati di documento è già aperto, un valore non null `punkDocDataExisting` valore viene passato a `IVsEditorFactory::CreateEditorInstance`. L'implementazione di factory dell'editor deve determinare se un oggetto dati documento esistente è compatibile eseguendo una query per le interfacce appropriate su di esso. Per altre informazioni, vedere [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md).  
  
-   Se si utilizza l'approccio di incorporamento semplificato, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia.  
  
-   Se si decide di utilizzare l'attivazione sul posto, implementare le interfacce seguenti:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Il `IOleInPlaceComponent` interfaccia viene utilizzata per evitare l'unione di menu OLE 2.  
  
     Il `IOleCommandTarget` implementazione gestisce i comandi, ad esempio **Taglia**, **Copia**, e **Incolla**. Quando si implementa `IOleCommandTarget`, decidere se l'editor richiede un proprio file vsct per definire la propria struttura di menu comando o se è possibile implementare i comandi standard definiti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. In genere, gli editor di utilizzano ed estendono i menu dell'IDE e definiscono le proprie barre degli strumenti. Tuttavia, spesso è necessario per un editor definire un proprio comandi specifici oltre a utilizzare il set di comandi standard dell'IDE. A tale scopo, l'editor deve dichiarare i comandi standard utilizza e quindi definire qualsiasi nuovi comandi, menu di scelta rapida, menu di primo livello e le barre degli strumenti in un file vsct. Se si crea un'attivazione sul posto dell'editor, quindi implementare <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e definire i menu e barre degli strumenti dell'editor in un file vsct anziché utilizzare l'unione di menu OLE 2.  
  
-   Per evitare di affollare nell'interfaccia utente di comando di menu, utilizzare i comandi esistenti nell'IDE prima di inventare nuovi comandi. Comandi condivisi vengono definiti in SharedCmdDef.vsct e ShellCmdDef.vsct. Questi file vengono installati per impostazione predefinita nella sottodirectory VisualStudioIntegration\\Common\\Inc del [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installazione.  
  
-   `ISelectionContainer` possibile esprimere una o più selezioni. Ogni oggetto selezionato viene implementato come un `IDispatch` oggetto.  
  
-   L'IDE implementa `IOleUndoManager` come servizio accessibile da un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o come un oggetto che può essere creata un'istanza tramite <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. Implementa l'editor di `IOleUndoUnit` per ogni interfaccia `Undo` azione.  
  
-   Esistono due posizioni un editor personalizzato è possibile esporre gli oggetti di automazione:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## Vedere anche  
 [Che contribuiscono al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Procedura: fornire il contesto per gli editor](../Topic/How%20to:%20Provide%20Context%20for%20Editors.md)