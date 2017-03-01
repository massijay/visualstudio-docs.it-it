---
title: BP_ERROR_TYPE | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 07248d28d34373176f9897472c39c0756012da59
ms.lasthandoff: 02/22/2017

---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Specifica il tipo di errore di un punto di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```c#  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membri  
 BPET_NONE  
 È specificato alcun errore di punto di interruzione.  
  
 BPET_TYPE_WARNING  
 Specifica un punto di interruzione di tipo avviso di errore.  
  
 BPET_TYPE_ERROR  
 Specifica un errore del punto di interruzione lo stile di errore.  
  
 BPET_SEV_HIGH  
 Specifica un punto di interruzione di alta gravità errore.  
  
 BPET_SEV_GENERAL  
 Specifica un punto di interruzione di medio livello di gravità errore.  
  
 BPET_SEV_LOW  
 Specifica un punto di interruzione di basso livello di gravità errore.  
  
 BPET_TYPE_MASK  
 Specifica un errore del punto di interruzione maschera stile.  
  
 BPET_SEV_MASK  
 Specifica un punto di interruzione tipo di maschera gravità errore.  
  
 BPET_GENERAL_WARNING  
 Specifica un punto di interruzione stile generale-avviso di errore.  
  
 BPET_GENERAL_ERROR  
 Specifica un punto di interruzione lo stile di errore generale di errore.  
  
 BPET_ALL  
 Specifica tutti i tipi di errore di punto di interruzione.  
  
## <a name="remarks"></a>Note  
 Questi valori possono essere combinati con un bit per bit `OR` e viene utilizzato per il `dwType` membro del [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struttura. Passato come parametro per il [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metodo.  
  
 Un tipo di errore di interruzione è composta da un tipo e un livello di gravità. Ciò significa che un tipo di errore di interruzione non è solo un tipo (ad esempio, `BPET_TYPE_ERROR`,) o un livello di gravità (ad esempio, `BPET_SEV_GENERAL`) da solo. `BPET_GENERAL_WARNING`e `BPET_GENERAL_ERROR` fornire valori predefiniti dei punti di interruzione di avviso ed errore generale.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
