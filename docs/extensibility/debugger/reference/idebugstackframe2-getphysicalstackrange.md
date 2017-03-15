---
title: "IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetPhysicalStackRange"
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetPhysicalStackRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene una rappresentazione computer\-dipendente l'intervallo di indirizzi virtuali associata a uno stack frame.  
  
## Sintassi  
  
```cpp#  
HRESULT GetPhysicalStackRange (   
   UINT64* paddrMin,  
   UINT64* paddrMax  
);  
```  
  
```c#  
int GetPhysicalStackRange (   
   out ulong paddrMin,  
   out ulong paddrMax  
);  
```  
  
#### Parametri  
 `paddrMin`  
 \[out\]  Restituisce l'indirizzo fisico più basso associato a questo stack frame.  
  
 `paddrMax`  
 \[out\]  Restituisce l'indirizzo fisico più elevato associato a questo stack frame.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Le informazioni restituite con questo metodo vengono utilizzate dall'amministratore di debug della sessione \(SDM\) per ordinare gli stack frame.  
  
 Si presuppone che lo stack di chiamate aumentano verso il basso, ovvero, che i nuovi stack frame vengono aggiunti agli indirizzi di memoria sempre più inferiori.  L'architettura di runtime deve fornire gli intervalli fisici dello stack che corrispondono a questa ipotesi.  
  
## Vedere anche  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)