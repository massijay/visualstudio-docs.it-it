---
title: IEnumDebugErrorBreakpoints2::Next | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugErrorBreakpoints2::Next
helpviewer_keywords: IEnumDebugErrorBreakpoints2::Next
ms.assetid: 6a3dee11-5267-4d77-9e28-6a38413ba70b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 227eaaabb1ad312b307040236d961c3b0b3a5b00
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugerrorbreakpoints2next"></a>IEnumDebugErrorBreakpoints2::Next
Restituisce il set successivo di elementi dall'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Next(  
   ULONG                    celt,  
   IDebugErrorBreakpoint2** rgelt,  
   ULONG*                   pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                     celt,  
   IDebugErrorBreakpoint2[] rgelt,  
   ref uint                 pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Il numero di elementi da recuperare. Specifica inoltre la dimensione massima del `rgelt` matrice.  
  
 `rgelt`  
 [in, out] Matrice di [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) elementi da compilare.  
  
 `pceltFetched`  
 [out] Restituisce il numero di elementi effettivamente restituiti nella `rgelt`.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`. Restituisce `S_FALSE` se può essere inferiore al numero di elementi richiesto sia restituiti; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)