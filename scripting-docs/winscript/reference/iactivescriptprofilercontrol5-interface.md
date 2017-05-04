---
title: "Interfaccia IActiveScriptProfilerControl5 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7fd0ce34-6ae3-428f-ba90-3e86a8a98ed0
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Interfaccia IActiveScriptProfilerControl5
Fornisce un metodo per enumerare negli oggetti dell'heap GC associati a un motore di script.  
  
## Sintassi  
  
```  
interface IActiveScriptProfilerControl5 : IActiveScriptProfilerControl4  
```  
  
## Metodi  
 [Metodo IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)  
 Restituisce un'interfaccia \([Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) che può essere utilizzata per scorrere gli oggetti dell'heap GC nel contesto del motore di script associato.