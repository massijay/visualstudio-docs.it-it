---
title: IDebugThread2::Suspend | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 9
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
ms.openlocfilehash: 3926456c8b625102dfc5df4d8818f3cacc3a2ce3
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Sospende un thread.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwSuspendCount`  
 [out] Restituisce il conteggio di sospensione dopo l'operazione di sospensione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Ogni chiamata a questo metodo incrementa il conteggio di sospensione maggiore di 0. Questo conteggio di sospensione viene visualizzato nel **thread** finestra di debug.  
  
 Per ogni chiamata a questo metodo, deve essere una chiamata successiva al [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)
