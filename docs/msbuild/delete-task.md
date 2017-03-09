---
title: "Delete Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Delete"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Delete task [MSBuild]"
  - "MSBuild, Delete task"
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Delete Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elimina i file specificati.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `Delete`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`DeletedFiles`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i file eliminati.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica i file da eliminare.|  
|`TreatErrorsAsWarnings`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, gli errori vengono registrati come avvisi.  Il valore predefinito è `false`.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene eliminato il file `MyApp.pdb`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <AppName>MyApp</AppName>  
    </PropertyGroup>  
  
    <Target Name="DeleteFiles">  
        <Delete Files="$(AppName).pdb" />  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)