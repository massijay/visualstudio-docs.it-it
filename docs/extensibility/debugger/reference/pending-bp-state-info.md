---
title: "PENDING_BP_STATE_INFO | Microsoft Docs"
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
  - "PENDING_BP_STATE_INFO"
helpviewer_keywords: 
  - "Struttura PENDING_BP_STATE_INFO"
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene informazioni sullo stato di un punto di interruzione che è pronto per l'associazione a un percorso di codice.  
  
## Sintassi  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```c#  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## Membri  
 Stato di  
 Un valore [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) dell'enumerazione che specifica lo stato del punto di interruzione in attesa.  
  
 flag  
 Una combinazione di flag [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) dall'enumerazione che specifica se il punto di interruzione viene virtualizzato.  
  
## Note  
 Questa struttura viene passata [GetState](../Topic/IDebugPendingBreakpoint2::GetState.md) al metodo in cui viene soddisfatta.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)   
 [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)