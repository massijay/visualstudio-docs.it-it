---
title: "IEnumDebugBoundBreakpoints2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugBoundBreakpoints2::Skip"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::Skip"
ms.assetid: 95659709-6d7c-44ca-b598-629eb688429f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugBoundBreakpoints2::Skip
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ignora il numero specificato di elementi.  
  
## Sintassi  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```c#  
int Skip(  
   uint celt  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Numero di elementi da ignorare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se `celt` è maggiore del numero di elementi rimanenti; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione viene impostata alla fine e `S_FALSE` viene restituito.  
  
## Vedere anche  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)