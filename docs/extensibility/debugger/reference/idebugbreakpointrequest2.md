---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
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
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "Interfaccia IDebugBreakpointRequest2"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta le informazioni necessarie per creare e associare qualsiasi tipo di punto di interruzione.  
  
## Sintassi  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## Note per gli implementatori  
 L'amministratore \(SDM\) di debug della sessione in genere implementa.  
  
## Note per i chiamanti  
 Il motore \(DE\) di debug riceve questa interfaccia con una chiamata [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) a per creare un punto di interruzione in attesa.  Una chiamata [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) in possono recuperare questa interfaccia da DE.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugBreakpointRequest2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ottiene il tipo di posizione del punto di interruzione della richiesta di un punto di interruzione.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ottiene le informazioni di richiesta del punto di interruzione che descrivono la richiesta di un punto di interruzione.|  
  
## Note  
 Dopo che il programma sottoposto a debug è stato caricato, una chiamata [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) alle associazioni di un punto di interruzione in attesa nella posizione richiesta nel programma.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)