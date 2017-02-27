---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::put_registerValue (metodo)"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Imposta il valore di un registro.  
  
## Sintassi  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### Parametri  
 `index`  
 \[in\]  un valore dal [Enumerazione CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) enumerazione che specifica il log per scrivere.  
  
 `NewVal`  
 \[in\]  Il nuovo valore del registro.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Nonostante la dimensione del valore, l'implementazione deve archiviare solo gli elementi del log in genere utilizzato.  Ad esempio, un registro a 8 bit utilizzare solo i 8 bit meno significativi del valore specificato.  
  
## Vedere anche  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumerazione CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)