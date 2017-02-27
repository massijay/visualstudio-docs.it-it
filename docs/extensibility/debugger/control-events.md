---
title: "Eventi di controllo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [debug SDK], eventi"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Eventi di controllo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È necessario inviare gli eventi durante l'esecuzione controllata del programma.  Tutti gli eventi vengono inviati tramite l'interfaccia di [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) e con attributi che è necessario implementare il metodo di [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .  
  
## metodi aggiuntivi  
 Alcuni eventi richiedono l'implementazione di metodi aggiuntivi, come segue:  
  
-   Inviare l'interfaccia di [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) quando il motore di debug \(DE\) viene inizializzato è necessario implementare il metodo di [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .  
  
-   Il controllo di esecuzione è richiesta l'implementazione di tali eventi del controllo come le interfacce di[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e di [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) .  **IDebugBreakEvent2** è obbligatorio solo per le interruzioni asincrone.  
  
-   Entrare nelle funzioni richiede l'implementazione dell'interfaccia di [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e dei relativi metodi.  
  
 Gli eventi che derivano dai punti di interruzione richiedono l'implementazione delle interfacce di [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), di [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e di [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) nonché i metodi di [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) e di [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) .  
  
 La valutazione asincrona di espressione è necessario implementare l'interfaccia di [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) e i metodi di [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[e GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .  
  
 gli eventi sincroni richiedono implementare il metodo di [IDebugEngine2:: ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) .  
  
 Affinché il motore scrivere l'output di tipo stringa, è necessario implementare il metodo di [IDebugOutputStringEvent2:: GetString](../Topic/IDebugOutputStringEvent2::GetString.md) .  
  
## Vedere anche  
 [Controllo dell'esecuzione e la valutazione dello stato](../../extensibility/debugger/execution-control-and-state-evaluation.md)