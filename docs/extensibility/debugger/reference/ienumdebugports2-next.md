---
title: "IEnumDebugPorts2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2::Next"
helpviewer_keywords: 
  - "IEnumDebugPorts2::Next"
ms.assetid: 3f43d18c-6bd1-4ddd-95ef-9550abd2ad09
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il set di elementi dell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugPort2** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint          celt,  
   IDebugPort2[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Il numero di elementi da recuperare.  Specifica inoltre la dimensione massima della matrice di `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matrice [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) di elementi da riempire.  
  
 `pceltFetched`  
 \[out\]  Restituisce il numero di elementi effettivamente restituiti in `rgelt`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se meno che il numero richiesto degli elementi possono essere restituiti, in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)