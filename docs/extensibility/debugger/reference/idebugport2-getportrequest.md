---
title: IDebugPort2::GetPortRequest | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPort2::GetPortRequest
helpviewer_keywords: IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df00ec25a4f417e6a84a5c42f04f082df6e0b05c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ottiene la descrizione di una porta utilizzata per creare la porta (se disponibile).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppRequest`  
 [out] Restituisce un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) oggetto che rappresenta la richiesta è stata utilizzata per creare la porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce `E_PORT_NO_REQUEST` se una porta non è stata creata utilizzando un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) richiesta porta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)