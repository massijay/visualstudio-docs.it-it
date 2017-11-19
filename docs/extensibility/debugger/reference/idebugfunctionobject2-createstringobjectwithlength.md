---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78b5f21a2b2f018c4eb35007cdfd2aa4f67b5ebf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Crea un oggetto stringa che ha la lunghezza specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcstrString`  
 [in] Il valore di stringa per l'oggetto stringa.  
  
 `uiLength`  
 [in] La lunghezza della stringa in byte.  
  
 `ppObject`  
 [out] Restituisce un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto che rappresenta l'oggetto stringa appena creata.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)