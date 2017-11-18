---
title: 'Idiasymbol:: Get_platform | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79e2757ae76f7973def05a1f6468d919cc77347f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetplatform"></a>IDiaSymbol::get_platform
Recupera il tipo di piattaforma per cui è stato compilato il modulo.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce un valore di [CV_CPU_TYPE_e (enumerazione)](../../debugger/debug-interface-access/cv-cpu-type-e.md) il tipo di enumerazione che specifica la piattaforma per cui è stato compilato del modulo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CPU_TYPE_e (enumerazione)](../../debugger/debug-interface-access/cv-cpu-type-e.md)