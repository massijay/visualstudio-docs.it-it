---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
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
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "Struttura METADATA_ADDRESS_METHOD"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura rappresenta l'indirizzo di un metodo di una classe.  
  
## Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## termini  
 tokMethod  
 ID del metodo.  
  
 \[C\+\+\] `_mdToken` è `typedef` per un 32 bit `int`.  
  
 dwOffset  
 L'offset dall'inizio della classe a questo metodo \(possibile rappresentare offset nella tabella vtable\).  
  
 dwVersion  
 La versione del metodo \(questo valore è univoco al provider di simboli\).  
  
## Note  
 Questa struttura fa parte dell'[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) unione nella struttura quando il campo di `dwKind` della struttura di `DEBUG_ADDRESS_UNION` è impostato su `ADDRESS_KIND_METHOD` \(un valore [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) dell'enumerazione\).  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)