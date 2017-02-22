---
title: "IDebugBreakpointEvent2::EnumBreakpoints | Microsoft Docs"
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
  - "IDebugBreakpointEvent2:::EnumBreakpoints"
helpviewer_keywords: 
  - "IDebugBreakpointEvent2:::EnumBreakpoints"
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointEvent2::EnumBreakpoints
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per tutti i punti di interruzione che hanno effettuato lo stato attivo sulla posizione corrente di codice.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumBreakpoints(  
  IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```c#  
int EnumBreakpoints(  
  out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### Parametri  
 `ppEnum`  
 \[out\]  Restituisce [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) un oggetto che enumera i punti di interruzione associati alla posizione corrente di codice.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Non tutti i punti di interruzione in una determinata posizione è possibile distribuire in un determinato momento, ad esempio un punto di interruzione con una condizione non genererà fino a riempire la condizione\).  
  
## Vedere anche  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)