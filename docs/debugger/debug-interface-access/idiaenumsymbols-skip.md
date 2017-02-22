---
title: "IDiaEnumSymbols::Skip | Microsoft Docs"
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
  - "IDiaEnumSymbols::Skip (metodo)"
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ignora un numero specificato dei simboli in una sequenza di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### Parametri  
 celta  
 \[in\]  Il numero di simboli nella sequenza di enumerazione da ignorare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce  `S_FALSE` se non sono presenti più simboli da ignorare.  
  
## Vedere anche  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)