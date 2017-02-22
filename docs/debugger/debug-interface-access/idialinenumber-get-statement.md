---
title: "IDiaLineNumber::get_statement | Microsoft Docs"
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
  - "IDiaLineNumber::get_statement (metodo)"
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber::get_statement
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un flag che indica che queste informazioni sulla riga descrivono l'inizio di un'istruzione, anziché un'espressione, nell'origine del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce `TRUE` se queste informazioni sulla riga descrivono l'inizio di un'istruzione nell'origine del programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se questa proprietà non è supportata.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Le istruzioni possono estendersi su più righe.  Questo metodo indica se il numero di riga associato contrassegna l'inizio di tale istruzione su più righe.  
  
## Vedere anche  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)