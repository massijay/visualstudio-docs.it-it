---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia è un'interfaccia di estensione implementata [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) dagli implementatori.  Consente all'implementatore ottenere le informazioni sull'ambiente di processo di debug.  
  
## Sintassi  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## Note per gli implementatori  
 Implementare questa interfaccia per ottenere informazioni sull'ambiente di esecuzione di un processo di debug.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProcessQueryProperties`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[QueryProperty](../Topic/IDebugProcessQueryProperties::QueryProperty.md)|Query per un valore di proprietà.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Query per i valori della proprietà.|  
  
## Note  
 Questa interfaccia viene implementata raramente.  
  
## Requisiti  
 intestazione: Portpriv.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)