---
title: "IDebugPendingBreakpoint2::Bind | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::Bind"
helpviewer_keywords: 
  - "Bind (metodo)"
  - "Metodo IDebugPendingBreakpoint2::Bind"
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Associa questo punto di interruzione corrente a uno o più percorsi di codice.  
  
## Sintassi  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```c#  
int Bind();  
```  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_BP_DELETED` se il punto di interruzione è stato eliminato.  
  
## Note  
 Quando questo metodo viene chiamato, un motore di \(DE\) debug deve tentare di associare questo punto di interruzione corrente a tutti i percorsi di codice che corrispondono.  
  
 Dopo il completamento del metodo, il chiamante deve attendere che indica di eventi che il punto di interruzione in attesa è associato o è per errore prima di presupporre che chiama a [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) o [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md).methods enumererà tutti i punti di interruzione di errori o limite, rispettivamente.  
  
## Vedere anche  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)