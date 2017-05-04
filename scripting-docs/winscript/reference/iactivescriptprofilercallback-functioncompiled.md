---
title: "IActiveScriptProfilerCallback::FunctionCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.FunctionCompiled
apilocation: scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::FunctionCompiled
Notifica all'oggetto del profiler che il motore di scripting ha rilevato una funzione durante la compilazione di uno script.  
  
## Sintassi  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Parametri  
 `functionId`  
 \[in\] ID univoco della funzione.  Questo ID assegnato nel motore di scripting.  
  
 `scriptId`  
 \[in\] ID univoco di script che la funzione fa parte di.  
  
 `pwszFunctionName`  
 \[in\] il nome della funzione, o null per una funzione anonima.  
  
 `pwszFunctionNameHint`  
 \[in\] il nome dedotto della funzione, o null se il motore di scripting non deduce alcun nome.  
  
 `pIDebugDocumentContext`  
 \[in\] se disponibile, il puntatore a un'interfaccia `IUnknown` che il profiler deve eseguire una query per un puntatore [Interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md).  In caso contrario, Null.  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.  
  
## Note  
 Il motore di scripting può fornire contesto del documento solo se questo è supportato dall'host.  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)