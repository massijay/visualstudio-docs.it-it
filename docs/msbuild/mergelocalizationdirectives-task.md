---
title: "MergeLocalizationDirectives Task | Microsoft Docs"
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
  - "localizing XAML [WPF MSBuild], moving comments and attributes to a separate file"
  - "MergeLocalizationDirectives task [WPF MSBuild], parameters"
  - "MergeLocalizationDirectives task [WPF MSBuild]"
  - "moving localization comments and attributes to a separate file [WPF MSBuild]"
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MergeLocalizationDirectives Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> unisce i commenti e gli attributi di localizzazione di uno o più file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in un singolo file per l'intero assembly.  
  
## Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Parametro **ITaskItem\[\]** obbligatorio.<br /><br /> Specifica l'elenco di file delle direttive di localizzazione per i singoli file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputFile`|Parametro di output **String** obbligatorio.<br /><br /> Specifica il percorso di output dell'assembly compilato delle direttive di localizzazione.|  
  
## Note  
 È possibile aggiungere commenti e attributi di localizzazione al contenuto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)].  Con il supporto di localizzazione [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)], è possibile rimuovere i commenti e gli attributi di localizzazione e inserirli in un file .loc separato dall'assembly generato.  È possibile eseguire questa operazione utilizzando l'attributo **LocalizationPropertyStorage**.  Per ulteriori informazioni sui commenti e gli attributi di localizzazione e su **LocalizationPropertyStorage**, vedere [Attributi e commenti di localizzazione](../Topic/Localization%20Attributes%20and%20Comments.md).  
  
## Esempio  
 Nell'esempio riportato di seguito vengono uniti i commenti di localizzazione di diversi file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in un unico file con estensione loc.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## Vedere anche  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)