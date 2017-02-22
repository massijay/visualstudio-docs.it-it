---
title: "IDiaSymbol::get_arrayIndexType | Microsoft Docs"
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
  - "IDiaSymbol::get_arrayIndexType (metodo)"
ms.assetid: cd63b9ec-9694-406c-b37f-bde6bd5fcbf2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_arrayIndexType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera l'interfaccia del simbolo del tipo di indice della matrice dei simboli.  
  
## Sintassi  
  
```cpp#  
HRESULT get_arrayIndexType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il tipo di indice della matrice dei simboli.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Note  
 Alcuni linguaggi possono specificare il tipo utilizzato come indice in una matrice.  Il simbolo restituito da questo metodo specifica il tipo.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v7.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)