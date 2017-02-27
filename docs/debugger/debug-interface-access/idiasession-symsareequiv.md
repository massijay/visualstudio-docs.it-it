---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "IDiaSession::symsAreEquiv (metodo)"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verifica se due simboli sono equivalenti.  
  
## Sintassi  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### Parametri  
 `symbolA`  
 \[in\]  il primo [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto utilizzato nel confronto.  
  
 `symbolB`  
 \[in\]  il secondo `IDiaSymbol` oggetto utilizzato nel confronto.  
  
## Valore restituito  
 Se i simboli sono equivalenti, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE`, i simboli non sono equivalenti.  In caso contrario, restituire un codice di errore.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)