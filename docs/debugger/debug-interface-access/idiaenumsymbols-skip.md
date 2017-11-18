---
title: IDiaEnumSymbols::Skip | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b7aa58a94b44270c89a1ea0ddcb380abd830b31
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Ignora un numero specificato di simboli in una sequenza di enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 celt  
 [in] Il numero di simboli nella sequenza di enumerazione da ignorare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` se sono non presenti ulteriori simboli da ignorare.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)