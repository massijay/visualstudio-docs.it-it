---
title: IDebugProcessEx2::Attach | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Attach
helpviewer_keywords: IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111895b73ee9685b9608be9812452d04d84cd48c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
Questo metodo indica il processo di una sessione è ora il debug del processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSession`  
 [in] Un valore che identifica in modo univoco la sessione di connessione a questo processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia passato `pSession` deve essere utilizzato solo come un cookie, un valore che identifica in modo univoco il gestore sessione di debug di connessione a questo processo; i metodi di interfaccia specificato non è funzionale.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)