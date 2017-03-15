---
title: "GenerateTrustInfo Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "MSBuild, GenerateTrustInfo task"
  - "GenerateTrustInfo task [MSBuild]"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GenerateTrustInfo Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Genera l'attendibilità dell'applicazione dal manifesto di base e dai parametri `TargetZone` e `ExcludedPermissions`.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `GenerateTrustInfo`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ApplicationDependencies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica gli assembly dipendenti.|  
|`BaseManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il manifesto di base da cui generare l'attendibilità dell'applicazione.|  
|`ExcludedPermissions`|Parametro `String` facoltativo.<br /><br /> Specifica uno o più valori di identità di autorizzazione separati da punto e virgola da escludere dal set di autorizzazioni predefinito per l'area.|  
|`TargetZone`|Parametro `String` facoltativo.<br /><br /> Specifica un set di autorizzazioni predefinito per l'area, ottenuto dai criteri del computer.|  
|`TrustInfoFile`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il file in cui sono contenute le informazioni di attendibilità di sicurezza dell'applicazione.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)