---
title: "IEnumCodePaths2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Next"
helpviewer_keywords: 
  - "IEnumCodePaths2::Next"
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumCodePaths2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il set di elementi dell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Il numero di elementi da recuperare.  Specifica inoltre la dimensione massima della matrice di `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matrice [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) di elementi da riempire.  
  
 `pceltFetched`  
 \[out\]  Restituisce il numero di elementi effettivamente restituiti in `rgelt`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se meno che il numero richiesto degli elementi possono essere restituiti, in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)