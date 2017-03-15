---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce l'espressione in modo asincrono.  
  
## Sintassi  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### Parametri  
 `dwFlags`  
 \[in\]  Una combinazione di flag [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) dall'enumerazione che controllano la valutazione di espressioni.  
  
 `pExprCallback`  
 \[in\]  questo parametro è sempre un valore null.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Un codice di errore tipico è:  
  
|delle modifiche a..."|Descrizione|  
|---------------------------|-----------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Un'altra espressione viene attualmente valutazione e la valutazione simultanea dell'espressione non è supportata.|  
  
## Note  
 Questo metodo deve restituire immediatamente dopo che ha avviato la valutazione di espressioni.  Quando l'espressione correttamente viene valutata, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) deve essere [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) inviato al callback dell'evento come fornito [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) tramite o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## Esempio  
 Nell'esempio seguente viene illustrato come implementare questo metodo per un oggetto semplice di `CExpression` che implementa [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) l'interfaccia.  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## Vedere anche  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)