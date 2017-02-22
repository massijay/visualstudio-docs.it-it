---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

legge `DWORD` valori in una raccolta di proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### Parametri  
 `id`  
 \[in\]  Identificatore della proprietà da leggere \(`PROPID` viene definito in WTypes.h ad esempio  `ULONG`\).  
  
 `pValue`  
 \[out\]  Restituisce il valore della proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  Restituisce `E_INVALIDARG` se la proprietà non è di tipo  `DWORD`.  
  
## Note  
 In `DWORD` è definito da windows come Unsigned Integer a 32 bit.  
  
## Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)