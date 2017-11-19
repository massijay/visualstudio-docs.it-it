---
title: IDebugDefaultPort2::GetPortNotify | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2::GetPortNotify
helpviewer_keywords: IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 938cd3a2ab87d2145f9dca2b9d60591027650114
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Questo metodo ottiene un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia per la porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppPortNotify`  
 [out] Un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 In genere, il `QueryInterface` metodo viene chiamato sull'oggetto che implementa il [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaccia per ottenere un [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interfaccia. Tuttavia, esistono casi in cui viene implementata l'interfaccia desiderato su un oggetto diverso. Questo metodo nasconde le circostanze e restituisce il `IDebugPortNotify2` interfaccia dall'oggetto più appropriato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)