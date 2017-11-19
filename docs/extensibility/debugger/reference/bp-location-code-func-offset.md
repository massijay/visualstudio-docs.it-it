---
title: BP_LOCATION_CODE_FUNC_OFFSET | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords: BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ccaf1b9c4aee385f26000bb6a397f32984dfe1a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodefuncoffset"></a>BP_LOCATION_CODE_FUNC_OFFSET
Descrive la posizione di offset di un punto di interruzione in una funzione nel codice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## <a name="members"></a>Membri  
 `bstrContext`  
 Il contesto del punto di interruzione, in genere un nome di metodo o una funzione come illustrato in uno stack di chiamate.  
  
 `pFuncPos`  
 Il [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) oggetto che descrive il nome della funzione e la posizione relativa a partire dall'inizio della funzione.  
  
## <a name="remarks"></a>Note  
 Questa struttura è membro il [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.  
  
 Il `pFuncPos` membro indica la posizione in cui il punto di interruzione di funzione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)