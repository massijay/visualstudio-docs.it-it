---
title: BP_COND_STYLE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_COND_STYLE
helpviewer_keywords: BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2dd89bd7e70e619bea5f1f2cb17b70e98eecaf3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Specifica lo stile di condizione punto di interruzione per in sospeso e associati i punti di interruzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```csharp  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## <a name="members"></a>Membri  
 BP_COND_NONE  
 Quando la posizione del punto di interruzione viene raggiunto, viene attivato il punto di interruzione. Nessuna condizione punto di interruzione specificata.  
  
 BP_COND_WHEN_TRUE  
 Viene attivato il punto di interruzione solo quando il punto di interruzione associata l'espressione condizionale restituisce `true`.  
  
 BP_COND_WHEN_CHANGED  
 Viene attivato il punto di interruzione solo quando il valore dell'espressione condizionale associato dal punto di interruzione è stata modificata dalla relativa valutazione precedente.  
  
## <a name="remarks"></a>Note  
 Utilizzato per il `styleCondition` appartenente il [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) struttura.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)