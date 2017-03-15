---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::get_registerValue (metodo)"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaStackWalkHelper::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera il valore di un registro.  
  
## Sintassi  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Parametri  
 `index`  
 \[in\]  un valore dal [Enumerazione CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) specificare di enumerazione da cui registrazione per ottenere il valore.  
  
 `pRetVal`  
 \[out\]  Restituisce il valore corrente del registro.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Nonostante la dimensione di `pRetVal` il parametro, l'implementazione deve archiviare solo gli elementi del log in genere utilizzato.  Ad esempio, un registro a 8 bit utilizza solo i 8 bit meno significativi del valore specificato.  Questo valore a 8 bit viene espanso a 64 bit una volta restituito da questo metodo.  
  
## Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumerazione CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)