---
title: "DEBUGREF_INFO_FLAGS | Microsoft Docs"
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
  - "DEBUGREF_INFO_FLAGS"
helpviewer_keywords: 
  - "Enumerazione DEBUGREF_INFO_FLAGS"
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUGREF_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare su un oggetto di riferimento di debug.  
  
## Sintassi  
  
```cpp#  
enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
typedef DWORD DEBUGREF_INFO_FLAGS;  
```  
  
```c#  
public enum enum_DEBUGREF_INFO_FLAGS {   
   DEBUGREF_INFO_NAME             = 0x00000001,  
   DEBUGREF_INFO_TYPE             = 0x00000002,  
   DEBUGREF_INFO_VALUE            = 0x00000004,  
   DEBUGREF_INFO_ATTRIB           = 0x00000008,  
   DEBUGREF_INFO_REFTYPE          = 0x00000010,  
   DEBUGREF_INFO_REF              = 0x00000020,  
   DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,  
   DEBUGREF_INFO_NONE             = 0x00000000,  
   DEBUGREF_INFO_ALL              = 0xffffffff  
};  
```  
  
## Membri  
 DEBUGREF\_INFORMATION\_NAME  
 Inizializzare\/utilizzare il campo di `bstrName` nella struttura.  
  
 DEBUGREF\_INFORMATION\_TYPE  
 Inizializzare\/utilizzare il campo di `bstrType` nella struttura.  
  
 DEBUGREF\_INFORMATION\_VALUE  
 Inizializzare\/utilizzare il campo di `bstrValue` nella struttura.  
  
 DEBUGREF\_INFORMATION\_ATTRIB  
 Inizializzare\/utilizzare il campo di`dwAttrib` nella struttura.  
  
 DEBUGREF\_INFORMATION\_REFTYPE  
 Inizializzare\/utilizzare il campo di `dwRefType` nella struttura.  
  
 DEBUGREF\_INFORMATION\_REF  
 Inizializzare\/utilizzare il campo di `pReference` nella struttura.  
  
 DEBUGREF\_INFORMATION\_VALUE\_AUTOEXPAND  
 Il campo di valore deve contenere il valore auto\-espanso, se disponibile, per questo tipo di oggetto.  
  
 DEBUGREF\_INFORMATION\_NONE  
 indica che nessun flag è impostato.  
  
 DEBUGREF\_INFORMATION\_ALL  
 Indica una maschera di flag.  
  
## Note  
 Questi flag vengono passati [EnumChildren](../Topic/IDebugReference2::EnumChildren.md) [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) ai metodi e per indicare i campi [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) della struttura devono essere inizializzati.  
  
 Utilizzato per il membro di `dwFields` della struttura di `DEBUG_REFERENCE_INFO` per indicare quali campi vengono utilizzati e valido quando la struttura viene restituita.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [EnumChildren](../Topic/IDebugReference2::EnumChildren.md)   
 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)