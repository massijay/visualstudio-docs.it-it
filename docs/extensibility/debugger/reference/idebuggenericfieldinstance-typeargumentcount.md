---
title: IDebugGenericFieldInstance::TypeArgumentCount | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddaf2ff3323bb7e4e1da55eb1b8ad8cd8931f9c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Restituisce il numero del tipo di argomenti di parametro per questa istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcArgs`  
 [in, out] Numero di argomenti di parametro di tipo per questa istanza.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ad esempio, se elenco\<int >, questo metodo restituisce 1 e, se elenco\<int, float2 > questo metodo restituisce 2. Questo metodo restituisce 0 se non sono presenti argomenti di tipo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)