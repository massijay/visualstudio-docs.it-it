---
title: "IDiaSegment::get_frame | Microsoft Docs"
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
  - "IDiaSegment::get_frame (metodo)"
ms.assetid: 9fece9c7-064a-4d6b-9cef-fc387f322205
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment::get_frame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera il numero di segmento.  
  
## Sintassi  
  
```cpp#  
HRESULT get_frame (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  restituisce il numero di segmento.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se questa proprietà non è supportata.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)