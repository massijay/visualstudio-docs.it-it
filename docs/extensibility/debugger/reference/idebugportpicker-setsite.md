---
title: IDebugPortPicker::SetSite | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4853d9ea3517cc5b589c6a9435b89a69738006d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Imposta il provider del servizio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSP`  
 [in] Riferimento all'interfaccia del provider del servizio.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo verrà chiamato prima della chiamata a qualsiasi altro metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)