---
title: "IDebugReturnValueEvent2::GetReturnValue | Microsoft Docs"
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
  - "IDebugReturnValueEvent2::GetReturnValue"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2::GetReturnValue"
ms.assetid: 86c50d5a-6df6-4798-818a-c587a8741f90
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReturnValueEvent2::GetReturnValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il valore restituito o l'esecuzione di istruzioni da o su una funzione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetReturnValue (   
   IDebugProperty2** ppReturnValue  
);  
```  
  
```c#  
int GetReturnValue (   
   out IDebugProperty2 ppReturnValue  
);  
```  
  
#### Parametri  
 `ppReturnValue`  
 \[out\]  restituisce [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) un oggetto che rappresenta il valore da recuperare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)