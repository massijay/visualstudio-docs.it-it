---
title: "TaskExtension Base Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, tool task base class"
  - "tool task base class [MSBuild]"
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# TaskExtension Base Class
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Molte attività ereditano dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Tramite questa catena di ereditarietà vengono aggiunti diversi parametri alle attività da essi derivate.  Tali parametri vengono elencati in questo documento.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri delle classi di base.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine> facoltativo.<br /><br /> Specifica l'interfaccia del modulo di gestione della compilazione disponibile per le attività.  Questo parametro viene impostato automaticamente tramite il motore di compilazione per consentire alle attività di richiamare il motore stesso.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine2> facoltativo.<br /><br /> Specifica l'interfaccia del modulo di gestione della compilazione disponibile per le attività.  Questo parametro viene impostato automaticamente tramite il motore di compilazione per consentire alle attività di richiamare il motore stesso.<br /><br /> Si tratta di una proprietà che consente agli autori di attività che ereditano da questa classe di non dover eseguire il cast del valore da `IBuildEngine` in `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parametro <xref:Microsoft.Build.Framework.IBuildEngine3> facoltativo.<br /><br /> Specifica l'interfaccia del motore di compilazione fornita dall'host.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parametro <xref:Microsoft.Build.Framework.ITaskHost> facoltativo.<br /><br /> Specifica l'istanza dell'oggetto host \(può essere null\).  Il motore di compilazione imposta questa proprietà se l'IDE dell'host ha un oggetto host associato con questa particolare attività.|  
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Parametro di sola lettura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facoltativo.<br /><br /> Ottiene un oggetto `TaskLoggingHelperExtension` che contiene i metodi di registrazione delle attività.|  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)