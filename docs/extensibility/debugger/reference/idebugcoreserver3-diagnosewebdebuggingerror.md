---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
caps.latest.revision: 8
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 04a8ecbb1bfdc7f14f6b493df7f1dc9e16b53cd6
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Per determinare il motivo per cui un auto-attach tentativi non riusciti.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DiagnoseWebDebuggingError(  
   LPCWSTR pszUrl  
);  
```  
  
```c#  
int DiagnoseWebDebuggingError(  
   string pszUrl  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszUrl`  
 [in] Non è attualmente utilizzato; deve sempre essere impostato su un valore null.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Altri codici restituiti tipici sono i seguenti:  
  
|Codice|Descrizione|  
|----------|-----------------|  
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Impossibile determinare perché il server remoto non è riuscito avviare il debug.|  
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Impossibile eseguire il debug sul server remoto, probabilmente a causa di autorizzazioni insufficienti o perché non è abilitato il verbo DEBUG.|  
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|Il server web è stato bloccato e blocca il verbo DEBUG, che è necessario abilitare il debug.|  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
