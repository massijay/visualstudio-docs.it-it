---
title: IDebugEngine2::SetLocale | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::SetLocale
helpviewer_keywords: IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41ad173f706b655f4d43a101618127070ae9ac6e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
Imposta le impostazioni locali del motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `wLangID`  
 [in] Specifica le impostazioni locali della lingua. Ad esempio 1033 per l'inglese.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato dal gestore di sessione di debug (SDM) per propagare le impostazioni locali dell'IDE in modo che le stringhe restituite per la Germania sono localizzate in modo corretto.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)