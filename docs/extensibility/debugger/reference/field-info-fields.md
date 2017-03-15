---
title: "FIELD_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO_FIELDS"
helpviewer_keywords: 
  - "Enumerazione FIELD_INFO_FIELDS"
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare su [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) un oggetto.  
  
## Sintassi  
  
```cpp#  
enum enum_FIELD_INFO_FIELDS {   
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
typedef DWORD FIELD_INFO_FIELDS;  
```  
  
```c#  
public enum enum_FIELD_INFO_FIELDS {  
   FIF_FULLNAME  = 0x0001,  
   FIF_NAME      = 0x0002,  
   FIF_TYPE      = 0x0004,  
   FIF_MODIFIERS = 0x0008,  
   FIF_ALL       = 0xffffffff,  
   FIF_NONE      = 0x0000  
};  
```  
  
## Membri  
 FIF\_FULLNAME  
 Inizializzare\/utilizzare il campo di `bstrFullName` [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) nella struttura.  
  
 FIF\_NAME  
 Inizializzare\/utilizzare il campo di `bstrName` nella struttura di `FIELD_INFO` .  
  
 FIF\_TYPE  
 Inizializzare\/utilizzare il campo di `bstrType` nella struttura di `FIELD_INFO` .  
  
 FIF\_MODIFIERS  
 Inizializzare\/utilizzare il campo di `bstrModifiers` nella struttura di `FIELD_INFO` .  
  
## Note  
 Questi valori vengono passati come argomento al [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metodo per specificare che i campi [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) della struttura devono essere inizializzati.  
  
 Questi valori vengono utilizzati nel membro di `dwFields` della struttura di `FIELD_INFO` per indicare quali campi vengono utilizzati e validi.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)