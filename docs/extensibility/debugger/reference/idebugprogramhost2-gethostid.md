---
title: IDebugProgramHost2::GetHostId | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramHost2::GetHostId
helpviewer_keywords: IDebugProgramHost2::GetHostId
ms.assetid: 7702e221-feb1-446b-a224-cb46c420987e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af778ce0f2b5d14a952426abe6d068e7b8ff6b30
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramhost2gethostid"></a>IDebugProgramHost2::GetHostId
Ottiene l'identificatore di processo del processo che ospita questo programma.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetHostId(   
   AD_PROCESS_ID* pdwId  
);  
```  
  
```csharp  
int GetHostId(   
   AD_PROCESS_ID[] pdwId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwId`  
 [in, out] Un [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) struttura che viene compilato con le informazioni di identificazione del processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)