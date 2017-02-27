---
title: "IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_relativeVirtualAddressEnabled (metodo)"
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Consente al client viene abilitata o disabilitata nel calcolo e l'utilizzo degli indirizzi virtuali relativi \(RVA\).  
  
## Sintassi  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### Parametri  
 NewVal  
 \[in\]  Impostare su `TRUE` per abilitare, o  `FALSE` per disabilitare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Gli indirizzi per gli oggetti di debug descritti da interfacce di diametro e alla base dell'immagine eseguibile, possono essere recuperati come indirizzi virtuali relativi.  
  
 L'utilizzo di Non è abilitato quando i segmenti inizialmente sono caricati da un file PDB.  Per ottenere lo stato corrente dell'utilizzo degli indirizzi, chiamare [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) metodo.  
  
 `put_relativeVirtualAddress` il metodo deve essere chiamato per abilitare gli indirizzi dopo una corrispondenza chiamata a  [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) il metodo ha stabilito nuove intestazioni di immagine.  
  
## Vedere anche  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)