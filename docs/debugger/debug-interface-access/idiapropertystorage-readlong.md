---
title: "IDiaPropertyStorage::ReadLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadLONG"
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

legge `LONG` valori in una raccolta di proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### Parametri  
 `id`  
 \[in\]  Identificatore della proprietà da leggere \(`PROPID` viene definito in WTypes.h ad esempio  `ULONG`\).  
  
 `pValue`  
 \[out\]  Restituisce il valore della proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Restituisce `E_INVALIDARG` se la proprietà non è di tipo  `LONG`.  
  
## Note  
 In `LONG` è definito da windows come signed integer a 32 bit.  
  
## Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)