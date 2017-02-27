---
title: "IDiaSymbol::get_language | Microsoft Docs"
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
  - "IDiaSymbol::get_language (metodo)"
ms.assetid: c759ad3c-1c21-4234-869b-86aa3a608a38
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_language
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il linguaggio del database di origine.  
  
## Sintassi  
  
```cpp#  
HRESULT get_language (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce un valore dal [Enumerazione CV\_CFL\_LANG](../../debugger/debug-interface-access/cv-cfl-lang.md) enumerazione che specifica il linguaggio del database di origine.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` o codice di errore.  
  
> [!NOTE]
>  un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione CV\_CFL\_LANG](../../debugger/debug-interface-access/cv-cfl-lang.md)