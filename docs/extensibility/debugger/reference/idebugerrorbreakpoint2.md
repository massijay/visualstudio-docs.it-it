---
title: "IDebugErrorBreakpoint2 | Microsoft Docs"
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
  - "IDebugErrorBreakpoint2"
helpviewer_keywords: 
  - "Interfaccia IDebugErrorBreakpoint2"
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugErrorBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un errore o un punto di interruzione di avviso, ad esempio una posizione non valida, un'espressione non valida, o i motivi per cui del punto di interruzione in attesa non è associato \(codice°non nuovamente caricato, e così via\).  
  
## Sintassi  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il modulo di debug implementa questa interfaccia come parte del supporto per i punti di interruzione.  Questa interfaccia viene utilizzata per segnalare problemi con associare un punto di interruzione.  
  
## Note per i chiamanti  
 Una chiamata [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) ottiene l'interfaccia.  Tale interfaccia può essere restituita \(come parte di un elenco rappresentato [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) da un'interfaccia\) da una chiamata a [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) o [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md).  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugErrorBreakpoint2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ottiene il punto di interruzione in attesa che ha provocato l'errore.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ottiene la risoluzione degli errori del punto di interruzione che descrive l'errore.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [Successivo](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)