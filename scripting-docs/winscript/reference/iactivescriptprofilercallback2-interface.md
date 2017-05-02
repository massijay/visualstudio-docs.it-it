---
title: "Interfaccia IActiveScriptProfilerCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptProfilerCallback2"
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Interfaccia IActiveScriptProfilerCallback2
Fornisce i metodi utilizzati dal motore di scripting per notificare a un oggetto del profiler quando gli eventi DOM \(Document Object Model \(DOM\) si verificano.  L'interfaccia viene implementata dall'oggetto del profiler.  
  
## Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica all'oggetto del profiler che il motore di script dovrà eseguire una chiamata di funzione DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica all'oggetto del profiler che il motore di scripting ha termine di una chiamata di funzione DOM.|  
  
## Note  
 L'interfaccia `IActiveScriptProfilerCallback2` innanzitutto rilasciata con Internet Explorer 9.  
  
 La notifica delle chiamate di funzione che non vengono chiamate nel DOM è fornita da [Interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Per aggiungere la possibilità di avviare e interrompere la profilatura quando uno script, chiamare i metodi seguenti.  Utilizzando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione all'avvio o si di profilatura.  
>   
>  -   Chiamare [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler aver avviato il profilo.  
> -   Chiamare [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che precedentemente smetterete di profilatura.  
  
## Vedere anche  
 [Interfacce del profiler dello script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)