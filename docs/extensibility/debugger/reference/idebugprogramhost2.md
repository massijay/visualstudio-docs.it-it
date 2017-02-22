---
title: "IDebugProgramHost2 | Microsoft Docs"
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
  - "IDebugProgramHost2"
helpviewer_keywords: 
  - "Interfaccia IDebugProgramHost2"
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia fornisce informazioni \(considerate\) host su un programma.  
  
## Sintassi  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore di debug implementa questa interfaccia lo stesso oggetto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dell'interfaccia per fornire informazioni sul processo di hosting.  Si tratta di un'interfaccia facoltativa.  
  
## Note per i chiamanti  
 chiamata [QueryInterface](/visual-cpp/atl/queryinterface) su un'interfaccia di `IDebugProgram2` per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugProgramHost2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Ottiene il titolo, il nome descrittivo, o il nome file del processo di hosting di questo programma.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Ottiene l'identificatore del processo di hosting del programma.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Ottiene il nome del computer che il processo di hosting di questo programma viene eseguito.|  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)