---
title: IDebugCoreServer3::EnableAutoAttach | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords: IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23c7faed077b8af442d81593808f9360995ba246
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Consente l'associazione automatica per i motori di debug specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rgguidSpecificEngines`  
 [in] Matrice di GUID per ogni motore di debug per contrassegnare come collegamento automatico.  
  
 `celtSpecificEngines`  
 [in] Il numero di motori specificato in `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] L'URL inizia da utilizzare quando ci si connette automaticamente.  
  
 `pbstrSessionID`  
 [out] ID della sessione che è stato collegato automaticamente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore. Un codice di errore `E_AUTO_ATTACH_NOT_REGISTERED`, che indica che la class factory auto-attach non è stata registrata.  
  
## <a name="remarks"></a>Note  
 Quando viene avviato un programma associato all'URL specificato, i motori di debug specificata vengono automaticamente avviati e collegati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)