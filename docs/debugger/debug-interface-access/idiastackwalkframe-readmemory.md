---
title: "IDiaStackWalkFrame::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkFrame::readMemory (metodo)"
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legge la memoria nell'immagine.  
  
## Sintassi  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parametri  
 `type`  
 \[in\] uno dei valori di enumerazione di [Enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) che specifica il tipo di memoria accedere.  
  
 `va`  
 \[in\] posizione di indirizzo virtuale nell'immagine da avviare lettura.  
  
 `cbData`  
 \[in\] dimensione del buffer di dati, in byte.  
  
 `pcbData`  
 \[out\] restituisce il numero di byte restituiti.  Se `data` è `NULL`, quindi`pcbData` contiene il numero totale di byte dei dati disponibili.  
  
 `data`  
 \[out\] buffer di che devono essere inseriti i dati dalla posizione specificata.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)