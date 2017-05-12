---
title: "Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3ab3d986-3314-4c7b-a1c8-18ed691a8b9c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Struttura PROFILER_HEAP_OBJECT_RELATIONSHIP
Rappresenta una relazione di un oggetto heap.  
  
## Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_RELATIONSHIP  
{  
    PROFILER_HEAP_OBJECT_NAME_ID relationshipId;  
    PROFILER_RELATIONSHIP_INFO relationshipInfo;  
    [switch_type(PROFILER_RELATIONSHIP_INFO), switch_is(relationshipInfo)] union  
    {  
        [case(PROFILER_PROPERTY_TYPE_NUMBER)] double numberValue;  
        [case(PROFILER_PROPERTY_TYPE_STRING)] LPCWSTR stringValue;  
        [case(PROFILER_PROPERTY_TYPE_HEAP_OBJECT)] PROFILER_HEAP_OBJECT_ID objectId;  
        [case(PROFILER_PROPERTY_TYPE_EXTERNAL_OBJECT)] PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
} PROFILER_HEAP_OBJECT_RELATIONSHIP;  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|relationshipId|[Tipo PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'id del nome della relazione, da [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).|  
|relationshipInfo|[Enumerazione PROFILER\_INFO\_OBJECT\_FLAGS](../../winscript/reference/profiler-relationship-info-enumeration.md)|Informazioni sulla relazione.|  
|numberValue|double|Il valore del numero.  Solo uno `numberValue``stringValue`\/\/\/`objectId``externalObjectAddress` è impostato, in base al valore `relationshipInfo`.|  
|stringValue|LPCWSTR|Il valore stringa.|  
|objectId|[Tipo PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|ID dell'oggetto dell'heap.|  
|externalObjectAddress|[Tipo PROFILER\_EXTERNAL\_OBJECT\_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L'indirizzo esterno dell'oggetto.|