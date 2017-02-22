---
title: "IEnumDebugBoundBreakpoints2 | Microsoft Docs"
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
  - "IEnumDebugBoundBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2"
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia enumera i punti di interruzione associati associati a di un punto di interruzione in attesa o un evento associato il punto di interruzione.  
  
## Sintassi  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore di \(DE\) debug implementa questa interfaccia come parte del supporto per i punti di interruzione.  Questa interfaccia deve essere implementato se i punti di interruzione sono supportati.  
  
## Note per i chiamanti  
 chiamate di Visual Studio:  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione che sono stati attivati.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione che sono stati associati.  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i punti di interruzione associato a quel punto di interruzione corrente.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugBoundBreakpoints2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Recupera un numero specificato dei punti di interruzione associati in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Ignora un numero specificato dei punti di interruzione associati in una sequenza di enumerazione.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Ottiene il numero di punti di interruzione associati in un enumeratore.|  
  
## Note  
 Visual Studio utilizza i punti di interruzione associati rappresentati da questa interfaccia per aggiornare la visualizzazione dei punti di interruzione nell'IDE.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)