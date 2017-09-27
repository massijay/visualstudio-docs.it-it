---
title: IDebugEngine2::SetException | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 10
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
ms.openlocfilehash: 2d7d1631c1b5179d51a80b2094766c4ed053ac36
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Specifica come il motore di debug (DE) deve gestire una determinata eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pException`  
 [in] Un [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struttura che descrive l'eccezione e come eseguirne il debug.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Era possibile indicare un Germania per arrestare il programma genera un'eccezione durante la prima opportunità, ovvero la seconda possibilità, o non è affatto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
