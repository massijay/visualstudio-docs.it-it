---
title: "IDiaSymbol::get_isSingleInheritance | Microsoft Docs"
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
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isSingleInheritance
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica se i punti del puntatore `this` a un membro dati con ereditarietà singola.  
  
## Sintassi  
  
```cpp  
HRESULT get_isSingleInheritance(   
   BOOL* pRetVal);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\] puntatore A `BOOL` che specifica se il puntatore `this` indica un membro dati con ereditarietà singola.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
## Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)