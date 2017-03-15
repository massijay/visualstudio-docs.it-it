---
title: "IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs"
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce un'enumerazione di simboli per i frame inline che corrispondono alla posizione di origine specificata.  
  
## Sintassi  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parametri  
 `parent`  
 \[in\] `IDiaSymbol` che corrisponde alla funzione di uno stub di scelta rapida che deve essere presente.  
  
 `file`  
 \[in\] `IDiaSourceFile` la posizione di origine.  
  
 `linenum`  
 \[in\] numero di riga della posizione di origine.  
  
 `colnum`  
 \[in\] numero di colonne della posizione di origine.  
  
 `ppResult`  
 \[out\] puntatore A un puntatore a interfaccia `IDiaEnumLineNumbers` inizializzato con il risultato.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)