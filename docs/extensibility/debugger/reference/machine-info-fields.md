---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
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
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumerazione MACHINE_INFO_FIELDS"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di informazioni per recuperare un determinato computer.  
  
## Sintassi  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## Membri  
 MCIF\_NAME  
 Inizializzare\/utilizzare il campo di `bstrName` nella struttura.  
  
 MCIF\_FLAGS  
 Inizializzare\/utilizzare il campo di `Flags` nella struttura.  
  
 MIF\_ALL  
 Inizializzare\/utilizzare tutti i campi nella struttura.  
  
## Note  
 Questi valori vengono passati [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md) al metodo per indicare i membri [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) della struttura devono essere inizializzati.  
  
 Utilizzata anche nel membro di `Fields` della struttura di `MACHINE_INFO` per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../Topic/IDebugCoreServer2::GetMachineInfo.md)