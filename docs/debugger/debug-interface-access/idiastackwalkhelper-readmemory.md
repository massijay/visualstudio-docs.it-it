---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::readMemory (metodo)"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legge un blocco di dati nell'immagine eseguibile in memoria.  
  
## Sintassi  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### Parametri  
 `type`  
 \[in\]  un valore dal [Enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) enumerazione che specifica il tipo di memoria per leggere.  
  
 va  
 \[in\]  Indirizzo virtuale nell'immagine da cui iniziare la lettura.  
  
 `cbData`  
 \[in\]  La dimensione del buffer di dati in byte.  
  
 `pcbData`  
 \[out\]  Restituisce il numero di byte letti effettivamente da.  se `pbData` viene  `NULL`, questo è il numero totale di byte dei dati disponibili.  
  
 `pbData`  
 \[in, out\]  Un buffer che viene riempito di memoria visualizzata.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumerazione MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)