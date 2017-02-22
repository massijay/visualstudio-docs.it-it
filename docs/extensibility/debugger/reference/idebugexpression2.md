---
title: "IDebugExpression2 | Microsoft Docs"
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
  - "IDebugExpression2"
helpviewer_keywords: 
  - "Interfaccia IDebugExpression2"
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpression2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un'espressione analizzata pronta per associare e valutare.  
  
## Sintassi  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per rappresentare un'espressione analizzata pronta per essere valutato.  
  
## Note per i chiamanti  
 Una chiamata [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) a restituisce questa interfaccia.  [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) restituisce [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) l'interfaccia.  Queste interfacce sono accessibili solo quando il programma sottoposto a debug è stato messo in pausa e uno stack frame è disponibile.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugExpression2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Valuta l'espressione in modo asincrono.|  
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|termina la valutazione asincrona di espressione.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Valuta l'espressione in modo sincrono.|  
  
## Note  
 Quando un programma è stato interrotto, l'amministratore \(SDM\) di debug della sessione ottiene uno stack frame da DE con una chiamata a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  Le chiamate di SDM quindi [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) per [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) ottenere l'interfaccia.  Questo è seguito da una chiamata a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) per creare l'interfaccia di `IDebugExpression2` , che rappresenta l'espressione analizzata pronta per essere valutato.  
  
 Lo SDM chiama o [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) effettivamente [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) valutare l'espressione e produrre un valore.  
  
 In un'implementazione di `IDebugExpressionContext2::ParseText`, la funzione di `CoCreateInstance` di utilizza COM di DE per creare un'istanza di un analizzatore di espressioni e per [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) ottenere un'interfaccia \(vedere l'esempio nell'interfaccia di `IDebugExpressionEvaluator` \).  Le chiamate di DE quindi [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) per [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) ottenere un'interfaccia.  Questa interfaccia viene utilizzata nell'implementazione di `IDebugExpression2::EvaluateSync` e di `IDebugExpression2::EvaluateAsync` per eseguire la valutazione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)