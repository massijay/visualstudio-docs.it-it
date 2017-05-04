---
title: "IActiveScriptProfilerCallback::Initialize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Initialize
apilocation: scrobj.dll
ms.assetid: a257111e-a50b-4962-9dd6-c893d40f6985
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptProfilerCallback::Initialize
Chiamato per inizializzare l'oggetto del profiler ogni volta che la profilatura viene avviato in un motore di scripting.  
  
## Sintassi  
  
```  
HRESULT Initialize(  
    [in] DWORD dwContext);  
```  
  
#### Parametri  
 `dwContext`  
 \[in\] valore byte A 4 che viene passato a [IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md).  
  
## Valore restituito  
 Restituisce un HRESULT.  I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Se il metodo non può inizializzare l'oggetto del profiler, deve restituire un HRESULT di errore per notificare al motore di scripting.  In questo caso, il motore di scripting deve chiamare direttamente [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md), passando il del parametro e quindi rilascia l'oggetto del profiler.  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)