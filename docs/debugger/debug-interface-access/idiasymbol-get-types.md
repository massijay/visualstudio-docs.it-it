---
title: "IDiaSymbol::get_types | Microsoft Docs"
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
  - "IDiaSymbol::get_types (metodo)"
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_types
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una matrice di tipi compilatore\-specifici per questo simbolo.  
  
## Sintassi  
  
```cpp#  
HRESULT get_types (   
   DWORD       cTypes,  
   DWORD*      pcTypes,  
   IDiaSymbol* types[]  
);  
```  
  
#### Parametri  
 `cTypes`  
 \[in\]  Dimensione del buffer per utilizzare i dati.  
  
 `pcTypes`  
 \[out\]  Restituisce il numero di tipi scritti, o, se `types` il parametro è  `NULL`, quindi il numero totale dei tipi disponibili.  
  
 `types[]`  
 \[out\]  Una matrice che deve essere compilata con [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetti che rappresentano tutti i tipi per questo simbolo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)