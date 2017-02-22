---
title: "IDiaStackFrame::get_size | Microsoft Docs"
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
  - "IDiaStackFrame::get_size (metodo)"
ms.assetid: 71e2f5ab-4aa8-4922-aa8a-b7db97ee143c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_size
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la dimensione dello stack frame in byte.  
  
## Sintassi  
  
```cpp#  
HRESULT get_size (   
   DWORD* pRetVal  
);  
```  
  
#### Parametri  
 `pRetVal`  
 \[out\]  Restituisce la dimensione dello stack frame in byte.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se la proprietà non è supportata.  In caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)