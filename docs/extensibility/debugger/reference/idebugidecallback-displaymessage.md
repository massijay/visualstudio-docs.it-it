---
title: IDebugIDECallback::DisplayMessage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 7b3f7e5fde160bc9d1e5ece61b810090c5dd7d9b
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
Invia la stringa di messaggio specificato alla finestra di output del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szMessage`  
 [in] Stringa di messaggio da visualizzare nella finestra di output del debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
