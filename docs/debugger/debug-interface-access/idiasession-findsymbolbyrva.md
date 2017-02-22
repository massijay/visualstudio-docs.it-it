---
title: "IDiaSession::findSymbolByRVA | Microsoft Docs"
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
  - "IDiaSession::findSymbolByRVA (metodo)"
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un tipo specificato di simboli che contiene, o è il più vicino a, un indirizzo virtuale relativo specificato \(RVA\).  
  
## Sintassi  
  
```cpp#  
HRESULT findSymbolByRVA (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parametri  
 `rva`  
 \[in\]  Specifica il gli indirizzi RVA.  
  
 `symtag`  
 \[in\]  Tipo di simboli da cercare.  I valori vengono ricavati da [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumerazione.  
  
 `ppSymbol`  
 \[out\]  restituisce [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che rappresenta il simbolo recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );  
```  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)