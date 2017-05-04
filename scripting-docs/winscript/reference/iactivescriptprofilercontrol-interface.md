---
title: "Interfaccia IActiveScriptProfilerControl | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Interfaccia IActiveScriptProfilerControl
Implementato nel motore di scripting il profilo di supportare.  In genere, un oggetto che implementa `IActiveScriptProfilerControl` implementa anche l'interfaccia [IActiveScript](../../winscript/reference/iactivescript.md).  In questo caso, è possibile ottenere un handle all'interfaccia `IActiveScriptProfilerControl` chiamando il metodo `IUnknown::QueryInterface` l'oggetto.  L'interfaccia fornisce i metodi necessari per interrompere e avviare la profilatura sul motore di scripting.  
  
## Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Iniziare la profilatura sul motore di scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Imposta la maschera eventi del profiler nel motore di scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Consente di interrompere la profilatura sul motore di scripting.|  
  
## Vedere anche  
 [Interfacce del profiler dello script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)