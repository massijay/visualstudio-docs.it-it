---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords: IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f1ff74931ac5433ff22330bc6f218315ccaf259
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Questo metodo utilizza una ricerca con distinzione tra maiuscole e per restituire il valore associato al nome di una costante di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pszValue`  
 [in] Stringa che specifica il nome per il quale ottenere il valore. Si noti che per C++, si tratta di una stringa di caratteri wide.  
  
 `pValue`  
 [out] Restituisce il valore numerico associato.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`, se il nome non fa parte di enumerazione o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo è tra maiuscole e minuscole. Se una ricerca con distinzione maiuscole/minuscole è necessario (ad esempio, in un linguaggio quale C++ in cui i nomi di maiuscole e minuscole), utilizzare [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)