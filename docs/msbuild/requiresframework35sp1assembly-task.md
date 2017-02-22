---
title: "RequiresFramework35SP1Assembly Task | Microsoft Docs"
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
  - "RequiresFramework35SP1Assembly task [MSBuild]"
  - "MSBuild, RequiresFramework35SP1Assembly task"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# RequiresFramework35SP1Assembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina se l'applicazione richiede .NET Framework 3.5 SP1.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `RequiresFramework35SP1Assembly`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Assemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly a cui viene fatto riferimento nell' applicazione.|  
|`CreateDesktopShortcut`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene creata un'icona di collegamento sul desktop durante l'installazione.|  
|`DeploymentManifestEntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome file del manifesto per l'applicazione.|  
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica l'assembly da eseguire quando viene eseguita l'applicazione.|  
|`ErrorReportUrl`|Parametro `String` facoltativo.<br /><br /> Specifica il sito Web mostrato nelle finestre di dialogo visualizzate durante le installazioni ClickOnce.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elenco dei file che saranno distribuiti quando viene pubblicata l'applicazione.|  
|`ReferencedAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly a cui viene fatto riferimento nel progetto.|  
|`RequiresMinimumFramework35SP1`|Parametro di output `Boolean` facoltativo.<br /><br /> Se `true`, per l'applicazione è richiesto .NET Framework 3.5 SP1.|  
|`SigningManifests`|Parametro di output `Boolean` facoltativo.<br /><br /> Se `true`, i manifesti ClickOnce sono firmati.|  
|`SuiteName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome della cartella del menu **Start** in cui verrà installata l'applicazione.|  
|`TargetFrameworkVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione di .NET Framework di destinazione per questa applicazione.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)