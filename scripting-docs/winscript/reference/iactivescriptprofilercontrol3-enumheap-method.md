---
title: "Metodo IActiveScriptProfilerControl3::EnumHeap | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo IActiveScriptProfilerControl3::EnumHeap
Restituisce un'interfaccia \([Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) che può essere utilizzata per scorrere gli oggetti heap GC nel contesto del modulo di gestione di script collegato.  
  
 È possibile chiamare il metodo in debug o di rilascio.  Questo metodo deve essere chiamato quando il thread UI è inattivo.  Una volta chiamato il metodo, nessuna operazione deve essere eseguita nel modulo di gestione di script tranne [Metodo IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) [Metodo IActiveScriptProfilerHeapEnum::Next](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) finché non restituisce S\_FALSE o un puntatore a interfaccia [Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) venga rilasciato.  
  
## Sintassi  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### Parametri  
 ppEnum  
 \[out\] Restituisce l'oggetto [Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md).  
  
## Valore restituito  
 HRESULT.