---
title: "IActiveScriptProfilerCallback::ScriptCompiled | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProfilerCallback.ScriptCompiled
apilocation: scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptProfilerCallback::ScriptCompiled
Notifica all'oggetto del profiler che il motore di scripting inserire uno script.  Questo metodo viene chiamato a ogni script che viene compilato.  
  
## Sintassi  
  
```  
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### Parametri  
 `scriptId`  
 \[in\] ID univoco di script che è stato compilato.  Questo ID assegnato nel motore di scripting.  
  
 `type`  
 \[in\] tipo di script che è stato compilato.  i valori sono definiti in [Enumerazione PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 \[in\] se disponibile, un puntatore a un'interfaccia `IUnknown` che il profiler deve eseguire una query per un puntatore [Interfaccia IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md).  In caso contrario, questo sarà null.  
  
## Valore restituito  
 Il valore restituito del metodo viene ignorato dal motore di scripting.  
  
## Note  
 Il motore di scripting può fornire contesto del documento solo se questo è supportato dall'host.  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)