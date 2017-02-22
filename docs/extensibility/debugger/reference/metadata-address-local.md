---
title: "METADATA_ADDRESS_LOCAL | Microsoft Docs"
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
  - "METADATA_ADDRESS_LOCAL"
helpviewer_keywords: 
  - "Struttura METADATA_ADDRESS_LOCAL"
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura rappresenta l'indirizzo di una variabile locale all'interno di un ambito in genere una funzione o un metodo.  
  
## Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## termini  
 tokMethod  
 ID del metodo o viene eseguita la variabile locale fanno parte di.  
  
 \[C\+\+\] `_mdToken` è `typedef` per un 32 bit `int`.  
  
 pLocal  
 il token di cui l'indirizzo questa struttura rappresenta.  
  
 dwIndex  
 Può essere indice di questa variabile locale nel metodo o funzione, o un altro valore \(specifico della lingua\).  
  
## Note  
 Questa struttura fa parte dell'[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) unione nella struttura quando il campo di `dwKind` della struttura di `DEBUG_ADDRESS_UNION` è impostato su `ADDRESS_KIND_LOCAL` \(un valore [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) dell'enumerazione\).  
  
 `Warning:`\[C\+\+ solo\] se `pLocal` non è null, è necessario chiamare `Release` sul puntatore di token \(`addr` è un campo [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) della struttura\):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)