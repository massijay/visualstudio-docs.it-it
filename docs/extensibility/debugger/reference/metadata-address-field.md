---
title: "METADATA_ADDRESS_FIELD | Microsoft Docs"
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
  - "METADATA_ADDRESS_FIELD"
helpviewer_keywords: 
  - "Struttura METADATA_ADDRESS_FIELD"
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_FIELD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura rappresenta l'indirizzo di un campo di una classe o struttura.  
  
## Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```c#  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## termini  
 tokField  
 ID del token del campo.  
  
 \[C\+\+\] `_mdToken` è `typedef` per un 32 bit `int`.  
  
## Note  
 Questa struttura fa parte dell'[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) unione nella struttura quando il campo di `dwKind` della struttura di `DEBUG_ADDRESS_UNION` è impostato su `ADDRESS_KIND_FIELD` \(un valore [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) dell'enumerazione\).  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)