---
title: "IDebugObject::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetMemoryContext"
helpviewer_keywords: 
  - "Metodo IDebugObject::GetMemoryContext"
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il contesto di memoria che rappresenta l'indirizzo del valore dell'oggetto.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```c#  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### Parametri  
 `pContext`  
 \[out\]  Restituisce [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) un oggetto che rappresenta l'indirizzo del valore dell'oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il contesto restituito di memoria specifica l'indirizzo del valore come rappresentato da questo [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) oggetto.  
  
## Vedere anche  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)