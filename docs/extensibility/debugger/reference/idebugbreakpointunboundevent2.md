---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente all'amministratore di debug della sessione \(SDM\) di un punto di interruzione associato è stato separato da un programma caricato.  
  
## Sintassi  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore di \(DE\) debug implementa questa interfaccia come parte del supporto per i punti di interruzione.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto di questa interfaccia \(utilizzi [QueryInterface](/visual-cpp/atl/queryinterface) di SDM accedere all'interfaccia di `IDebugEvent2` \).  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento quando un punto di interruzione associato è stato separato.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback fornite da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugBreakpointUnboundEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Ottiene il punto di interruzione che è diventata non associato.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|ottiene il motivo che il punto di interruzione è stato separato.|  
  
## Note  
 Quando una DLL o una classe del motore di debug scarica, tutti i punti di interruzione associati al codice in quel modulo devono essere separati dal programma sottoposto a debug.  `IDebugBreakpointUnboundEvent2` viene inviato per ciascun punto di interruzione non associato.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)