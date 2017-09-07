---
title: METADATA_ADDRESS_ARRAYELEM | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: df941d56a1b9baf8ffa15b022e0b9577da143fc8
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="metadataaddressarrayelem"></a>METADATA_ADDRESS_ARRAYELEM
Questa struttura rappresenta un elemento di matrice all'interno di una matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>Termini  
 tokMethod  
 L'ID della matrice di questo elemento è una parte.  
  
 [C++] `_mdToken` è un `typedef` un 32-bit `int`.  
  
 dwIndex  
 L'indice di questo elemento all'interno della matrice.  
  
## <a name="remarks"></a>Note  
 Questa struttura è parte dell'unione nel [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando il `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_ARRAYELEM` (compreso il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
