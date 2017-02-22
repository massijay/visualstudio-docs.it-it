---
title: "NATIVE_ADDRESS | Microsoft Docs"
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
  - "NATIVE_ADDRESS"
helpviewer_keywords: 
  - "Struttura NATIVE_ADDRESS"
ms.assetid: 7a0cd085-bfc8-45cc-a3d4-4459070e207a
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# NATIVE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa struttura rappresenta un indirizzo nativo.  
  
## Sintassi  
  
```cpp  
typedef struct _tagNATIVE_ADDRESS {  
   DWORD unknown;  
} NATIVE_ADDRESS;  
```  
  
```c#  
public struct NATIVE_ADDRESS {  
   public uint unknown;  
}  
```  
  
## termini  
 unknown  
 Indirizzo nativo \(il significato di questo dipende dal runtime e dal sistema operativo\).  
  
## Note  
 Questa struttura fa parte dell'[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) unione nella struttura quando il campo di `dwKind` della struttura di `DEBUG_ADDRESS_UNION` è impostato su `ADDRESS_KIND_NATIVE` \(un valore [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) dell'enumerazione\).  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)