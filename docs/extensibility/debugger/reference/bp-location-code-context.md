---
title: "BP_LOCATION_CODE_CONTEXT | Microsoft Docs"
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
  - "BP_LOCATION_CODE_CONTEXT"
helpviewer_keywords: 
  - "Struttura BP_LOCATION_CODE_CONTEXT"
ms.assetid: 37412896-021a-4f73-9bb7-4125502c2e18
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_CODE_CONTEXT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritta la posizione di un punto di interruzione associato direttamente a un indirizzo nel programma sottoposto a debug.  
  
## Sintassi  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_CONTEXT {   
   IDebugCodeContext2* pCodeContext;  
} BP_LOCATION_CODE_CONTEXT;  
```  
  
## Membri  
 pCodeContext  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) L'oggetto che identifica la posizione del punto di interruzione nel codice.  
  
## Note  
 Questa struttura è un membro [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) della struttura come parte di unione.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)