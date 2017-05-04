---
title: "Metodo IActiveScriptProfilerHeapEnum::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0336286f-1dcd-4df9-adf5-76b59b4e74bb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IActiveScriptProfilerHeapEnum::Next
Ottiene l'oggetto successivo o gli oggetti nell'heap oggetti da [Metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).  
  
## Sintassi  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] PROFILER_HEAP_OBJECT** heapObjects,   
    [out] ULONG *pceltFetched);  
  
```  
  
#### Parametri  
 `celt`  
 Numero di oggetti da restituire.  
  
 `heapObjects`  
 \[out\] le strutture seguenti [Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).  
  
 `pceltFetched`  
 \[out\] numero di oggetti restituiti,  
  
## Valore restituito  
 HRESULT.