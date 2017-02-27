---
title: "IDiaAddressMap::get_addressMapEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::get_addressMapEnabled (metodo)"
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

indica se un mapping di indirizzo è stato stabilito per una sessione particolare.  
  
## Sintassi  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### Parametri  
 pRetVal  
 \[out\]  Restituisce `TRUE` se la riproduzione d'indirizzi è abilitata.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 I postprocessori eseguibili talvolta aggiornano l'eseguibile.  Il diametro contiene un meccanismo per supportare la conversione dei simboli al nuovo layout.  
  
 Le applicazioni client possono impostare il mapping dell'indirizzo di una sessione particolare ottenendo [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) interfaccia da  [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaccia e chiamare  [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) metodo seguito da una chiamata a  [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metodo.  `get_addressMapEnabled` il metodo restituisce i risultati di chiamare  `put_addressMapEnabled` metodo.  
  
## Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)