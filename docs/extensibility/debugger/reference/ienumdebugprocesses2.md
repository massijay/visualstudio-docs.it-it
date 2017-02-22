---
title: "IEnumDebugProcesses2 | Microsoft Docs"
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
  - "IEnumDebugProcesses2"
helpviewer_keywords: 
  - "IEnumDebugProcesses2"
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia enumera i processi in esecuzione su una porta di debug.  
  
## Sintassi  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## Note per gli implementatori  
 Un fornitore di porte personalizzato implementa questa interfaccia per definire un elenco di processi in esecuzione su una porta.  
  
## Note per i chiamanti  
 chiamate di Visual Studio [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md) per ottenere questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugProcesses2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera un numero specificato dei processi in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora un numero specificato dei processi in una sequenza di enumerazione.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../Topic/IEnumDebugProcesses2::Clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Ottiene il numero di processi in un enumeratore.|  
  
## Note  
 Visual Studio utilizza questa interfaccia per popolare la finestra di **processi** .  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../Topic/IDebugPort2::EnumProcesses.md)