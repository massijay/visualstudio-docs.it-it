---
title: IDebugObject::GetMemoryContext | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetMemoryContext
helpviewer_keywords: IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93f6d82b88be23b160effe1c8162648132f461c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Ottiene il contesto di memoria che rappresenta l'indirizzo del valore dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```csharp  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pContext`  
 [out] Restituisce un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto che rappresenta l'indirizzo del valore dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il contesto di memoria restituito specifica l'indirizzo del valore come rappresentato da questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)