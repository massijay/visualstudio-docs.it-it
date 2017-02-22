---
title: "MACHINE_INFO | Microsoft Docs"
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
  - "MACHINE_INFO"
helpviewer_keywords: 
  - "Struttura MACHINE_INFO"
ms.assetid: e7564ff2-00b5-4750-8fd5-dc1029a16912
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# MACHINE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Descrive un particolare computer.  
  
## Sintassi  
  
```cpp#  
typedef struct tagMACHINE_INFO {   
   MACHINE_INFO_FIELDS Fields;  
   BSTR                bstrName;  
   MACHINE_INFO_FLAGS  Flags;  
} MACHINE_INFO;  
```  
  
```c#  
public struct MACHINE_INFO {   
   public uint   Fields;  
   public string bstrName;  
   public uint   Flags;  
};  
```  
  
## Membri  
 `Fields`  
 Una combinazione di flag [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) dall'enumerazione che specificano i campi della struttura vengono inizializzati.  
  
 `bstrName`  
 Il nome del computer.  equivalente a chiamare [GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md).  
  
 `Flags`  
 Una combinazione di flag [MACHINE\_INFO\_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) dall'enumerazione che descrive gli attributi del computer.  
  
## Note  
 Questa struttura viene restituita da una chiamata [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) al metodo.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MACHINE\_INFO\_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)