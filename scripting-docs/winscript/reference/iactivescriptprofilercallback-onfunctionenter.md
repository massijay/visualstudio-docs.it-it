---
title: "IActiveScriptProfilerCallback::OnFunctionEnter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.OnFunctionEnter
apilocation: scrobj.dll
ms.assetid: 12dab2b4-df4e-444d-99cb-25e1c278e6e8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptProfilerCallback::OnFunctionEnter
Notifica all'oggetto del profiler che il motore di scripting sta per l'esecuzione di una chiamata di funzione che non è una chiamata nel Document Object Model \(DOM\).  
  
## Sintassi  
  
```  
HRESULT OnFunctionEnter(  
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
 Per le chiamate DOM, il motore di scripting chiama [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md) anziché `IActiveScriptProfilerCallback::OnFunctionEnter`.  Ciò è dovuto al numero di metodi e proprietà univoci nel DOM.  
  
## Vedere anche  
 [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)   
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)