---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::pdataByVA (metodo)"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Restituisce il blocco di dati PDATA associato all'indirizzo virtuale.  
  
## Sintassi  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### Parametri  
 `va`  
 \[in\]  Specificare l'indirizzo virtuale dei dati per verificare.  
  
 `cbData`  
 \[in\]  La dimensione dei dati in byte da verificare.  
  
 `pcbData`  
 \[out\]  Restituisce la dimensione effettiva dei dati in byte che sono stati ottenuti.  
  
 `pbData`  
 \[in, out\]  Un buffer che vengono inseriti i dati richiesti.  Non può essere `NULL`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non esistono PDATA per l'indirizzo specificato.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Il PDATA \(la sezione denominata “pdata„\) di un modulo contiene informazioni sulla gestione delle eccezioni per le funzioni.  
  
 Il chiamante conosce il numero di dati devono essere restituiti in modo che il chiamante non è necessario chiedere quantità di dati è disponibile.  Di conseguenza, per un'implementazione è accettabile di questo metodo restituirà un errore se `pbData` il parametro è  `NULL`.  
  
## Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)