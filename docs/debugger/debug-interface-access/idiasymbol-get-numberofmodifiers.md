---
title: "IDiaSymbol::get_numberOfModifiers | Microsoft Docs"
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
ms.assetid: 61ff7431-1994-4f7e-a182-1817f16f60a9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_numberOfModifiers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il numero dei modificatori che si applicano al tipo originale.  
  
## Sintassi  
  
```cpp  
HRESULT get_numberOfModifiers(   
   DWORD* pRetVal);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\] puntatore A `DWORD` che specifica il numero dei modificatori che si applicano al tipo originale.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)