---
title: IDiaSymbol::get_acceleratorPointerTags | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8467c25c8665dfb3fc91ea29d9b99c184b7ecce
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Restituisce tutti i valori tag puntatore tasti di scelta rapida che corrispondono a una funzione di stub di C++ AMP tasti di scelta rapida.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cnt`  
 [in] Le dimensioni della matrice di output `pPointerTags`.  
  
 `pcnt`  
 [out] Il numero di tag di puntatore tasti di scelta rapida nella funzione stub C++ AMP tasti di scelta rapida.  
  
 `pPointerTags`  
 [out] Oggetto `DWORD` puntatore alla matrice che viene riempito con i valori di tag puntatore tasti di scelta rapida nella funzione stub C++ AMP tasti di scelta rapida.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo viene chiamato su un `IDiaSymbol` interfaccia che corrisponde a una funzione di stub di C++ AMP tasti di scelta rapida.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)