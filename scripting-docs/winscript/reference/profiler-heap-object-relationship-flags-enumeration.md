---
title: "Enumerazione PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Enumerazione PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS
Flag che rappresentano se un oggetto heap puntato in una relazione tra oggetti è un metodo di impostazione o di richiamo.  Utilizzato nel metodo [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) quando il valore di PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS viene specificato nel parametro `enumFlags`.  
  
## Sintassi  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,  
    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,  
} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_NONE|0x00000000|Questo oggetto heap puntato in una relazione tra oggetti non è identificato come metodo Get o metodo Set.|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_GET\_ACCESSOR|0x00010000|L'oggetto heap puntato in una relazione tra oggetti è un metodo Get.  Queste informazioni vengono memorizzate nel livello 2 byte \(16 bit\) del campo [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS\_IS\_SET\_ACCESSOR|0x00020000|L'oggetto heap puntato in una relazione tra oggetti è un metodo Set.  Queste informazioni vengono memorizzate nel livello 2 byte \(16 bit\) del campo `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo`.|