---
title: "IActiveScriptProfilerCallback::OnFunctionExit | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionExit
apilocation: scrobj.dll
ms.assetid: a5d21715-2b0b-423e-8644-f04a9e7cde3d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionExit
Notifica all'oggetto del profiler che il motore di scripting ha termine di una chiamata di funzione che non è una chiamata nel Document Object Model \(DOM\).  
  
## Sintassi  
  
```  
HRESULT OnFunctionExit(  
    [in] PROFILER_TOKEN scriptId,   
    [in] PROFILER_TOKEN functionId);  
```  
  
#### Parametri  
 `scriptId`  
 \[in\] ID univoco di script che la funzione fa parte di.  Questo ID assegnato nel motore di scripting.  
  
 `functionId`  
 \[in\] ID univoco della funzione.  Questo ID assegnato nel motore di scripting.  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.  
  
## Note  
 Per le chiamate DOM, il motore di scripting chiama [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md) anziché `IActiveScriptProfilerCallback::OnFunctionExit`.  Ciò è dovuto al numero di metodi e proprietà univoci nel DOM.  
  
## Vedere anche  
 [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)   
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)