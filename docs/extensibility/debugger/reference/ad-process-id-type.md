---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "Enumerazione AD_PROCESS_ID_TYPE"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica come interpretare un ID processo [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) nella struttura.  
  
## Sintassi  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## Membri  
 AD\_PROCESS\_ID\_SYSTEM  
 L'ID processo è un identificatore di sistema.  Utilizzare il campo di `ProcessId.dwProcessId` [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) della struttura.  
  
 AD\_PROCESS\_ID\_GUID  
 l'ID processo è un GUID.  Utilizzare il campo di `ProcessId.guidProcessId` della struttura di `AD_PROCESS_ID` .  
  
## Note  
 Utilizzato per il membro di `ProcessIdType` [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) della struttura per identificare il tipo di ID del contenuto nella struttura.  Determina come interpretare l'unione di `ProcessId` nella struttura.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)