---
title: IDebugCanStopEvent2::GetReason | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b5d4c50b407406ea9a5d878decf859b8ab70863d
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Ottiene il motivo per cui il motore di debug (DE) desidera arrestare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcr`  
 [out] Restituisce un valore di [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumerazione che descrive il motivo per questo evento.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene in genere chiamato prima di [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) metodo in modo che il chiamante può determinare se passare diverso da zero (`TRUE`) per il `IDebugCanStopEvent2::CanStop` metodo.  
  
 Il motivo per l'arresto può essere `CANSTOP_ENTRYPOINT`, ovvero la Germania ha raggiunto un punto di ingresso, o `CANSTOP_STEPIN`, ovvero la Germania ha eseguito l'accesso una funzione.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
