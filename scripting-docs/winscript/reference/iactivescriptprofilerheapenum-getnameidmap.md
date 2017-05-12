---
title: "IActiveScriptProfilerHeapEnum::GetNameIdMap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 88514c93-850b-48d4-9a68-1e27d7411f0d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IActiveScriptProfilerHeapEnum::GetNameIdMap
Restituisce i nomi di stringhe che corrispondono ai valori [Tipo PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md).  
  
## Sintassi  
  
```  
HRESULT GetNameIdMap (  
    [out, size_is(,*pcelt)] LPCWSTR* pNameList[],   
    [out] UINT *pcelt);  
```  
  
#### Parametri  
 `pNameList`  
 \[out\] matrice dei nomi associati ai valori [Tipo PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md).  
  
 `pcelt`  
 \[out\] numero dei nomi nella matrice.  
  
## Valore restituito  
 HRESULT.