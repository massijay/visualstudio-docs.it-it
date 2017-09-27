---
title: IDebugField::GetInfo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 12
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
ms.openlocfilehash: 60eb5889f197af894dc07478a08ede828090f8c2
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Questo metodo ottiene informazioni visualizzabili sul campo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 [in] Una combinazione di [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) le costanti che consente di selezionare informazioni da visualizzare. Se il campo rappresenta un simbolo, questo viene in genere il nome del simbolo e il tipo.  
  
 `pFieldInfo`  
 [out] Restituisce le informazioni nel fornito [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) struttura.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
