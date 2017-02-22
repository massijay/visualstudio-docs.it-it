---
title: "IDiaSymbol::get_baseSymbolId | Microsoft Docs"
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
ms.assetid: cd504d2b-194f-4106-8de5-2de827a79cbd
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_baseSymbolId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il simbolo ID da cui il puntatore è basato.  
  
## Sintassi  
  
```cpp  
HRESULT get_baseSymbolId(   
   DWORD *pRetVal);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\] puntatore A `DWORD` che utilizza il simbolo ID da cui il puntatore è basato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)