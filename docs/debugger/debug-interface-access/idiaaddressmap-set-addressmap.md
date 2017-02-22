---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "IDiaAddressMap::set_addressMap (metodo)"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fornisce un mapping di indirizzo le conversioni del layout dell'immagine di supporto.  
  
## Sintassi  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### Parametri  
 `cbData`  
 \[in\]  Il numero di elementi in `data` parametro.  
  
 `data[]`  
 \[in\]  una matrice di [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) strutture che definiscono il mapping della conversione.  
  
 `imagetoSymbols`  
 \[in\]  `TRUE` se  `data` il parametro corrisponde a un mapping tra il nuovo layout di immagine al layout originale \(come descritto dai simboli di debug.  `FALSE` se  `data` è un mapping al nuovo layout dell'immagine ricavato dal layout originale.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 In genere, il diametro recupera i mapping di conversione di indirizzo dal file di database di programma \(PDB\).  Se questi valori sono mancanti, [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) il metodo viene chiamato due volte, una volta con  `imagetoSymbols` parametro impostato su  `TRUE` e una volta con  `imagetoSymbols` parametro impostato su  `FALSE`.  Le conversioni di mapping di indirizzo non possono essere abilitate tramite [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) metodo a meno che entrambi i mapping di conversione forniti.  
  
## Vedere anche  
 [Struttura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)