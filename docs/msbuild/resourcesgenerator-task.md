---
title: "ResourcesGenerator Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "embedding resources into a .resources file [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild]"
  - "ResourcesGenerator task [WPF MSBuild], parameters"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResourcesGenerator Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incorpora una o più risorse \(.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario e altri tipi di estensione\) in un file .resources.  
  
## Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`OutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso della directory di output.  Se il percorso non è un percorso assoluto, verrà trattato come percorso relativo alla directory di progetto radice.|  
|`OutputResourcesFile`|Parametro di output **ITaskItem\[\]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file .resources generato.  Se il percorso non è un percorso assoluto, verrà generato il file .resources relativo alla directory di progetto radice.|  
|`ResourcesFiles`|Parametro **ITaskItem\[\]** obbligatorio.<br /><br /> Specifica una o più risorse da incorporare nel file con estensione generato.|  
  
## Esempio  
 Nell'esempio riportato di seguito viene generato un file con estensione resources con una sola risorsa con estensione bmp.  La risorsa .bmp viene generata in una directory relativa alla directory radice del progetto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## Vedere anche  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)