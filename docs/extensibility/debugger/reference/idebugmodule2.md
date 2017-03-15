---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "Interfaccia IDebugModule2"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta modulo\-che è, un'unità eseguibile di un programma\-tale come DLL.  
  
## Sintassi  
  
```  
IDebugModule2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per rappresentare un modulo e per fornire l'accesso alle informazioni su tale modulo.  
  
## Note per i chiamanti  
 Una chiamata [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) a restituisce questa interfaccia.  Il DE invia [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) l'interfaccia gestione \(SDM\) di debug della sessione utilizzando il metodo [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  
  
 Tale interfaccia può essere restituita [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) in una struttura \(restituita da una chiamata [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)a\).  
  
 [Successivo](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) restituisce anche questa interfaccia \([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) restituisce [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) l'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugModule2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Ottiene [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) l'oggetto che descrive il modulo.|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO.  NOT UTILIZZARE.  Ricaricare i simboli per questo modulo.|  
  
## Note  
 Le informazioni del modulo possono essere visualizzati nella finestra di **moduli** dell'IDE.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)