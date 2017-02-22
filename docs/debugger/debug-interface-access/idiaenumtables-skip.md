---
title: "IDiaEnumTables::Skip | Microsoft Docs"
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
  - "IDiaEnumTables::Skip (metodo)"
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignora un numero specificato delle tabelle in una sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Il numero delle tabelle nella sequenza di enumerazione da ignorare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` se non sono presenti più tabelle da ignorare.  
  
## Vedere anche  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)