---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene utilizzata dal motore \(DE\) di debug per l'invio di eventi di debug gestione \(SDM\) di debug della sessione.  
  
## Sintassi  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## Note per gli implementatori  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementa questa interfaccia per ricevere eventi dal modulo di debug.  
  
## Note per i chiamanti  
 Il modulo di debug in genere riceve questa interfaccia quando le chiamate di [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)SDM [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  Il modulo di debug invia gli eventi allo SDM chiamando [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugEventCallback2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Invia una notifica degli eventi di debug a SDM.|  
  
## Note  
 Sebbene [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) specificare che accettano un'interfaccia di `IDebugEventCallback2` , questo non avviene e il puntatore a interfaccia verrà sempre un valore null.  Invece, il motore di debug deve utilizzare l'interfaccia di `IDebugEventCallback2` ricevuta nella chiamata a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), o [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Se i mezzi di un pacchetto [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in codice gestito, si consiglia di <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> viene richiamato sulle diverse interfacce a cui vengono passati [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)