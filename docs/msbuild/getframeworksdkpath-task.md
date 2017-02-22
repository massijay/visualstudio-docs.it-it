---
title: "GetFrameworkSdkPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath task [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath task"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetFrameworkSdkPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera il percorso di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `GetFrameworkSdkPath`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Parametro di output in sola lettura `String` facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 2.0, se presente.  In caso contrario, restituisce `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Parametro di output in sola lettura `String` facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 3.5, se presente.  In caso contrario, restituisce `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Parametro di output in sola lettura `String` facoltativo.<br /><br /> Restituisce il percorso di .NET SDK versione 4.0, se presente.  In caso contrario, restituisce `String.Empty`.|  
|`Path`|Parametro di output `String` facoltativo.<br /><br /> Contiene il percorso della versione più recente di .NET SDK, se presente.  In caso contrario, restituisce `String.Empty`.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `GetFrameworkSdkPath` viene utilizzata per memorizzare il percorso di [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] nella proprietà `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)