---
title: "LC Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, LC task"
  - "LC task [MSBuild]"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping di LC.exe, uno strumento che genera un file license da un file licx.  Per ulteriori informazioni su LC.exe, vedere [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `LC`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`LicenseTarget`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica l'eseguibile per cui vengono generati i file licenses.|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Evita la visualizzazione del messaggio di avvio Microsoft.|  
|`OutputDirectory`|Parametro `String` facoltativo.<br /><br /> Specifica la directory in cui inserire i file licenses di output.|  
|`OutputLicense`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file licenses.  Se non si specifica un nome, viene utilizzato il nome del file licx e il file licenses viene inserito nella directory contenente il file licx.|  
|`ReferencedAssemblies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i componenti a cui si fa riferimento da caricare durante la generazione del file license.|  
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio resgen.exe.|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli elementi che contengono componenti concessi in licenza da includere nel file licenses.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/complist` di [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).|  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `LC` viene utilizzata per compilare le licenze.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)