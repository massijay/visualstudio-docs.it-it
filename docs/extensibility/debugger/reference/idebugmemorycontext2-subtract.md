---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
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
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "Subtract (metodo)"
  - "Metodo IDebugMemoryContext2::Subtract"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sottrae il valore specificato dal contesto corrente e restituisce un nuovo contesto.  
  
## Sintassi  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parametri  
 `dwCount`  
 \[in\]  Il numero di byte di memoria a incremento.  
  
 `ppMemCxt`  
 \[out\]  restituisce un nuovo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un contesto di memoria è un indirizzo, in modo da ridurre un valore da un indirizzo produce un nuovo indirizzo che richiede una nuova interfaccia di contesto.  
  
 Questo metodo deve produrre sempre un nuovo contesto, anche se l'indirizzo risultante è esterna allo spazio di memoria associato al contesto.  L'unica eccezione è se memoria non può essere allocata per il nuovo contesto o se `ppMemCxt` è un valore null \(che è un errore\).  
  
## Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)