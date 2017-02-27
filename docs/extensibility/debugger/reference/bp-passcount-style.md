---
title: "BP_PASSCOUNT_STYLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_PASSCOUNT_STYLE"
helpviewer_keywords: 
  - "Struttura BP_PASSCOUNT_STYLE"
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_PASSCOUNT_STYLE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica la condizione associata al conteggio della sessione del punto di interruzione in modo che il punto di interruzione alla generazione.  
  
## Sintassi  
  
```cpp#  
enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
typedef DWORD BP_PASSCOUNT_STYLE;  
```  
  
```c#  
public enum enum_BP_PASSCOUNT_STYLE {   
   BP_PASSCOUNT_NONE             = 0x0000,  
   BP_PASSCOUNT_EQUAL            = 0x0001,  
   BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,  
   BP_PASSCOUNT_MOD              = 0x0003  
};  
```  
  
## Membri  
 BP\_PASSCOUNT\_NONE  
 Non specifica stile di conteggio della sessione del punto di interruzione.  
  
 BP\_PASSCOUNT\_EQUAL  
 Consente di impostare lo stile di conteggio della sessione del punto di interruzione in modo che sia uguale a.  Le generazioni del punto di interruzione quando il numero di volte in cui il punto di interruzione è uguale raggiunti il conteggio della sessione.  
  
 BP\_PASSCOUNT\_EQUAL\_OR\_GREATER  
 Consente di impostare lo stile di conteggio della sessione del punto di interruzione per essere uguale o maggiore.  Le generazioni del punto di interruzione quando il numero di volte viene raggiunto il punto di interruzione è uguale a o maggiore del numero della sessione.  
  
 BP\_PASSCOUNT\_MOD  
 Specifica un conteggio della sessione di modulo.  Ad esempio, se il conteggio di sessione è di tipo `BP_PASSCOUNT_MOD` e il valore di conteggio della sessione è 4, le generazioni del punto di interruzione ogni volta che il numero di passaggi è un multiplo di 4.  
  
## Note  
 Utilizzato per il membro di `stylePassCount` [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) della struttura che è a sua volta un membro di [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struttura.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)