---
title: IDiaStackFrame::get_registerValue | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a454beb98fc8579bf625dbdb64db1cf60f8dd50a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Recupera il valore di un registro specificato come indicato nel frame dello stack.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `registerIndex`  
 [in] Uno del [CV_HREG_e (enumerazione)](../../debugger/debug-interface-access/cv-hreg-e.md) valori di enumerazione.  
  
 `pRetVal`  
 [out] Valore memorizzato nel registro.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [CV_HREG_e (enumerazione)](../../debugger/debug-interface-access/cv-hreg-e.md)