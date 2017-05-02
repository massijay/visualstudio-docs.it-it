---
title: "IActiveScriptProfilerControl::StartProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StartProfiling
apilocation: scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerControl::StartProfiling
Iniziare la profilatura sul motore di scripting.  Il modulo di gestione di script crea un'istanza dell'oggetto del profiler tramite una chiamata a [CoCreateInstance](http://msdn.microsoft.com/it-it/7295a55b-12c7-4ed0-a7a4-9ecee16afdec).  
  
## Sintassi  
  
```  
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### Parametri  
 `clsidProfilerObject`  
 \[in\] identificatore di classe \(CLSID\) dell'oggetto del profiler da creare.  
  
 `dwEventMask`  
 \[in\] A una maschera di bit a 4 byte che specifica i tipi di eventi.  i bit sono definiti in [Enumerazione PROFILER\_EVENT\_MASK](../../winscript/reference/profiler-event-mask-enumeration.md).  
  
 `dwContext`  
 \[in\] valore byte A 4 passato all'oggetto del profiler.  
  
## Valore restituito  
 Restituisce un HRESULT.  I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`ACTIVPROF_E_PROFILER_PRESENT`|La profilatura è già attivato.|  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)