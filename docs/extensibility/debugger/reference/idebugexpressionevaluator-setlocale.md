---
title: IDebugExpressionEvaluator::SetLocale | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpressionEvaluator::SetLocale
helpviewer_keywords: IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bdba51967b470023deb5997bc243b900e3155245
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Questo metodo imposta la lingua da utilizzare per creare risultati stampabili.  
  
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
 [in] L'identificatore di lingua.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Può essere chiamato più volte mentre l'analizzatore di espressioni (Java EE) viene caricato, pertanto l'analizzatore di Espressioni deve essere in grado di cambiare la lingua in tempo reale. L'analizzatore di Espressioni utilizza queste impostazioni locali per restituire messaggi di errore e le stringhe nella lingua corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)