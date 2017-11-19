---
title: METADATA_ADDRESS_PARAM | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_PARAM
helpviewer_keywords: METADATA_ADDRESS_PARAM structure
ms.assetid: 90904f19-0e71-4cb3-a56e-6a2e92f66dfc
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 472eee2ee8cd657457e2c31331fbdedc2db075ae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="metadataaddressparam"></a>METADATA_ADDRESS_PARAM
Questa struttura rappresenta un parametro di un metodo o funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_PARAM {  
   _mdToken tokMethod;  
   _mdToken tokParam;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_PARAM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_PARAM {  
   public int  tokMethod;  
   public int  tokParam;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>Termini  
 tokMethod  
 L'ID del metodo il parametro fa parte di.  
  
 tokParam  
 L'ID del parametro.  
  
 dwIndex  
 L'indice del parametro in un elenco di parametri.  
  
## <a name="remarks"></a>Note  
 Questa struttura è parte dell'unione nel [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando il `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_PARAM` (compreso il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)