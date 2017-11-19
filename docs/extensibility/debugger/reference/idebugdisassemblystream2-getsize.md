---
title: IDebugDisassemblyStream2::GetSize | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetSize
helpviewer_keywords: IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35dfb225c6359e3b039b21255b1e6ba5979c3e6f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Ottiene le dimensioni nelle istruzioni del flusso disassembly.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetSize(   
   UINT64* pnSize  
);  
```  
  
```csharp  
int GetSize(   
   out ulong pnSize  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pnSize`  
 [out] Restituisce le dimensioni, nelle istruzioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il valore restituito da questo metodo può essere utilizzato per allocare una matrice di [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) strutture che viene quindi passato al [lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)