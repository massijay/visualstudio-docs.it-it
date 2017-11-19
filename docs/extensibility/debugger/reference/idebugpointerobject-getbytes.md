---
title: IDebugPointerObject::GetBytes | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::GetBytes
helpviewer_keywords: IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e94564eaaf10765e68e35fa4f573efae7c74dc7e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ottiene il valore a cui punta come una serie di byte consecutivi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwStart`  
 [in] Offset, in byte, dall'inizio dell'oggetto a cui puntata.  
  
 `dwCount`  
 [in] Il numero di byte da recuperare.  
  
 `pBytes`  
 [in, out] Matrice che viene compilata con il valore come una serie di byte consecutivi, a partire dall'offset specificato dall'oggetto a cui punta.  
  
 `pdwBytes`  
 [out] Restituisce il numero di byte effettivamente recuperati.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene utilizzato se il puntatore come rappresentato da questo [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) punta a un tipo primitivo o di una semplice matrice di tipi primitivi (ovvero, una matrice che può essere rappresentato da una semplice sequenza di byte).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)