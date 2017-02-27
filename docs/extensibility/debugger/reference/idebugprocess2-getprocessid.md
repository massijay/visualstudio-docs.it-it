---
title: "IDebugProcess2::GetProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetProcessId"
helpviewer_keywords: 
  - "IDebugProcess2::GetProcessId"
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il GUID di questo processo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```c#  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### Parametri  
 `pguidProcessId`  
 \[out\]  restituisce il GUID per questo processo.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Identificatore univoco globale \(GUID\) identifica questo processo da tutti gli altri processi in esecuzione nel sistema.  
  
## Vedere anche  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)