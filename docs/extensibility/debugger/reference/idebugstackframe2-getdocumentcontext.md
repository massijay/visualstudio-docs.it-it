---
title: "IDebugStackFrame2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDocumentContext"
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il contesto del documento per questo stack frame.  
  
## Sintassi  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### Parametri  
 `ppCxt`  
 \[out\]  Restituisce [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) un oggetto che rappresenta la posizione corrente in un documento di origine.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo è più veloce rispetto a chiamando [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) il metodo e quindi di chiamando [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) il metodo sul contesto di codice.  Tuttavia, non è garantito che ogni modulo \(DE\) di debug implementerà questo metodo.  
  
## Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)