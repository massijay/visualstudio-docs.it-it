---
title: "BP_COND_STYLE | Microsoft Docs"
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
  - "BP_COND_STYLE"
helpviewer_keywords: 
  - "Enumerazione BP_COND_STYLE"
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_COND_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica lo stile della condizione del punto di interruzione per i punti di interruzione in corso e associati.  
  
## Sintassi  
  
```cpp#  
enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
typedef DWORD BP_COND_STYLE;  
```  
  
```c#  
public enum enum_BP_COND_STYLE {   
   BP_COND_NONE         = 0x0000,  
   BP_COND_WHEN_TRUE    = 0x0001,  
   BP_COND_WHEN_CHANGED = 0x0002  
};  
```  
  
## Membri  
 BP\_COND\_NONE  
 Genera il punto di interruzione quando la posizione del punto di interruzione viene soddisfatta.  Nessuna condizione del punto di interruzione specificata.  
  
 BP\_COND\_WHEN\_TRUE  
 Genera il punto di interruzione solo quando l'espressione condizionale associata al punto di interruzione dà come risultato `true`.  
  
 BP\_COND\_WHEN\_CHANGED  
 Genera il punto di interruzione solo quando il valore dell'espressione condizionale associata al punto di interruzione è stato modificato dalla valutazione precedente.  
  
## Note  
 Utilizzato per il membro di `styleCondition` [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) della struttura.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)