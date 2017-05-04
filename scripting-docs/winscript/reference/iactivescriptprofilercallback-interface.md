---
title: "Interfaccia IActiveScriptProfilerCallback | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Interfaccia IActiveScriptProfilerCallback
Fornisce i metodi utilizzati dal motore di scripting per notificare a un oggetto del profiler quando si verificano gli eventi.  L'interfaccia viene implementata dall'oggetto del profiler.  
  
## Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Chiamato per inizializzare l'oggetto del profiler ogni volta che la profilatura viene avviato in un motore di scripting.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Chiamato per liberare e rilasciare l'oggetto del profiler ogni volta che l'esecuzione viene interrotta in un motore di scripting.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica all'oggetto del profiler che il motore di scripting completare lo script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica all'oggetto del profiler che il motore di scripting ha rilevato una funzione durante la compilazione di uno script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica all'oggetto del profiler che il motore di scripting sta per l'esecuzione di una chiamata di funzione che non è una chiamata nel Document Object Model \(DOM\).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica all'oggetto del profiler che il motore di scripting ha termine di una chiamata di funzione che non è una chiamata nel DOM.|  
  
## Note  
 La notifica delle chiamate di funzione nel Document Object Model \(DOM\) viene fornita da [Interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Per aggiungere la possibilità di avviare e interrompere la profilatura quando uno script, chiamare i metodi seguenti.  Utilizzando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione all'avvio o si di profilatura.  
>   
>  -   Chiamare [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler aver avviato il profilo.  
> -   Chiamare [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che precedentemente smetterete di profilatura.  
  
## Vedere anche  
 [Interfacce del profiler dello script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)