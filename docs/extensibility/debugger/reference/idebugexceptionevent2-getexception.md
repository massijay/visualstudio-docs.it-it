---
title: IDebugExceptionEvent2::GetException | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExceptionEvent2::GetException
helpviewer_keywords: IDebugExceptionEvent2::GetException
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5cc68f7fb843e97e9333aa8d0223ed601df98273
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexceptionevent2getexception"></a>IDebugExceptionEvent2::GetException
Ottiene una descrizione dettagliata dell'eccezione che ha generato questo evento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```csharp  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pExceptionInfo`  
 [in, out] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura che viene compilato con la descrizione dell'eccezione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 [Solo C++] Il chiamante è responsabile per liberare tutte le stringhe nel [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura e il rilascio di [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) oggetto della struttura.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)