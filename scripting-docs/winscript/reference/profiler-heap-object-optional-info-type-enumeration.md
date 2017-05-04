---
title: "Enumerazione PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: fcb55f5f-ce75-4d05-9ce9-ba28c622f97d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Enumerazione PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE
Rappresenta i diversi tipi di informazioni facoltative.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).  
  
## Sintassi  
  
```  
typedef [v1_enum] enum {  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE                    = 0x00000001,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME                = 0x00000002,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST                   = 0x00000003,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY            = 0x00000004,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES              = 0x00000005,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES             = 0x00000006,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE      = 0x00000007,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE   = 0x00000008,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS                = 0x00000009,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS                  = 0x0000000A,  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_MAX_VALUE                    = PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE;  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_PROTOTYPE|0x00000001|Informazioni sul prototipo dell'oggetto dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_FUNCTION\_NAME|0x00000002|Informazioni sul nome di funzione dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_SCOPE\_LIST|0x00000003|Informazioni su [Struttura PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)dell'oggetto dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INTERNAL\_PROPERTY|0x00000004|Informazioni sulla proprietà interna dell'oggetto dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_NAME\_PROPERTIES|0x00000005|Informazioni sulle proprietà dell'oggetto dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_INDEX\_PROPERTIES|0x00000006|Informazioni sulle proprietà dell'indice dell'oggetto dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_ATTRIBUTES\_SIZE|0x00000007|La dimensione degli attributi associati a un elemento DOM.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_ELEMENT\_TEXT\_CHILDREN\_SIZE|0x00000008|La dimensione del testo associato a un elemento DOM.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_RELATIONSHIPS|0x00000009|Informazioni sulle relazioni dell'oggetto dell'heap.|  
|ROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|0x0000000A|Informazioni sugli eventi di runtime delle finestre dell'oggetto dell'heap.|  
|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_MAX\_VALUE|PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFORMATION\_WINRTEVENTS|Il valore massimo dell'enumerazione.|