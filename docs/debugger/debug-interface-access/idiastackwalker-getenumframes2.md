---
title: "IDiaStackWalker::getEnumFrames2 | Microsoft Docs"
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
  - "IDiaStackWalker2::getEnumFrames2 (metodo)"
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un enumeratore dello stack frame per un tipo di piattaforma specifico.  
  
## Sintassi  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Parametri  
 `cpuid`  
 \[in\]  un valore dal [Enumerazione CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumerazione, specificando il tipo di piattaforma.  
  
 `pHelper`  
 \[in\]  L'helper [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) oggetto.  
  
 `ppEnum`  
 \[out\]  restituisce [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) oggetto che contiene un elenco di  [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) oggetti.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Per ottenere un elenco dello stack frame per la piattaforma x86, chiamare [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) metodo.  
  
## Vedere anche  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Enumerazione CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)