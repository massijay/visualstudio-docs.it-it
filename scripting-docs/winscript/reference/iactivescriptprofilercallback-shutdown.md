---
title: "IActiveScriptProfilerCallback::Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.Shutdown
apilocation: scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptProfilerCallback::Shutdown
Chiamato per notificare all'oggetto del profiler ogni volta che l'esecuzione viene interrotta in un motore di scripting.  Questa modalità, l'oggetto del profiler può chiamare le routine di pulizia, se necessario.  Questo metodo viene chiamato dal motore di scripting quando il motore di scripting fase di chiusura, o quando una chiamata a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) non riesce.  
  
## Sintassi  
  
```  
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### Parametri  
 `hrReason`  
 \[in\] il motivo per interrompere.  Se il motore di scripting viene più utilizzato, `S_OK` viene passato.  Se la chiamata a [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) restituisce un HRESULT di errore, l'hresult viene passato.  In caso contrario, questo valore viene recuperato da [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)