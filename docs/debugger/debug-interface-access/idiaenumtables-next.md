---
title: "IDiaEnumTables::Next | Microsoft Docs"
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
  - "IDiaEnumTables::Next (metodo)"
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un numero specificato delle tabelle nella sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Il numero di tabelle nell'enumeratore da recuperare.  
  
 `rgelt`  
 \[out\]  Una matrice che deve essere compilata con [IDiaTable](../../debugger/debug-interface-access/idiatable.md) oggetti che rappresentano le tabelle desiderate.  
  
 `pceltFetched`  
 \[out\]  Restituisce il numero di tabelle nell'enumeratore recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se non sono presenti più tabelle.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)