---
title: "IDiaPropertyStorage::ReadBOOL | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBOOL"
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

legge `BOOL` valori in una raccolta di proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### Parametri  
 `id`  
 \[in\]  Identificatore della proprietà da leggere \(`PROPID` viene definito in WTypes.h ad esempio  `ULONG`\).  
  
 `pValue`  
 \[out\]  Restituisce il valore della proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Restituisce `E_INVALIDARG` se la proprietà non è di tipo  `BOOL`.  
  
## Note  
 Per risultati coerenti, interpretare `BOOL` valore in modo che i valori diversi da zero siano  `TRUE` e zero è  `FALSE`.  
  
## Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)