---
title: "IDebugReference2::GetSize | Microsoft Docs"
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
  - "IDebugReference2::GetSize"
helpviewer_keywords: 
  - "IDebugReference2::GetSize"
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene la dimensione, in byte, del valore del riferimento.  Riservato per un utilizzo futuro.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### Parametri  
 `pdwSize`  
 \[out\]  Restituisce la dimensione, in byte, del valore del riferimento.  
  
## Valore restituito  
 Restituisce sempre `E_NOTIMPL`.  
  
## Vedere anche  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)