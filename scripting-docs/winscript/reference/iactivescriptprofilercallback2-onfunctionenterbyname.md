---
title: "IActiveScriptProfilerCallback2::OnFunctionEnterByName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptProfilerCallback2::OnFunctionEnterByName"
ms.assetid: 24b1593a-97fc-4d70-9b85-ec86fb59f987
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptProfilerCallback2::OnFunctionEnterByName
Notifica all'oggetto del profiler che il motore di script dovrà eseguire una chiamata di funzione DOM \(Document Object Model \(DOM\).  
  
## Sintassi  
  
```  
HRESULT OnFunctionEnterByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
```  
  
#### Parametri  
 `pwszFunctionName`  
 \[in\] il nome della funzione che il motore di script dovrà eseguire.  
  
 `scriptType`  
 \[in\] tipo di funzione.  Per le descrizioni dei valori validi, vedere [Enumerazione PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.  
  
## Note  
 Per le chiamate DOM, il motore di scripting chiama questo metodo anziché chiamare [IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md).  Ciò è dovuto al numero di metodi e proprietà univoci nel DOM.  
  
## Vedere anche  
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)   
 [Interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md)