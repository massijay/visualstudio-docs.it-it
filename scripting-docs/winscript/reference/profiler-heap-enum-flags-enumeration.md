---
title: "Enumerazione PROFILER_HEAP_ENUM_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Enumerazione PROFILER_HEAP_ENUM_FLAGS
Flag che rappresentano se viene esposta un'informazione aggiuntiva su un oggetto heap puntato in una relazione tra oggetti.  Utilizzato nel metodo [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).  
  
## Sintassi  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,  
    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,  
} PROFILER_HEAP_ENUM_FLAGS;  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_ENUM\_FLAGS\_NONE|0x00000000|Questo oggetto heap non espone informazioni aggiuntive su una relazione tra oggetti.  Questo oggetto dell'heap si comporta come [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|PROFILER\_HEAP\_ENUM\_ENUM\_ STORE\_RELATIONSHIP\_FLAGS|0x00000001|Questo oggetto heap esporrà informazioni sulla possibilità o meno che un oggetto puntato in una relazione tra oggetti sia un metodo Get o un metodo Set.  Queste informazioni vengono memorizzate nel livello 2 byte \(16 bit\) del campo [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) come uno dei valori di enumerazione [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md).|