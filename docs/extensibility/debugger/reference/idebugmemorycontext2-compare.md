---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
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
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "Metodo IDebugMemoryContext2::Compare"
  - "Compare (metodo)"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Confronta il contesto di memoria per ogni contesto nella matrice specificata nel modo indicato dal confronto tra i flag, restituire un indice del primo contesto che corrisponde a.  
  
## Sintassi  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### Parametri  
 `compare`  
 \[in\]  Un valore [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md) dell'enumerazione che determina il tipo di confronto.  
  
 `rgpMemoryContextSet`  
 \[in\]  Le matrici di riferimenti [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) a oggetti da eseguire su.  
  
 `dwMemoryContextSetLen`  
 \[in\]  Il numero dei contesti nella matrice di `rgpMemoryContextSet` .  
  
 `pdwMemoryContext`  
 \[out\]  Restituisce l'indice del primo contesto di memoria che soddisfa il confronto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  restituisce `E_COMPARE_CANNOT_COMPARE` se i due contesti non possono essere confrontati.  
  
## Note  
 Il modulo \(DE\) di debug non deve supportare tutti i tipi di confronto, ma deve supportare almeno `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE`.  
  
## Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)