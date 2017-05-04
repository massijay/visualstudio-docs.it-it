---
title: "Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 46ca87ea-5b0f-437d-a33f-b2d9a457e036
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST
Rappresenta un elenco delle relazioni che appartengono a un oggetto heap.  
  
## Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_RELATIONSHIP elements[];  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST;  
  
```  
  
## Membri  
  
|Membro|Type|Descrizione|  
|------------|----------|-----------------|  
|Conteggio|UINT|Il numero delle relazioni di un oggetto heap.|  
|elementi|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Le relazioni di un oggetto heap.|