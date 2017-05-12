---
title: "Enumerazione APPLICATION_NODE_EVENT_FILTER | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Costanti APPLICATION_NODE_EVENT_FILTER"
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Enumerazione APPLICATION_NODE_EVENT_FILTER
Specifica i tipi di nodi per escludere quando filtrando i documenti di codice.  Utilizzato in [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) e in [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
>  Queste costanti sono implementate da PDM v10.0 e maggiore.  Trovato in activdbg100.h.  
  
## Sintassi  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {  
    FILTER_EXCLUDE_NOTHING = 0,  
    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,  
    FILTER_EXCLUDE_EVAL_CODE = 0x2  
} APPLICATION_NODE_EVENT_FILTER;  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|FILTER\_EXCLUDE\_NOTHING|0x00000000|Inviare tutti gli eventi.|  
|FILTER\_EXCLUDE\_ANONYMOUS\_CODE|0x00000001|Escludere i nodi anonimi di codice.  Questi nodi sono utilizzati dal runtime JScript per `new Function([args,] <code>)'`.|  
|FILTER\_EXCLUDE\_EVAL\_CODE|0x00000002|Escludere i nodi eval di codice.  Questi nodi sono utilizzati dal runtime JScript per supportare eval.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)