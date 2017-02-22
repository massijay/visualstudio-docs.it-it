---
title: "IEnumDebugCodeContexts2::Next | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2::Next"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2::Next"
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il set di elementi dell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext2** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                 celt,  
   IDebugCodeContext2[] rgelt,  
   ref uint             pceltFetched  
);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Il numero di elementi da recuperare.  Specifica inoltre la dimensione massima della matrice di `rgelt` .  
  
 `rgelt`  
 \[in, out\]  Matrice [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) di elementi da riempire.  
  
 `pceltFetched`  
 \[out\]  Restituisce il numero di elementi effettivamente restituiti in `rgelt`.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`.  Restituisce `S_FALSE` se meno che il numero richiesto degli elementi possono essere restituiti, in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)