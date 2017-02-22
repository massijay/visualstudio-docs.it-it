---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Prev (metodo)"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera i simboli precedenti nell'ordine in base all'indirizzo.  
  
## Sintassi  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  Il numero di simboli nell'enumeratore da recuperare.  
  
 rgelt  
 \[out\]  Una matrice cui è possibile riempito con [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetti che rappresentano i simboli desiderati.  
  
 pceltFetched  
 \[out\]  Restituisce il numero di simboli nell'enumeratore recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti simboli precedenti.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo aggiorna la posizione dell'enumeratore dal numero di elementi recuperati.  
  
## Vedere anche  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)