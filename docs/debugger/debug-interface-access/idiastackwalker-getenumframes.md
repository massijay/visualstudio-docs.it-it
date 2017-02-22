---
title: "IDiaStackWalker::getEnumFrames | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames (metodo)"
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker::getEnumFrames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un enumeratore dello stack frame per le piattaforme x86.  
  
## Sintassi  
  
```cpp#  
HRESULT getEnumFrames(   
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Parametri  
 `pHelper`  
 \[in\]  L'helper [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) oggetto.  
  
 `ppEnum`  
 \[out\]  restituisce [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) oggetto di cui è presente un elenco  [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) oggetti.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Per ottenere un elenco dello stack frame su qualsiasi altra piattaforma, chiamare [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) metodo.  
  
## Vedere anche  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)