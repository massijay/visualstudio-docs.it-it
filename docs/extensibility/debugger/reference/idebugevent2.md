---
title: "IDebugEvent2 | Microsoft Docs"
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
  - "IDebugEvent2"
helpviewer_keywords: 
  - "Interfaccia IDebugEvent2"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per comunicare le informazioni di debug critiche, come arrestare un punto di interruzione che le informazioni non critiche, ad esempio un messaggio di debug.  
  
## Sintassi  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug e il fornitore di porte personalizzate implementano l'interfaccia nello stesso oggetto di tutte le altre interfacce eventi.  
  
## Note per i chiamanti  
 Utilizzo dell'ID dell'interfaccia \(IID\) fornita a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) o [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), le chiamate di amministratore di debug \(SDM\) della [QueryInterface](/visual-cpp/atl/queryinterface) sessione in `IDebugEvent2` interfaccia per ottenere l'interfaccia eventi appropriata.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugEvent2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|ottiene gli attributi per questo evento di debug.|  
  
## Note  
 Le interfacce eventi più specifiche, [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)ad esempio, non derivano dall'interfaccia IDebugEvent2 ma vengono implementate come un'interfaccia separata sullo stesso oggetto come `IDebugEvent2`.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)