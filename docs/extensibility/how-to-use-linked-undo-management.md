---
title: "Procedura: utilizzare la gestione di annullamento collegato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - gestione fase di rollback collegata"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: utilizzare la gestione di annullamento collegato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La di annullamento collegata consente all'utente di annullare contemporaneamente le stesse modifiche in più file.  Ad esempio, le modifiche simultanee di testo tramite i file di programma più, ad esempio un file di intestazione e un file di Visual C\+\+, è una transazione di annullamento collegata.  La funzionalità di annullamento collegata viene compilata nell'implementazione dell'ambiente di gestione di annullamento e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> consente di modificare questa funzionalità.  La di annullamento collegata viene implementata da un'unità di annullamento padre che può collegare gli stack di annullamento separati da considerare come una singola unità di annullamento.  La procedura per l'utilizzo della fase di annullamento collegata è dettagliata nella sezione seguente.  
  
### Per utilizzare un'operazione di annullamento collegata  
  
1.  Chiamare `QueryService` su `SVsLinkedUndoManager` per ottenere un puntatore a `IVsLinkedUndoTransactionManager`.  
  
2.  Create the initial parent linked undo unit by calling <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>.  Ciò consente di impostare il punto di partenza per un set di stack di annullamento da raggruppare gli stack di annullamento collegati.  Nel metodo di `OpenLinkedUndo` sarà inoltre necessario specificare se si desidera che undo collegata per essere rigido o non rigido.  il comportamento di annullamento collegato Non rigido significa che alcuni dei documenti con gli elementi di pari livello di annullamento collegati possono chiudere e successivamente consentire agli altri elementi di pari livello di annullamento collegati nei relativi stack.  Il comportamento di annullamento collegato rigido specifica che tutti gli stack dell'elemento di pari livello di annullamento collegati devono essere annullati insieme o non annullati affatto.  aggiungere gli stack di annullamento collegati successivi chiamando il metodo di [IOleUndoManager:: aggiungere](http://msdn.microsoft.com/library/windows/desktop/ms680135) .  
  
3.  La chiamata <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> viene eseguito il rollback di tutte unità di annullamento collegato come una.  
  
    > [!NOTE]
    >  Per implementare la gestione di annullamento collegata in un editor, aggiungere la gestione di annullamento.  Per ulteriori informazioni sull'implementazione della gestione di annullamento collegata, vedere [Procedura: Implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md).  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Procedura: implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md)