---
title: "IDebugReference2::GetMemoryContext | Microsoft Docs"
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
  - "IDebugReference2::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugReference2::GetMemoryContext"
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ottiene un contesto di memoria di un riferimento.  Riservato per un utilizzo futuro.  
  
## Sintassi  
  
```cpp#  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```c#  
int GetMemoryContext (   
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### Parametri  
 `ppMemory`  
 \[out\]  Restituisce [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) l'oggetto che rappresenta la memoria associata al valore del riferimento.  
  
## Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)