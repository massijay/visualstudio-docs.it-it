---
title: "IDiaPropertyStorage::Enum | Microsoft Docs"
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
  - "IDiaPropertyStorage::Enum"
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::Enum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ottiene un enumeratore per le proprietà all'interno di questo set.  
  
## Sintassi  
  
```cpp#  
HRESULT Enum (   
   IEnumSTATPROPSTG** ppenum  
);  
```  
  
#### Parametri  
 `ppenum`  
 \[out\]  restituisce `IEnumSTATPROPSTG` oggetto \(nello spazio dei nomi Microsoft.VisualStudio.OLE.Interop\) che rappresenta un'enumerazione delle proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)