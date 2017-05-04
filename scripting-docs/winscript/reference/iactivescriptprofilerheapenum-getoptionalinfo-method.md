---
title: "Metodo IActiveScriptProfilerHeapEnum::GetOptionalInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99ed9df5-71cf-4c25-b189-af9accc466ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Metodo IActiveScriptProfilerHeapEnum::GetOptionalInfo
Ottiene le informazioni facoltative per l'oggetto specificato \(dal set di oggetti dell'heap restituiti da [Metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)\).  
  
 Non è necessario liberare la memoria assegnata agli oggetti restituiti.  Chiamare, invece, [Metodo IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo](../../winscript/reference/iactivescriptprofilerheapenum-freeobjectandoptionalinfo-method.md).  
  
## Sintassi  
  
```  
HRESULT GetOptionalInfo (  
    [in] PROFILER_HEAP_OBJECT* heapObject,  
    [in] ULONG celt,  
    [out, size_is(celt)] PROFILER_HEAP_OBJECT_OPTIONAL_INFO* optionalInfo);  
  
```  
  
#### Parametri  
 `heapObject`  
 Oggetto [Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) per il quale restituire l'informazione.  
  
 `celt`  
 Numero di strutture [Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) da restituire.  
  
 `optionalInfo`  
 \[out\] Una matrice di strutture [Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md) per l'oggetto specificato.  
  
## Valore restituito  
 HRESULT.