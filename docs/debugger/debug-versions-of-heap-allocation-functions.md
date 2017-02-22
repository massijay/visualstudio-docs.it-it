---
title: "Versioni di debug di funzioni di allocazione heap | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.crt"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC (macro)"
  - "_malloc_dbg (funzione)"
  - "debug [CRT], funzioni di allocazione heap"
  - "debug dei problemi di memoria, funzioni della libreria di debug CRT"
  - "allocazione di heap, debug"
  - "malloc (funzione)"
  - "perdite di memoria, funzioni della libreria di debug CRT"
ms.assetid: 91748bdc-f4cd-4d8b-ab98-0493dab7ed0d
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Versioni di debug di funzioni di allocazione heap
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La libreria di runtime del linguaggio C contiene speciali versioni di debug delle funzioni di allocazione heap.  Queste funzioni presentano lo stesso nome delle corrispondenti versioni di rilascio, con l'unica differenza del suffisso \_dbg.  Questo argomento illustra le differenze tra la versione di rilascio di una funzione CRT e la versione \_dbg, utilizzando `malloc` e `_malloc_dbg` come esempi.  
  
 Quando viene definito [\_DEBUG](/visual-cpp/c-runtime-library/debug), CRT associa tutte le chiamate a [malloc](/visual-cpp/c-runtime-library/reference/malloc) a [\_malloc\_dbg](/visual-cpp/c-runtime-library/reference/malloc-dbg).  Pertanto non è necessario riscrivere il codice utilizzando `_malloc_dbg` anziché `malloc` per sfruttarne i vantaggi durante il debug.  
  
 È tuttavia possibile chiamare `_malloc_dbg` esplicitamente.  La chiamata esplicita di `_malloc_dbg` presenta alcuni vantaggi supplementari:  
  
-   Registrazione delle allocazioni del tipo `_CLIENT_BLOCK`.  
  
-   Memorizzazione del file sorgente e del numero di riga nel punto in cui ha avuto luogo la richiesta di allocazione.  
  
 Se non si desidera convertire le chiamate a `malloc` in chiamate a `_malloc_dbg`, è possibile ottenere le informazioni sul file di origine definendo [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc). In questo modo, il preprocessore associa direttamente tutte le chiamate a `malloc` alle chiamate a `_malloc_dbg` anziché basarsi su un wrapper di `malloc`.  
  
 Per registrare i tipi separati di allocazioni in blocchi client, è necessario chiamare `_malloc_dbg` direttamente e impostare il parametro `blockType` su `_CLIENT_BLOCK`.  
  
 Quando \_DEBUG non viene definito, le chiamate a `malloc` non vengono disturbate, le chiamate a `_malloc_dbg` vengono risolte in `malloc`, la definizione di [\_CRTDBG\_MAP\_ALLOC](/visual-cpp/c-runtime-library/crtdbg-map-alloc) viene ignorata e non vengono fornite le informazioni sul file di origine relative alla richiesta di allocazione.  Dal momento che `malloc` non presenta alcun parametro del tipo di blocco, le richieste di tipi `_CLIENT_BLOCK` vengono gestite come allocazioni standard.  
  
## Vedere anche  
 [Tecniche di debug CRT](../debugger/crt-debugging-techniques.md)