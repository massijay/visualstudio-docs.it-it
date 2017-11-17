---
title: 'Idiaaddressmap:: Put_imagealign | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38856520641ff2ea191e3f712a1f355e841e1aff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
Imposta l'allineamento dell'immagine.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 NewVal  
 [in] Nuovo valore di allineamento immagine per il file eseguibile.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Immagini, caricare file eseguibili, vengono allineate ai limiti di memoria specificata. L'allineamento in quanto può essere influenzata dall'architettura di sistema corrente e da opzioni della fase di compilazione e collegamento. L'allineamento dell'immagine è sempre nei limiti di byte. I valori di allineamento immagine seguente sono validi: i limiti di 1, 2, 4, 8, 16, 32 e 64 byte.  
  
 L'allineamento dell'immagine corrente può essere recuperato con una chiamata al [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) metodo.  
  
> [!NOTE]
>  L'immagine è già caricato nel momento in cui che questo metodo può essere chiamato. Il `put_imageAlign` metodo viene in genere utilizzato quando l'immagine è stato spostato o modificato e un nuovo allineamento è obbligatorio.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)