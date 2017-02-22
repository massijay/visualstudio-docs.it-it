---
title: "IEnumDebugBoundBreakpoints2::GetCount | Microsoft Docs"
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
  - "IEnumDebugBoundBreakpoints2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugBoundBreakpoints2::GetCount"
ms.assetid: 5a572eeb-beb7-4fc7-8259-792d277069be
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugBoundBreakpoints2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce il numero di elementi nell'enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### Parametri  
 `pcelt`  
 \[out\]  Restituisce il numero di elementi nell'enumerazione.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo non fa parte dell'interfaccia solito di enumerazione COM che specifica che solo `Next`, `Clone`, `Skip`e i metodi di `Reset` devono essere distribuiti.  
  
## Vedere anche  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)