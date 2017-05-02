---
title: "Struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Struttura PROFILER_HEAP_OBJECT_OPTIONAL_INFO
Rappresenta le informazioni facoltative sugli oggetti dell'heap.  
  
## Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO  
{  
    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;  
    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union  
    {  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;  
        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;  
    };  
} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
  
```  
  
## Membri  
  
|Membro|Type|Descrizione|  
|------------|----------|-----------------|  
|infoType|[Enumerazione PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Il tipo di informazioni facoltative.|  
|prototipo|[Tipo PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|ID dell'oggetto prototipo dell'oggetto dell'heap.|  
|`functionName`|LPCWSTR|Il nome di funzione dell'heap.|  
|elementAttributesSize|UINT|La dimensione dell'elemento dell'oggetto dell'heap.|  
|elementTextChildrenSize|UINT|La dimensione dei figli dell'oggetto dell'heap.|  
|scopeList|[Struttura PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|L'elenco dell'ambito dell'oggetto dell'heap.|  
|internalProperty|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|La proprietà interna dell'oggetto dell'heap.|  
|namePropertyList|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Un elenco delle proprietà dell'oggetto dell'heap.|  
|indexPropertyList|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Un elenco di proprietà dell'oggetto dell'heap.|  
|relationshipList|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Un elenco delle relazioni dell'oggetto dell'heap.|  
|eventList|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Un elenco di eventi dell'oggetto dell'heap.|