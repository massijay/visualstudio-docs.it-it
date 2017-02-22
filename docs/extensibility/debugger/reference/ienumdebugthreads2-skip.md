---
title: "IEnumDebugThreads2::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2::Skip"
helpviewer_keywords: 
  - "IEnumDebugThreads2::Skip"
ms.assetid: eab068d4-1f8d-44cd-bc54-92a10fe23de6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugThreads2::Skip
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
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)