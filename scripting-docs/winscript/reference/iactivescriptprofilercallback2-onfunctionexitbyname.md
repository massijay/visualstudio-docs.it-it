---
title: "IActiveScriptProfilerCallback2::OnFunctionExitByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionExitByName"
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerCallback2::OnFunctionExitByName
Notifica all'oggetto del profiler che il motore di scripting ha termine di una chiamata di funzione DOM \(Document Object Model \(DOM\).  
  
## Sintassi  
  
```  
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### Parametri  
 `pwszFunctionName`  
 \[in\] il nome della funzione che il motore di scripting il termine dell'esecuzione.  
  
 `scriptType`  
 \[in\] tipo di funzione.  Per le descrizioni dei valori validi, vedere [Enumerazione PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.  
  
## Note  
 Per le chiamate DOM, il motore di scripting chiama questo metodo anziché chiamare [IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md).  Ciò è dovuto al numero di metodi e proprietà univoci nel DOM.  
  
## Vedere anche  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [Interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)