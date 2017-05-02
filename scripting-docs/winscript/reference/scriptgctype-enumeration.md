---
title: "Enumerazione SCRIPTGCTYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Enumerazione SCRIPTGCTYPE
Il tipo di operazione da eseguire.  Utilizzato nel metodo [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md).  
  
## Sintassi  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {  
    SCRIPTGCTYPE_NORMAL           = 0,  
    SCRIPTGCTYPE_EXHAUSTIVE       = 1,  
} SCRIPTGCTYPE;  
  
```  
  
## Valori di enumerazione  
  
|||  
|-|-|  
|SCRIPTGCTYPE\_NORMAL|Scegliere la modalità normale.  Il valore Integer è 0.|  
|SCRIPTGCTYPE\_EXHAUSTIVE|Scegliere il Garbage Collection completa.  Il valore Integer è 1.|  
  
## Vedere anche  
 [Costanti, enumerazioni e codici di errore dello script ActiveX](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)