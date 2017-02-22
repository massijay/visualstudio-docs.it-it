---
title: "IDiaEnumSegments::Clone | Microsoft Docs"
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
  - "IDiaEnumSegments::Clone (metodo)"
ms.assetid: 93deaac6-72ab-4408-ba14-66174a618757
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.  
  
## Sintassi  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSegments** ppenum  
);  
```  
  
#### Parametri  
 ppenum  
 \[out\]  restituisce [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md) oggetto che contiene un duplicato dell'enumeratore.  I segmenti non siano duplicati, solo enumeratore.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)