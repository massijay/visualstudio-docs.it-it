---
title: "IDiaEnumSymbols::Next | Microsoft Docs"
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
  - "IDiaEnumSymbols::Next (metodo)"
ms.assetid: bfe5fe27-6a84-4392-910f-e325146d7552
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un numero specificato di simboli nella sequenza di enumerazione.  
  
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
 \[out\]  Una matrice che deve essere compilata con [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetti che rappresentano i simboli desiderati.  
  
 pceltFetched  
 \[out\]  Restituisce il numero di simboli nell'enumeratore recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti più simboli.  In caso contrario, restituisce un codice di errore.  
  
## Esempio  
  
```cpp#  
IDiaEnumSymbols* pEnum  
CComPtr< IDiaSymbol> pSym;  
DWORD celt;  
pEnum->Next( 1, &pSym, &celt );  
```  
  
## Vedere anche  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)