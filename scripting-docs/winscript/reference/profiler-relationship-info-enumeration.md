---
title: "Enumerazione PROFILER_INFO_OBJECT_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fae69317-6224-4a6a-8e9e-ccaa6a330818
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Enumerazione PROFILER_INFO_OBJECT_FLAGS
Rappresenta le informazioni sull'oggetto in relazione.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## Sintassi  
  
```  
typedef [v1_enum] enum {  
    PROFILER_PROPERTY_TYPE_NUMBER = 0x01,  
    PROFILER_PROPERTY_TYPE_STRING = 0x02,  
    PROFILER_PROPERTY_TYPE_HEAP_OBJECT = 0x03,  
    PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT = 0x04,  
    PROFILER_PROPERTY_TYPE_BSTR = 0x05,  
} PROFILER_RELATIONSHIP_INFO;  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|PROFILER\_PROPERTY\_TYPE\_NUMBER|0x01|l'oggetto è un numero.|  
|PROFILER\_PROPERTY\_TYPE\_STRING|0x02|l'oggetto è una stringa.|  
|PROFILER\_PROPERTY\_TYPE\_HEAP\_OBJECT|0x03|L'oggetto è un oggetto heap.|  
|PROFILER\_PROPERTY\_TYPE\_EXTERNAL\_OBJECT|0x04|L'oggetto è esterno, ovvero, non nell'heap di Garbage Collection.|  
|PROFILER\_PROPERTY\_TYPE\_BSTR|0x05|l'oggetto è un BSTR.|