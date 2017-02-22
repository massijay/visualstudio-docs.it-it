---
title: "GetFrameworkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkPath task [MSBuild]"
  - "MSBuild, GetFrameworkPath task"
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetFrameworkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera il percorso degli assembly [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `GetFrameworkPath`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso degli assembly di .NET Framework 1.1, se presenti.  In caso contrario, restituisce `null`.|  
|`FrameworkVersion20Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso degli assembly di .NET Framework 2.0, se presenti.  In caso contrario, restituisce `null`.|  
|`FrameworkVersion30Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso degli assembly di .NET Framework 3.0, se presenti.  In caso contrario, restituisce `null`.|  
|`FrameworkVersion35Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso degli assembly di .NET Framework 3.5, se presenti.  In caso contrario, restituisce `null`.|  
|`FrameworkVersion40Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso degli assembly di .NET Framework 4.0, se presenti.  In caso contrario, restituisce `null`.|  
|`Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso degli assembly di .NET Framework più recenti, se disponibili.  In caso contrario, restituisce `null`.|  
  
## Note  
 Se sono installate più versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], viene restituita la versione su cui [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] è stato progettato per essere eseguito.  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `GetFrameworkPath` viene utilizzata per memorizzare il percorso di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] nella proprietà `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)