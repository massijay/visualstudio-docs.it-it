---
title: "MODULE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumerazione MODULE_INFO_FIELDS"
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica i flag per le informazioni del modulo di debug.  
  
## Sintassi  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## Membri  
 MIF\_NONE  
 Inizializzare\/utilizzare nessuno dei campi della struttura.  
  
 MIF\_NAME  
 Inizializzare\/utilizzare il campo di `m_bstrName` [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) nella struttura.  
  
 MIF\_URL  
 Inizializzare\/utilizzare il campo di `m_bstrUrl` nella struttura di `MODULE_INFO` .  
  
 MIF\_VERSION  
 Inizializzare\/utilizzare il campo di `m_bstrVersion` nella struttura di `MODULE_INFO` .  
  
 MIF\_DEBUGMESSAGE  
 Inizializzare\/utilizzare il campo di `m_bstrDebugMessage` nella struttura di `MODULE_INFO` .  
  
 MIF\_LOADADDRESS  
 Inizializzare\/utilizzare il campo di `m_addrLoadAddress` nella struttura di `MODULE_INFO` .  
  
 MIF\_PREFFEREDADDRESS  
 Inizializzare\/utilizzare il campo di `m_addrPreferredLoadAddress` nella struttura di `MODULE_INFO` .  
  
 MIF\_SIZE  
 Inizializzare\/utilizzare il campo di `m_dwSize` nella struttura di `MODULE_INFO` .  
  
 MIF\_LOADORDER  
 Inizializzare\/utilizzare il campo di `m_dwLoadOrder` nella struttura di `MODULE_INFO` .  
  
 MIF\_TIMESTAMP  
 Inizializzare\/utilizzare il campo di `m_TimeStamp` nella struttura di `MODULE_INFO` .  
  
 MIF\_URLSYMBOLLOCATION  
 Inizializzare\/utilizzare il campo di `m_bstrUrlSymbolLocation` nella struttura di `MODULE_INFO` .  
  
 MIF\_FLAGS  
 Inizializzare\/utilizzare il campo di `m_dwModuleFlags` nella struttura di `MODULE_INFO` .  
  
 MIF\_ALLFIELDS  
 Inizializzare\/utilizzare tutti i campi nella struttura di `MODULE_INFO` .  
  
## Note  
 Questi valori vengono passati come argomento al [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) metodo per indicare i campi [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) della struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati nella struttura di `MODULE_INFO` per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)