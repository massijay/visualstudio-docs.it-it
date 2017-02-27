---
title: "Valutazione dell&#39;espressione in modalit&#224; di interruzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modalità di interruzione, la valutazione di espressioni"
  - "debug [debug SDK], la valutazione di espressioni"
  - "valutazione dell'espressione, la modalità di interruzione"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Valutazione dell&#39;espressione in modalit&#224; di interruzione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'esempio seguente viene descritto il processo che si verifica quando il debugger è in modalità di interruzione e deve effettuare la valutazione di espressioni.  
  
## Processo di valutazione di espressioni  
 Questi sono i passaggi fondamentali relativi alla valutazione di un'espressione:  
  
1.  L'amministratore \(SDM\) di debug della sessione chiama [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per ottenere un'interfaccia di contesto dell'espressione [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Lo SDM chiama quindi [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) con la stringa da analizzare.  
  
3.  Se ParseText non restituisce S\_OK, il motivo per cui l'errore viene restituito.  
  
     \- in caso contrario  
  
     Se ParseText restituisce S\_OK, lo SDM quindi possibile chiamare [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) per ottenere un valore finale dall'espressione analizzata.  
  
    -   Nel caso di utilizzo di `IDebugExpression2::EvaluateSync`, l'interfaccia di callback specificato viene utilizzata per comunicare il processo corrente di valutazione.  Il valore finale viene restituito in un'interfaccia di [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    -   Nel caso di utilizzo di `IDebugExpression2::EvaluateAsync`, l'interfaccia di callback specificato viene utilizzata per comunicare il processo corrente di valutazione.  una volta che la valutazione è completa, EvaluateAsync invia un'interfaccia di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) con il callback.  Con questa interfaccia eventi, il valore finale può essere ottenuto tramite [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)