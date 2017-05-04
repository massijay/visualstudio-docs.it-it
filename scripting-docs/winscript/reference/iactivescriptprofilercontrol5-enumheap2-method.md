---
title: "Metodo IActiveScriptProfilerControl5::EnumHeap2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IActiveScriptProfilerControl5::EnumHeap2
Restituisce un'interfaccia \([Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) che può essere utilizzata per scorrere gli oggetti dell'heap GC nel contesto del motore di script associato.  
  
 È possibile chiamare questo metodo nella modalità di debug o di rilascio.  Questo metodo deve essere chiamato quando il thread UI non è attivo.  Dopo che il metodo è stato chiamato, non deve essere eseguita alcuna operazione in base al modulo di gestione di script, tranne [Metodo IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md), fino a quando [Metodo IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) non restituisce S\_FALSE o il puntatore a interfaccia [Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) non viene rilasciato.  
  
## Sintassi  
  
```  
HRESULT EnumHeap2(  
    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,  
    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Parametri  
 enumFlags  
 Valore che specifica se vengono esposte ulteriori informazioni su un oggetto puntato in una relazione tra oggetti.  Informazioni aggiuntive possono indicare se l'oggetto puntato è un metodo di impostazione o di richiamo.  Per ulteriori informazioni, vedi [Enumerazione PROFILER\_HEAP\_ENUM\_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md).  
  
 ppEnum  
 \[out\] Restituisce l'oggetto [Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Valore restituito  
 Restituisce un HRESULT.  I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|L'enumerazione dell'heap completata correttamente.|  
|`E_OUTOFMEMORY`|Non vi è disponibile memoria sufficiente eseguire l'enumerazione dell'heap.|  
|`E_FAIL`|Errore interno.|