---
title: "GenerateTemporaryTargetAssembly Task | Microsoft Docs"
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
  - "build process [WPF MSBuild], XAML page refers to a locally declared type"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild]"
  - "GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters"
  - "creating an assembly [WPF MSBuild], XAML page refers to a locally declared type"
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateTemporaryTargetAssembly Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> genera un assembly se almeno una pagina [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] in un progetto fa riferimento a un tipo dichiarato localmente in tale progetto.  L'assembly generato viene rimosso dopo il completamento del processo di compilazione o in caso di suo esito negativo.  
  
## Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssemblyName`|Parametro **String** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto ed è anche il nome dell'assembly di destinazione generato temporaneamente.  Ad esempio, se un progetto genera un eseguibile [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] il cui nome è **WinExeAssembly.exe**, il parametro **AssemblyName** presenterà il valore **WinExeAssembly**.|  
|`CompileTargetName`|Parametro **String** obbligatorio.<br /><br /> Specifica il nome della destinazione [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] utilizzata per generare assembly dai file di codice sorgente.  Il valore tipico per **CompileTargetName** è **CoreCompile**.|  
|`CompileTypeName`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di compilazione eseguito dalla destinazione specificata dal parametro **CompileTargetName**.  Per la destinazione **CoreCompile**, questo valore è **Compile**.|  
|`CurrentProject`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso completo del file di progetto [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] per il progetto che richiede un assembly di destinazione temporaneo.|  
|`GeneratedCodeFiles`|Parametro **ITaskItem\[\]** facoltativo.<br /><br /> Specifica l'elenco di file di codice gestito specifici del linguaggio generati dall'attività [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md).|  
|`IntermediateOutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui viene generato l'assembly di destinazione temporaneo.|  
|`MSBuildBinPath`|Parametro **String** obbligatorio.<br /><br /> Specifica il percorso di **MSBuild.exe**, necessario per compilare l'assembly di destinazione temporaneo.|  
|`ReferencePath`|Parametro **ITaskItem\[\]** facoltativo.<br /><br /> Specifica un elenco di assembly, per percorso e nome file, a cui viene fatto riferimento dai tipi compilati nell'assembly di destinazione temporaneo.|  
|`ReferencePathTypeName`|Parametro **String** obbligatorio.<br /><br /> Specifica il parametro utilizzato dal parametro di destinazione della compilazione \(**CompileTargetName**\), che specifica l'elenco di riferimenti ad assembly \(**ReferencePath**\).  Il valore appropriato è **ReferencePath**.|  
  
## Note  
 Il primo passaggio di compilazione del markup, eseguito dall'[MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), compila i file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario.  Di conseguenza, il compilatore necessita di un elenco degli assembly a cui si fa riferimento che contengono i tipi utilizzati dai file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  Tuttavia, se un file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] utilizza un tipo definito nello stesso progetto, non verrà creato un assembly corrispondente per tale progetto fino a quando quest'ultimo non viene compilato.  Pertanto, non sarà possibile fornire un riferimento all'assembly durante il primo passaggio di compilazione del markup.  
  
 Invece **MarkupCompilePass1** rinvia la conversione dei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] che contengono riferimenti ai tipi nello stesso progetto a un secondo passaggio di compilazione del markup, eseguito dall'[MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  Prima dell'esecuzione di **MarkupCompilePass2**, verrà generato un assembly temporaneo.  Questo assembly contiene i tipi utilizzati dai file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] il cui passaggio di compilazione del markup è stato rinviato.  Un riferimento all'assembly generato viene fornito a **MarkupCompilePass2** durante l'esecuzione, per consentire la conversione in formato binario dei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] con compilazione rinviata.  
  
## Esempio  
 Nell'esempio riportato di seguito viene generato un assembly temporaneo poiché `Page1.xaml` contiene un riferimento a un tipo che si trova nello stesso progetto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
  </Target>  
</Project>  
```  
  
## Vedere anche  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Panoramica delle applicazioni browser XAML di WPF](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)