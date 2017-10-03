---
title: IDebugProcessSecurity::GetUserName | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
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
ms.openlocfilehash: 081f073ba59021ca56dd084bd2cef0fde6c5c32e
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ottiene il nome utente dal fornitore porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrUserName`  
 [out] Stringa contenente il nome utente.  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`. In caso contrario viene restituito un codice di errore.  
  
## <a name="remarks"></a>Note  
 `GetUserName`Restituisce il nome utente visualizzato nel **nome utente** colonna il **Connetti a processo** la finestra di dialogo. Per visualizzare il **Connetti a processo** nella finestra di dialogo fare clic su **Connetti a processo** sul **strumenti** dal menu di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
