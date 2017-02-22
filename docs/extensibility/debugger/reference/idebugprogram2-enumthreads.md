---
title: "IDebugProgram2::EnumThreads | Microsoft Docs"
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
  - "IDebugProgram2::EnumThreads"
helpviewer_keywords: 
  - "IDebugProgram2::EnumThreads"
ms.assetid: 0f2a8c51-1315-4c96-8aa1-6a937dc2a769
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumThreads
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco di thread in esecuzione nel programma.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumThreads(   
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int EnumThreads(   
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) un oggetto che contiene un elenco di thread.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)