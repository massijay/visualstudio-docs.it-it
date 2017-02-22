---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap::set_imageHeaders (metodo)"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta le intestazioni di immagini per abilitare la conversione di indirizzo virtuale relativa.  
  
## Sintassi  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### Parametri  
 cbData  
 \[in\]  Numero di byte dei dati dell'intestazione.  deve essere `n*sizeof(IMAGE_SECTION_HEADER)` dove  `n` è il numero di test della sezione nell'eseguibile.  
  
 dati \[\]  
 \[in\]  una matrice di  `IMAGE_SECTION_HEADER` strutture da utilizzare come le intestazioni di immagine.  
  
 originalHeaders  
 \[in\]  Impostare su `FALSE` se le intestazioni di immagine sono contenute nella nuova immagine,  `TRUE` se riflettono l'immagine originale prima di un aggiornamento.  In genere, è impostato su `TRUE` solo in combinazione con le chiamate a  [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 `IMAGE_SECTION_HEADER` strutturare viene dichiarato in Winnt.h e rappresenta il formato di verificata la sezione di immagine eseguibile.  
  
 I calcoli di indirizzi virtuali relativi dipendono da `IMAGE_SECTION_HEADER` valori.  In genere, il diametro recupera tali dal file di database di programma \(PDB\).  Se questi valori non sono disponibili, il diametro non potrà calcolare gli indirizzi virtuali relativi \(RVA e [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) il metodo restituisce  `FALSE`.  Il client deve chiamare [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) metodo per abilitare i calcoli di indirizzi virtuali relativi dopo aver fornito le intestazioni mancanti nell'immagine stessa immagine.  
  
## Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)