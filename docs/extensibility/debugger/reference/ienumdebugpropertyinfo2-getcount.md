---
title: IEnumDebugPropertyInfo2::GetCount | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPropertyInfo2::GetCount
helpviewer_keywords: IEnumDebugPropertyInfo2::GetCount
ms.assetid: 9b0b3ce6-08cb-46fd-a6d9-92b36e60da19
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1a9d464aab2b75f90b2e32d30529ce5d063da321
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugpropertyinfo2getcount"></a>IEnumDebugPropertyInfo2::GetCount
Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcelt`  
 [out] Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non è solitamente si interfaccia COM di enumerazione che specifica che solo il `Next`, `Clone`, `Skip`, e `Reset` metodi devono essere implementate.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)