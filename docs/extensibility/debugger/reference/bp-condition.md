---
title: "BP_CONDITION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_CONDITION"
helpviewer_keywords: 
  - "Struttura BP_CONDITION"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vengono descritte le condizioni in cui un punto di interruzione viene generato.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## Membri  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) l'oggetto che rappresenta il thread attivo per l'applicazione che contiene il punto di interruzione.  
  
 `styleCondition`  
 Un valore [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) dell'enumerazione che descrive lo stile di questa condizione del punto di interruzione.  
  
 `bstrContext`  
 La posizione del punto di interruzione.  
  
 `bstrCondition`  
 Lo stato di infornamento del punto di interruzione.  
  
 `nRadix`  
 Base da utilizzare nella valutazione delle informazioni numerica.  
  
## Note  
 Questa struttura è un membro [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
 Questa struttura passata come parametro [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) ai metodi [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) e.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)