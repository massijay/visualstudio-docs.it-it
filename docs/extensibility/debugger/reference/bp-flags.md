---
title: "BP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_FLAGS"
helpviewer_keywords: 
  - "Enumerazione BP_FLAGS"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Fornisce i flag facoltativi che possono essere utilizzati per specificare informazioni aggiuntive quando si imposta un punto di interruzione.  
  
## Sintassi  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## Membri  
 BP\_FLAG\_NONE  
 Non specifica il flag punto di interruzione.  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 Specifica che il motore di debug \(DE\) deve eseguire il mapping del punto di interruzione utilizzando la posizione del documento.  È applicabile solo ai punti di interruzione in un file di origine basati su script come pagine \(ASP\) ASP.  
  
 \_STOP OF BP\_FLAG\_DO NOT  
 Specifica che il punto di interruzione deve essere elaborato dal motore di debug, ma che il motore di debug finally non verrà arrestata in \(ovvero [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) un oggetto evento non è necessario inviare\).  Questo flag è progettato per essere utilizzato principalmente con i punti di analisi.  
  
## Note  
 Utilizzato per il membro di `dwFlags` [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) strutture.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)