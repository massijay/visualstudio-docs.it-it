---
title: "IDiaEnumSymbolsByAddr::Next | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::Next (metodo)"
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera i simboli seguenti nell'ordine in base all'indirizzo.  
  
## Sintassi  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  Il numero di simboli nell'enumeratore da recuperare.  
  
 rgelt  
 \[out\]  Una matrice che deve essere compilata con [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta i simboli desiderati.  
  
 pceltFetched  
 \[out\]  Restituisce il numero di simboli nell'enumeratore recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti più simboli.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo aggiorna la posizione dell'enumeratore dal numero di elementi recuperati.  
  
## Vedere anche  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)