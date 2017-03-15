---
title: "IDiaAddressMap::put_addressMapEnabled | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap::put_addressMapEnabled (metodo)"
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica se il mapping di indirizzo deve essere utilizzato per convertire gli indirizzi del simbolo.  
  
## Sintassi  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### Parametri  
 NewVal  
 \[in\]  Impostare su `TRUE` per abilitare la conversione dei simboli, o  `FALSE` per disabilitare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 I postprocessori eseguibili talvolta aggiornano l'eseguibile.  Il diametro contiene un meccanismo per supportare la conversione dei simboli al nuovo layout.  
  
 Quando un file PDB viene caricato, il mapping di indirizzo archiviato nel file è abilitato.  In alcuni casi, tuttavia, quando un'applicazione client può essere necessario fornire il proprio mapping di indirizzi chiamando [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo.  se `set_addressMap` il metodo ha esito positivo, l'applicazione client deve chiamare  `put_addressMapEnabled` metodo con  `NewVal` parametro di  `TRUE` per consentire l'utilizzo di tale mapping di indirizzo.  
  
 Lo stato corrente del mapping di indirizzo abilitato può essere recuperato tramite una chiamata a [IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) metodo.  
  
## Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)