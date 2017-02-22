---
title: "ResolveManifestFiles Task | Microsoft Docs"
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
  - "ResolveManifestFiles task [MSBuild]"
  - "MSBuild, ResolveManifestFiles task"
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveManifestFiles Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Risolve i seguenti elementi nel processo di compilazione nei file per la generazione del manifesto: elementi compilati, dipendenze, satelliti, contenuto, simboli di debug e documentazione.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `ResolveManifestFiles`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del manifesto della distribuzione.|  
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il riferimento all'assembly gestito o al manifesto ClickOnce che rappresenta il punto di ingresso del manifesto.|  
|`ExtraFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file aggiuntivi.|  
|`ManagedAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly gestiti.|  
|`NativeAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly nativi.|  
|`OutputAssemblies`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly generati.|  
|`OutputDeploymentManifestEntryPoint`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il punto di ingresso di output del manifesto della distribuzione.|  
|`OutputEntryPoint`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il punto di ingresso dell'output.|  
|`OutputFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file di output.|  
|`PublishFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file da pubblicare.|  
|`SatelliteAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly satellite.|  
|`SigningManifests`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, i manifesti sono firmati.|  
|`TargetCulture`|Parametro `String` facoltativo.<br /><br /> Specifica le impostazioni cultura di destinazione per gli assembly satellite.|  
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework di destinazione.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)