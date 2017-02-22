---
title: "IDiaSymbol::get_hasAlloca | Microsoft Docs"
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
  - "IDiaSymbol::get_hasAlloca (metodo)"
ms.assetid: 3b9fb747-670b-4da7-bb70-612f7b911786
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_hasAlloca
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un flag che indica a se la funzione contiene una chiamata `alloca` \(utilizzato per allocare memoria nello stack\).  
  
## Sintassi  
  
```  
[C++]HRESULT get_hasAlloca(   BOOL *pFlag);  
```  
  
#### Parametri  
 `pFlag`  
 \[out\]  Restituisce `TRUE` se la funzione contiene una chiamata a  `alloca`; in caso contrario, restituisce  `FALSE`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Requisiti  
  
|Requisiti|Descrizione|  
|---------------|-----------------|  
|intestazione:|dia2.h|  
|versione:|DIA SDK v8.0|  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)