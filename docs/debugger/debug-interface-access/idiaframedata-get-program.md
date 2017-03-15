---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "IDiaFrameData::get_program (metodo)"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recuperare la stringa del programma utilizzata per calcolare il set di log prima della chiamata alla funzione corrente.  
  
## Sintassi  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce la stringa del programma.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se questa proprietà non è supportata.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 La stringa del programma è una sequenza di macro che viene interpretata per stabilire il prologo.  Ad esempio, uno stack frame tipico può utilizzare la stringa del programma `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`.  Il formato di notazione polacca inversa, in cui gli operatori seguono gli operandi.  `T0` rappresenta una variabile temporanea nello stack.  In questo esempio vengono eseguiti i passaggi seguenti:  
  
1.  Contenuto in movimento del log `ebp` in  `T0`.  
  
2.  aggiungere `4` il valore in  `T0` per produrre un indirizzo, ottenere il valore dall'indirizzo e archiviare il valore nel registro  `eip`.  
  
3.  Ottenere il valore dall'indirizzo archiviato in `T0` e archivio che i valori nel registro  `ebp`.  
  
4.  aggiungere `8` il valore in  `T0` e archivio che i valori nel registro  `esp`.  
  
 Si noti che la stringa del programma è specifica della CPU e impostazione della convenzione di chiamata per la funzione rappresentata dallo stack frame corrente.  
  
## Vedere anche  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)