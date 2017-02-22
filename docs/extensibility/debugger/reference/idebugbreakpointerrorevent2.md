---
title: "IDebugBreakpointErrorEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointErrorEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointErrorEvent2"
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente all'amministratore di debug della sessione \(SDM\) di un punto di interruzione in attesa non può essere associato a un programma caricato, a causa di un avviso o un errore.  
  
## Sintassi  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il DE implementa questa interfaccia come parte del supporto per i punti di interruzione.  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) L'interfaccia deve essere implementata nello stesso oggetto di questa interfaccia \(utilizzi [QueryInterface](/visual-cpp/atl/queryinterface) di SDM accedere all'interfaccia di `IDebugEvent2` \).  
  
## Note per i chiamanti  
 Il DE crea e invia questo oggetto evento quando di un punto di interruzione in attesa non può essere associato al programma sottoposto a debug.  L'evento viene inviato mediante [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) la funzione di callback fornite da SDM quando è collegato al programma sottoposto a debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugBreakpointErrorEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ottiene [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) l'interfaccia che descrive il problema o l'errore.|  
  
## Note  
 Ogni volta che un punto di interruzione verrà associato, un evento viene inviato a SDM.  Se il punto di interruzione non può essere associato, `IDebugBreakpointErrorEvent2` viene inviato; in caso contrario, [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) viene inviato.  
  
 Ad esempio, quando la condizione associata al punto di interruzione in attesa non si riesce ad analizzare o valutare, un avviso viene inviato dal punto di interruzione in attesa non può essere associato a.  Questa situazione può verificarsi se il codice del punto di interruzione non ha caricato nuovamente.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)