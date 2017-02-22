---
title: "IDebugExpression2::Abort | Microsoft Docs"
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
  - "IDebugExpression2::Abort"
helpviewer_keywords: 
  - "IDebugExpression2::Abort"
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo annulla la valutazione asincrona di espressione come avviato da una chiamata [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) al metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT Abort(  
   void  
);  
```  
  
```c#  
int Abort();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Quando la valutazione asincrona di espressione viene annullata, di non [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) inviato un evento al callback di evento passati [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ai [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metodi.  
  
## Vedere anche  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)