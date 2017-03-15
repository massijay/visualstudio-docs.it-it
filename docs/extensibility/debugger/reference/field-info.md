---
title: "FIELD_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_INFO"
helpviewer_keywords: 
  - "Struttura FIELD_INFO"
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura viene descritta una variabile locale, un parametro, o un altro campo.  
  
## Sintassi  
  
```cpp#  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```c#  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## Membri  
 dwFields  
 Una combinazione di flag [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) dall'enumerazione che specifica quali membri sono riempiti.  
  
 bstrFullName  
 Il nome completo del campo.  
  
 bstrName  
 Il nome breve del campo.  
  
 bstrType  
 Tipo del campo.  
  
 dwModifiers  
 Una combinazione di flag [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) dall'enumerazione che descrive il campo.  
  
## Note  
 Questa struttura viene passata [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) al metodo in cui viene soddisfatta.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD\_INFO\_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)