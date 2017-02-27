---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "Interfaccia IDebugCoreServer2"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia viene utilizzata per rappresentare e ottenere informazioni da un server in un computer nella rete.  
  
## Sintassi  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## Note per gli implementatori  
 Visual Studio implementa questa interfaccia per rappresentare un server.  Ogni istanza di Visual Studio crea un'istanza dell'interfaccia.  
  
## Note per i chiamanti  
 un fornitore di porte personalizzato riceve questa interfaccia in una chiamata a [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Il modulo di debug possibile ottenere indirettamente questa interfaccia con una [Metodo GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) chiamata \(che restituisce [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), un'interfaccia derivata da `IDebugCoreServer2`\).  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugCoreServer2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)|ottiene il nome e gli attributi di un computer.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|ottiene il nome di un computer.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ottiene un fornitore di porte che esiste in un computer.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ottiene una porta che già esiste nel computer.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumeratore per tutte le porte in un computer.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumeratore per tutti i fornitori di porte in un computer.|  
|[GetMachineUtilities\_V7](../Topic/IDebugCoreServer2::GetMachineUtilities_V7.md)|Ottiene le utilità del computer per un computer.|  
  
## Note  
 Questa interfaccia viene utilizzata da Visual Studio per esplorare i processi in esecuzione su computer in rete.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Metodo GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)