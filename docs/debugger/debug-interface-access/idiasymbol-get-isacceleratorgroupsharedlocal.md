---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53585bb1bd4b5185fa7ecc1dd998d48736d3b094
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa gruppo nel codice compilato per un tasto di scelta rapida di C++ AMP.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pFlag`  
 [out] Un puntatore a un `BOOL` che indica se il simbolo corrisponde a una variabile locale condivisa gruppo nel codice compilato per un tasto di scelta rapida di C++ AMP. Se `TRUE`, `get_baseDataSlot` e `get_baseDataOffset` metodi possono essere utilizzati per ottenere le informazioni sul percorso di archiviazione per la variabile.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)