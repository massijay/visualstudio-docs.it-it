---
title: BP_LOCATION_CODE_CONTEXT | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_CONTEXT
helpviewer_keywords: BP_LOCATION_CODE_CONTEXT structure
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 129a96c2c91d56f23ffb1ef61af32f6e85b40b75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="bplocationcodecontext"></a>BP_LOCATION_CODE_CONTEXT
Descrive il percorso di un punto di interruzione associato direttamente a un indirizzo nel programma sottoposto a debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _BP_LOCATION_CODE_CONTEXT {   
   IDebugCodeContext2* pCodeContext;  
} BP_LOCATION_CODE_CONTEXT;  
```  
  
## <a name="members"></a>Membri  
 pCodeContext  
 Il [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) oggetto che identifica la posizione del punto di interruzione nel codice.  
  
## <a name="remarks"></a>Note  
 Questa struttura è membro il [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struttura come parte di un'unione.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)