---
title: "IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs"
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
  - "IDebugExpressionEvaluationCompleteEvent2"
helpviewer_keywords: 
  - "IDebugExpressionEvaluationCompleteEvent2"
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene inviata dal motore \(DE\) di debug gestione \(SDM\) di debug della sessione quando la valutazione asincrona di espressione è completa.  
  
## Sintassi  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia per indicare il completamento di una valutazione di espressioni avviata da una chiamata a [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto dell'interfaccia.  Gli utilizzi di SDM [QueryInterface](/visual-cpp/atl/queryinterface) accedere all'interfaccia di `IDebugEvent2` .  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento per indicare il completamento di una valutazione di espressioni.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback che viene fornita da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|ottiene l'espressione originale.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Ottiene il risultato della valutazione di un'espressione.|  
  
## Note  
 Il DE necessario inviare questo evento, se la valutazione è stata completata o meno.  
  
 Se la valutazione non viene completata, i flag di `DEBUG_PROPINFO_ATTRIB` e di `DEBUG_PROPINFO_VALUE` non verranno [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) impostate nella struttura restituita da [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) \( [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) l'oggetto viene creato da DE e viene restituito nell'evento di `IDebugExpressionEvaluationCompleteEvent2` se la valutazione ha esito negativo\).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)