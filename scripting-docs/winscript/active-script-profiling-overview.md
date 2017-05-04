---
title: "Panoramica di profilatura di script ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilatura script ActiveX"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Panoramica di profilatura di script ActiveX
[Interfacce del profiler dello script ActiveX](../winscript/reference/active-script-profiler-interfaces.md) abilita il profilo di un motore di scripting.  Profilare attivo script è costituito dalle parti seguenti:  
  
-   Motore di linguaggio  
  
-   Host  
  
-   Profiler  
  
## Motore di linguaggio  
 Il motore di linguaggio esegue lo script.  Fornisce metodi che consentono l'analisi del codice di script che viene eseguito.  Quando la profilatura è abilitato, il motore di linguaggio accetti l'identificatore di classe \(CLSID\) dell'oggetto COM del profiler come argomento.  Crea un'istanza dell'oggetto COM del profiler e chiama quindi il profiler quando si verificano vari eventi.  
  
 Il motore di linguaggio implementa [Interfaccia IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md)\).  
  
> [!NOTE]
>  Il Language Runtime di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] controlla la variabile di ambiente JS\_PROFILER di creazione per determinare se il profilo deve essere attivato.  Se la variabile è impostata sul CLSID del profiler, Language Runtime crea un'istanza dell'oggetto COM del profiler, utilizzando il valore della variabile per determinare il profiler da creare.  
  
## Host  
 L'host crea il motore di linguaggio e fornisce il motore di linguaggio con script da eseguire.  Uno SmartHost fornisce anche il contesto del documento utilizzabili da un debugger o da un profiler per fornire più informazioni in caso di debug o di profilatura.  
  
## Profiler  
 Il profiler riceve le chiamate dal motore di linguaggio quando si verificano vari eventi.  Il profiler deve essere registrato come oggetto COM e deve implementare l'interfaccia di [Interfaccia IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md) \).  
  
## Vedere anche  
 [Interfacce del profiler dello script ActiveX](../winscript/reference/active-script-profiler-interfaces.md)