---
title: "METADATA_ADDRESS_RETVAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_RETVAL"
helpviewer_keywords: 
  - "Struttura METADATA_ADDRESS_RETVAL"
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa struttura rappresenta un valore restituito da un metodo o funzione.  
  
## Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```c#  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## Termini  
 tokMethod  
 L'ID del metodo per il valore restituito.  
  
 dwCorType  
 Tipo di base del valore restituito. Questo è un valore compreso il `CorElementType` definita nell'enumerazione di [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] file SDK CorHdr. h.  
  
 dwSigSize  
 La dimensione della firma del valore restituito \(archiviata nel `rgSig`\).  
  
 rgSig  
 Matrice di byte che costituiscono la firma del valore restituito.  
  
## Note  
 Questa struttura è parte dell'unione nel [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando la `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_RETVAL` \(compreso il [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione\).  
  
## Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)