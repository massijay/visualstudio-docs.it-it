---
title: IDebugMemoryContext2::Subtract | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b1dc686846e0ca1e60f6bfce03dc5976c0d1d34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Sottrae il valore specificato nel contesto corrente e restituisce un nuovo contesto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCount`  
 [in] Il numero di byte di memoria da decrementare.  
  
 `ppMemCxt`  
 [out] Restituisce un nuovo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un contesto di memoria è un indirizzo, pertanto se si sottrae un valore da un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia di contesto.  
  
 Questo metodo deve restituire sempre un nuovo contesto, anche se l'indirizzo risulta è all'esterno dello spazio di memoria associato al contesto corrente. L'unica eccezione è se non vi è memoria da allocare per il nuovo contesto o se `ppMemCxt` è un valore null (che è un errore).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)