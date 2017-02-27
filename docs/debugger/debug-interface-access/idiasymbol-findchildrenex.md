---
title: "IDiaSymbol::findChildrenEx | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenEx"
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::findChildrenEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera gli elementi figlio del simbolo.  I simboli locali restituiti sono inclusi le informazioni nell'intervallo, se il programma viene compilato con ottimizzazione su.  
  
## Sintassi  
  
```cpp#  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
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
  
 `ppResult`  
 \[out\]  restituisce [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) oggetto contenente un elenco dei simboli figlio recuperati.  
  
## Valore restituito  
 Restituisce `S_OK` se almeno un elemento figlio del simbolo è stato trovato, o restituisce  `S_FALSE` se nessun figlio è stato trovato, in caso contrario, restituisce un codice di errore.  
  
## Note  
 questo metodo è la versione estesa di [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).  
  
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