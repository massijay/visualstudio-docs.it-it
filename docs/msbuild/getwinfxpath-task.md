---
title: "GetWinFXPath Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "getting the directory of the current .NET Framework runtime [WPF MSBuild]"
  - "GetWinFXPath task [WPF MSBuild], parameters"
  - "GetWinFXPath task [WPF MSBuild]"
  - "obtaining the path to the current .NET Framework runtime [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetWinFXPath Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> restituisce la directory del runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] corrente.  
  
## Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`WinFXPath`|Parametro di output **String** facoltativo.<br /><br /> Specifica il percorso reale del runtime [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso del runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] nativo.|  
|`WinFXWowPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso degli assembly [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] nel modulo **Windows on Windows** a 32 bit nei sistemi a 64 bit.|  
  
## Note  
 Se l'attività <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> viene eseguita su un processore a 64 bit, il parametro **WinFXPath** verrà impostato sul percorso archiviato nel parametro **WinFXWowPath**; in caso contrario, il parametro **WinFXPath** verrà impostato sul percorso archiviato nel parametro **WinFXNativePath**.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'attività **GetWinFXPath** per individuare il percorso nativo del runtime [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## Vedere anche  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)