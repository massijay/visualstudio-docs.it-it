---
title: "Quando un punto di interruzione consente di associare o diventa non associato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "debug [Debugging SDK], punto di interruzione associati a eventi"
  - "punto di interruzione associato a eventi"
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Quando un punto di interruzione consente di associare o diventa non associato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando un punto di interruzione non può essere associato a viene effettuata una chiamata al metodo di [IDebugPendingBreakpoint2:: CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , il tempo di associazione e creare il periodo del punto di interruzione essere diverso.  
  
## metodi chiamati  
 L'amministratore \(SDM\) di debug della sessione vengono chiamati i metodi seguenti:  
  
1.  [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  Il DE restituisce [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).  
  
2.  [IDebugPendingBreakpoint2:: Attivare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3.  [IDebugPendingBreakpoint2:: virtualizzare](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4.  Il metodo di [IDebugPendingBreakpoint2:: associazione](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) e restituisce S\_OK.  Il DE invia [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) o [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5.  Metodi di [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) e di[IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) per testare e ottenere i punti di interruzione associati.  
  
## Vedere anche  
 [Eventi di chiamata del Debugger](../../extensibility/debugger/calling-debugger-events.md)