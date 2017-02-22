---
title: "Procedura: cancellare lo Stack di annullamento | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - deselezionare stack di annullamento"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: cancellare lo Stack di annullamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La procedura riportata di seguito seguito viene illustrato come rimuovere lo stack di annullamento.  
  
### Per rimuovere lo stack di annullamento  
  
1.  Per cancellare l'utilizzo di annullamento dello stack il metodo di [IOleUndoManager:: DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) .  Di seguito viene riportato un esempio di codice riportato di seguito:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## Vedere anche  
 [Procedura: implementare la gestione di annullamento](../extensibility/how-to-implement-undo-management.md)