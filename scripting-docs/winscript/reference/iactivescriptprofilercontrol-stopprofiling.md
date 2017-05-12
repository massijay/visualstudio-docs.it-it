---
title: "IActiveScriptProfilerControl::StopProfiling | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerControl.StopProfiling
apilocation: scrobj.dll
ms.assetid: 23b46ed6-a398-44c0-bc49-bf122e697cfe
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerControl::StopProfiling
Consente di interrompere la profilatura sul motore di scripting.  Questo metodo chiama [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) l'oggetto del profiler e lo rilascia.  
  
## Sintassi  
  
```  
HRESULT StopProfiling(  
    [in] HRESULT hrShutdownReason);  
```  
  
#### Parametri  
 `hrShutdownReason`  
 \[in\] l'hresult venga passato come parametro al metodo [IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md) dell'oggetto del profiler.  
  
## Valore restituito  
 Restituisce un HRESULT.  I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La profilatura non è abilitato.|  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)