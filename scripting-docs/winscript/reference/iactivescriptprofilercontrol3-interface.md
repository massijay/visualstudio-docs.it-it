---
title: "Interfaccia IActiveScriptProfilerControl3 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 64bc860a-54d4-475a-80f6-2f9dba6448ee
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Interfaccia IActiveScriptProfilerControl3
Fornisce un metodo per enumerare sugli oggetti dell'heap GC associati a un modulo di gestione di script.  
  
## Sintassi  
  
```  
interface IActiveScriptProfilerControl3 : IActiveScriptProfilerControl2  
```  
  
## Metodi  
 [Metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)  
 Restituisce un'interfaccia \([Interfaccia IActiveScriptProfilerHeapEnum](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\) che può essere utilizzata per scorrere gli oggetti heap GC nel contesto del modulo di gestione di script collegato.