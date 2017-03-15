---
title: "ADDRESS_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "Enumerazione ADDRESS_KIND"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica i tipi degli indirizzi.  
  
## Sintassi  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```c#  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## termini  
 ADDRESS\_KIND\_NATIVE  
 Un indirizzo nativo, rappresentato [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) dalla struttura.  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 Un indirizzo non gestito a un puntatore di `this` \(`Me` in Visual Basic\) e rappresentato [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) dalla struttura.  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 Un indirizzo fisico non gestito, rappresentato [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) dalla struttura.  
  
 ADDRESS\_KIND\_METHOD  
 Un metodo di una classe, rappresentato [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) dalla struttura.  
  
 ADDRESS\_KIND\_FIELD  
 Un campo di una classe, rappresentato [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) dalla struttura.  
  
 ADDRESS\_KIND\_LOCAL  
 L'indirizzo di una variabile locale ed è rappresentato [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) dalla struttura.  
  
 ADDRESS\_KIND\_PARAM  
 Un metodo o un parametro di funzione, rappresentato [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) dalla struttura.  
  
 ADDRESS\_KIND\_ARRAYELEM  
 Un elemento di matrice, rappresentato [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) dalla struttura.  
  
 ADDRESS\_KIND\_RETVAL  
 Un valore restituito, rappresentato [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) dalla struttura.  
  
## Note  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) Il metodo restituisce [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) la struttura che contiene un'unione di strutture possibili, [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) la struttura.  Il campo di `dwKind` della struttura di `DEBUG_ADDRESS_UNION` utilizza il valore di `ADDRESS_KIND` e viene descritto come interpretare il campo di unione.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)