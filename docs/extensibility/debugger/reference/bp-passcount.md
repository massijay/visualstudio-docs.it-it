---
title: "BP_PASSCOUNT | Microsoft Docs"
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
  - "BP_PASSCOUNT"
helpviewer_keywords: 
  - "Struttura BP_PASSCOUNT"
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritto il conteggio e le condizioni in cui un punto di interruzione viene generato.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```c#  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## Membri  
 `dwPassCount`  
 Il numero di volte per passare il punto di interruzione prima di generare.  
  
 `stylePassCount`  
 Un valore [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) dell'enumerazione che specifica lo stile del conteggio della sessione del punto di interruzione.  
  
## Note  
 Questa struttura è un membro [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) della struttura.  
  
 Questa struttura passata come parametro[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) ai metodi[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md) e.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)