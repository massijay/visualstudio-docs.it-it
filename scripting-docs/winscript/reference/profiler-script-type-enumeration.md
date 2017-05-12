---
title: "Enumerazione PROFILER_SCRIPT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: PROFILER_SCRIPT_TYPE
apilocation: scrobj.dll
ms.assetid: 3ab6633a-6241-44f0-b837-14336f70c71e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Enumerazione PROFILER_SCRIPT_TYPE
Specifica il tipo di script.  
  
## Sintassi  
  
```  
typedef enum {  
    PROFILER_SCRIPT_TYPE_USER,  
    PROFILER_SCRIPT_TYPE_DYNAMIC,  
    PROFILER_SCRIPT_TYPE_NATIVE,  
    PROFILER_SCRIPT_TYPE_DOM  
} PROFILER_SCRIPT_TYPE;  
```  
  
## Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|PROFILER\_SCRIPT\_TYPE\_USER|Specifica il codice di script scritto dall'utente.|  
|PROFILER\_SCRIPT\_TYPE\_DYNAMIC|Specifica il codice di script generato dinamicamente durante l'esecuzione.|  
|PROFILER\_SCRIPT\_TYPE\_NATIVE|Specifica il tipo di script per le funzioni native e gli oggetti definiti nel modulo di gestione di script.|  
|PROFILER\_SCRIPT\_TYPE\_DOM|Specifica una chiamata nel Document Object Model \(DOM\) di Internet Explorer, ad esempio, una chiamata al metodo `document.getElementById`.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del profiler di script ActiveX](../../winscript/reference/active-script-profiler-constants-enumerations-and-structures.md)   
 [IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)   
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)