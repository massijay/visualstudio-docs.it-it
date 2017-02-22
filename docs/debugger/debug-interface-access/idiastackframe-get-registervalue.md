---
title: "IDiaStackFrame::get_registerValue | Microsoft Docs"
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
  - "IDiaStackFrame::get_registerValue (metodo)"
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il valore di un registro specificato come archiviato nello stack frame.  
  
## Sintassi  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### Parametri  
 `registerIndex`  
 \[in\]  Uno di [Enumerazione CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) valori di enumerazione.  
  
 `pRetVal`  
 \[out\]  Valore archiviato nel log.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Vedere anche  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Enumerazione CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)