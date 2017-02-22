---
title: "IDiaEnumSectionContribs::Next | Microsoft Docs"
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
  - "IDiaEnumSectionContribs::Next (metodo)"
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un numero specificato di contributi la sezione della sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  Il numero dei contributi della sezione nell'enumeratore da recuperare.  
  
 rgelt  
 \[out\]  Una matrice che deve essere compilata con [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) oggetti che rappresentano i contributi desiderati della sezione.  
  
 pceltFetched  
 \[out\]  Restituisce il numero dei contributi della sezione nell'enumeratore recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti più contributi della sezione.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)