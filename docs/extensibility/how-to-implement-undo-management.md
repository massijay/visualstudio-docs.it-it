---
title: "Procedura: implementare la gestione di annullamento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - annullare gestione"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Procedura: implementare la gestione di annullamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'interfaccia primaria utilizzata per la gestione di annullamento è <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, che viene implementata dall'ambiente.  Per supportare gestione di annullamento, di annullamento separate di utilizzo \(ovvero <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, che possono contenere singoli passaggi più.  
  
 Come implementare la gestione di annullamento varia a seconda che l'editor supporta più visualizzazioni o meno.  Le procedure per ogni implementazione sono dettagliate nelle sezioni seguenti.  
  
## Casi in cui un editor supporta un singolo punto di vista  
 In questo scenario, l'editor non supporta più visualizzazioni.  È presente un editor e un documento e supportano l'annullamento su.  Utilizzare la procedura riportata di seguito per implementare la gestione di annullamento.  
  
#### Per supportare gestione di annullamento per un editor di singolo\-visualizzazione  
  
1.  Chiamata `QueryInterface` sull'interfaccia di `IServiceProvider` sulla struttura della finestra per `IOleUndoManager`, dall'oggetto del documento per accedere a gestione di annullamento \(`IID_IOLEUndoManager`\).  
  
2.  Quando una visualizzazione viene posizionato in una struttura della finestra, ottiene un puntatore di sito, che può utilizzare per chiamare `QueryInterface` per `IServiceProvider`.  
  
## Casi in cui un editor supporta più visualizzazioni  
 Se si dispone di documento e la separazione di visualizzazione, esiste in genere un amministratore di annullamento associato al documento stesso.  Tutte le unità di annullamento vengono inseriti in un amministratore di annullamento associato all'oggetto dati del documento.  
  
 Instead of the view querying for the undo manager, of which there is one for each view, the document data object calls <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> to instantiate the undo manager, specifying a class identifier of CLSID\_OLEUndoManager.  L'identificatore di classe definito nel file di OCUNDOID.h.  
  
 When using <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> to create your own undo manager instance, use the following procedure to hook your undo manager into the environment.  
  
#### Per associare il gestore di annullamento nell'ambiente  
  
1.  Chiamare `QueryInterface` sull'oggetto restituito da <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> per `IID_IOleUndoManager`.  Archiviare il puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  chiamare `QueryInterface` su `IOleUndoManager` per `IID_IOleCommandTarget`.  Archiviare il puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Relay your <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> and <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> calls into the stored `IOleCommandTarget` interface for the following StandardCommandSet97 commands:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  chiamata `QueryInterface` su `IOleUndoManager` per `IID_IVsChangeTrackingUndoManager`.  Archiviare il puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Use the pointer to <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> to call the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>, and the <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> methods.  
  
5.  chiamata `QueryInterface` su `IOleUndoManager` per `IID_IVsLinkCapableUndoManager`.  
  
6.  Chiamare l'entity\_M:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient\(Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient\) al documento, che deve implementare anche l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> .  Quando il documento viene chiuso, chiamare `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Quando il documento viene chiuso, chiamare `QueryInterface` sull'amministratore di annullamento per `IID_IVsLifetimeControlledObject`.  
  
8.  Chiamare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.  
  
9. Quando vengono apportate modifiche al documento, chiamare <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> sull'amministratore a una classe di `OleUndoUnit` .  Il metodo di <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> mantiene un riferimento all'oggetto, pertanto in genere è lo rilascia immediatamente dopo <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 La classe di `OleUndoManager` rappresenta una singola istanza di annullamento dello stack.  Pertanto, è presente un oggetto di annullamento dell'amministratore di entità di dati che viene rilevato per la fase di annullamento o la ripetizione.  
  
> [!NOTE]
>  Mentre l'oggetto di annullamento amministratore viene utilizzato ampiamente dall'editor di testo, è un componente generale che non include il supporto specifico all'editor di testo.  Se si desidera supportare undo a più livelli o la ripetizione, è possibile utilizzare questo oggetto a tale scopo.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Procedura: cancellare lo Stack di annullamento](../extensibility/how-to-clear-the-undo-stack.md)