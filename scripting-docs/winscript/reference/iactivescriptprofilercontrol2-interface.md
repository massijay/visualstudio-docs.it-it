---
title: "Interfaccia IActiveScriptProfilerControl2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IActiveScriptProfilerControl2"
ms.assetid: 89455276-5c23-420b-a7e0-804a32635291
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Interfaccia IActiveScriptProfilerControl2
Fornisce metodi che aggiungono la possibilità di iniziare o interrompere la profilatura quando uno script in esecuzione.  
  
## Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md)|Notifica al profiler aver avviato il profilo in tutti i moduli di gestione di scripting applicabili.  Ciò consente di ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando avviare la profilatura.|  
|[IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)|Notifica al profiler che si desidera interrompere la profilatura in tutti i moduli di gestione di scripting applicabili.  Ciò consente di ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] in esecuzione quando si interrompe il profilo.|  
  
## Vedere anche  
 [Interfaccia IActiveScriptProfilerControl](../../winscript/reference/iactivescriptprofilercontrol-interface.md)   
 [Interfacce del profiler dello script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)