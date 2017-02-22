---
title: "IDebugStackFrame2::GetExpressionContext | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene un contesto di valutazione per la valutazione di espressioni nel contesto corrente di uno stack frame e stack di un thread.  
  
## Sintassi  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```c#  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### Parametri  
 `ppExprCxt`  
 \[out\]  Restituisce [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) un oggetto che rappresenta un contesto per la valutazione di espressioni.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 In genere, un contesto di valutazione di un'espressione può essere considerato come ambito per eseguire la valutazione di espressioni.  Chiamare [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) il metodo per analizzare un'espressione e quindi chiamare il risultato [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) i metodi per valutare l'espressione analizzata.  
  
## Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)