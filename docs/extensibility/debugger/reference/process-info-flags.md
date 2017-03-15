---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "Enumerazione PROCESS_INFO_FLAGS"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritto o specifica le proprietà di un processo.  
  
## Sintassi  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## Membri  
 PIFLAG\_SYSTEM\_PROCESS  
 Indica che il processo è un processo di sistema.  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 Indica che il processo sottoposto a debug da un debugger.  Può essere un debugger di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] , oppure può essere un altro debugger, ad esempio, WinDbg.  
  
 PIFLAG\_PROCESS\_STOPPED  
 Indica che il processo venga arrestato.  Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato.  Disponibile in [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] e versioni successive.  
  
 PIFLAG\_PROCESS\_RUNNING  
 Indica che è in esecuzione il processo.  Valido solo se `PIFLAG_DEBUGGER_ATTACHED` viene anche specificato.  Disponibile in [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)] e versioni successive.  
  
## Note  
 Utilizzato per il membro di `Flags` [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) della struttura.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)