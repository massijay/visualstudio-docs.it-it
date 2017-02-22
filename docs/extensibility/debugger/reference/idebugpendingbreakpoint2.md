---
title: "IDebugPendingBreakpoint2 | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2"
helpviewer_keywords: 
  - "Interfaccia IDebugPendingBreakpoint2"
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un punto di interruzione che è pronto per l'associazione a un percorso di codice.  
  
## Sintassi  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore di \(DE\) debug implementa questa interfaccia come parte del supporto per i punti di interruzione.  
  
## Note per i chiamanti  
 Una chiamata [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) crea un punto di interruzione in [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) attesa in un'interfaccia.  Una chiamata [Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) crea un'interfaccia di `IDebugBreakpoint2` che rappresenta un punto di interruzione associato nel programma.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugPendingBreakpoint2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se questo punto di interruzione corrente può essere associato a un percorso di codice.|  
|[Operazione di binding](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Associa questo punto di interruzione corrente a uno o più percorsi di codice.|  
|[GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)|Ottiene lo stato di questo punto di interruzione corrente.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ottiene la richiesta del punto di interruzione utilizzata per creare questo punto di interruzione corrente.|  
|[Virtualizzare](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Alternare lo stato virtualizzato di questo punto di interruzione corrente.|  
|[Abilita](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alternare lo stato attivato di questo punto di interruzione corrente.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Imposta o modifica la condizione associata a questo punto di interruzione corrente.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Imposta o modifica il conteggio della sessione associato a questo punto di interruzione corrente.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera i punti di interruzione limitano da questo punto di interruzione corrente.|  
|[EnumErrorBreakpoints](../Topic/IDebugPendingBreakpoint2::EnumErrorBreakpoints.md)|Enumera i punti di interruzione di errore in derivato da questo punto di interruzione corrente.|  
|[Delete](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|elimina questo punto di interruzione in corso e tutti i punti di interruzione limitano da.|  
  
## Note  
 `IDebugPendingBreakpoint2` può essere considerato come un provider di tutte le informazioni necessarie necessarie per associare un punto di interruzione da codificare applicabile a uno o più programma.  
  
 Di un punto di interruzione in attesa potenzialmente possibile scrivere più di un punto di interruzione associato.  Ad esempio, un punto di interruzione nel modello di tipo c \+\+\-style potrebbe produrre un punto di interruzione associato per ogni istanza univoca del modello.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../Topic/IDebugBoundBreakpoint2::GetPendingBreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)