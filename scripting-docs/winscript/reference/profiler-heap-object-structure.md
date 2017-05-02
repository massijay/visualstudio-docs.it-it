---
title: "Struttura PROFILER_HEAP_OBJECT | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9f35362c-6856-4cfb-b990-031a156a58eb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Struttura PROFILER_HEAP_OBJECT
Rappresenta gli oggetti dell'heap raccolti da [Metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Sintassi  
  
```  
typedef struct _PROFILER_HEAP_OBJECT  
{  
    UINT size;  
    union {  
        PROFILER_HEAP_OBJECT_ID objectId;  
        PROFILER_EXTERNAL_OBJECT_ADDRESS externalObjectAddress;  
    };  
    PROFILER_HEAP_OBJECT_NAME_ID typeNameId;  
    USHORT flags;   
    USHORT optionalInfoCount;  
} PROFILER_HEAP_OBJECT;  
```  
  
## Membri  
  
|Membro|Type|Descrizione|  
|------------|----------|-----------------|  
|objectId|[Tipo PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|ID dell'oggetto dell'heap.|  
|externalObjectAddress|[Tipo PROFILER\_EXTERNAL\_OBJECT\_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L'indirizzo esterno dell'oggetto di un oggetto, come oggetto di tipo C\+\+\-allocated, che è esterno dell'heap JavaScript.|  
|typeNameId|[Tipo PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'id del nome del tipo object heap, recuperato da [IActiveScriptProfilerHeapEnum::GetNameIdMap](../../winscript/reference/iactivescriptprofilerheapenum-getnameidmap.md).  Solo uno `externalObjectAddress` o `typeName` è presente in base al valore `flags`.|  
|flag|[Enumerazione PROFILER\_HEAP\_OBJECT\_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flag che contengono informazioni di base sull'heap.|  
|optionalInfoCount|USHORT|Il numero di record [Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) disponibili per l'oggetto dell'heap.|