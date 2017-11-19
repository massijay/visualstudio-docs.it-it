---
title: IDebugAddress::GetAddress | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Restituisce una struttura che descrive un oggetto e la relativa posizione all'interno dell'ambito o di un contenitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in, out] Oggetto [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura che viene compilato da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura viene passata a questo metodo, che quindi viene riempita con le informazioni appropriate. Modalità di interpretazione di queste informazioni dipende dal tipo di informazioni restituite e il gestore di simboli se stesso. Vedere [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) per altri dettagli.  
  
## <a name="see-also"></a>Vedere anche  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)