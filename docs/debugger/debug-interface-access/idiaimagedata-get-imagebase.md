---
title: "IDiaImageData::get_imageBase | Microsoft Docs"
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
  - "IDiaImageData::get_imageBase (metodo)"
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la posizione di memoria in cui l'immagine deve essere basata.  
  
## Sintassi  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce il valore finale di base dell'immagine.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 A causa dei conflitti di base dell'immagine, un'immagine può essere ribasata automaticamente a una posizione di memoria inutilizzata quando viene caricata.  Questo metodo restituisce il suggerimento di base \(posizione di memoria suggerita\) che sia stato memorizzato nel form in fase di compilazione.  
  
## Vedere anche  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)