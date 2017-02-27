---
title: "IDiaSymbol::findChildrenExByVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByVA"
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera gli elementi figlio del simbolo che sono validi a un indirizzo virtuale specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parametri  
 `symtag`  
 \[in\]  Specifica i tag dei simboli degli elementi figlio da recuperare, come definito in [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md).  Impostare su `SymTagNull` per tutti gli elementi figlio vengano recuperati.  
  
 `name`  
 \[in\]  Specifica il nome degli elementi figlio da recuperare.  Impostare su `NULL` per tutti gli elementi figlio vengano recuperati.  
  
 `compareFlags`  
 \[in\]  Specifica le opzioni di confronto applicare per assegnare un nome alla corrispondenza.  Valori da [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) l'enumerazione può essere utilizzata da solo o nell'associazione.  
  
 `address`  
 \[in\]  Specificare l'indirizzo virtuale.  
  
 `ppResult`  
 \[out\]  restituisce [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) oggetto contenente un elenco dei simboli figlio recuperati.  
  
## Valore restituito  
 Restituisce `S_OK` se almeno un elemento figlio del simbolo è stato trovato, o restituisce  `S_FALSE` se nessun figlio è stato trovato, in caso contrario, restituisce un codice di errore.  
  
## Note  
 I simboli locali restituiti sono inclusi le informazioni nell'intervallo.  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumerazione NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)