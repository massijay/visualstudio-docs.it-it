---
title: "AspNetCompiler Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AspNetCompiler task"
  - "AspNetCompiler task [MSBuild]"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AspNetCompiler Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività `AspNetCompiler` esegue il wrapping di aspnet\_compiler.exe, un'utilità che consente la precompilazione di applicazioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `AspNetCompiler`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'assembly con nome sicuro consente chiamanti parzialmente attendibili.|  
|`Clean`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, verrà eseguita la pulitura dell'applicazione precompilata.  Tutti i componenti precedentemente compilati verranno ricompilati.  Il valore predefinito è `false`.  Questo parametro corrisponde all'opzione **\-c** di aspnet\_compiler.exe.|  
|`Debug`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, le informazioni di debug \(file pdb\) vengono generate durante la compilazione.  Il valore predefinito è `false`.  Questo parametro corrisponde all'opzione **\-d** di aspnet\_compiler.exe.|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, l'assembly non viene firmato completamente quando viene creato.|  
|`FixedNames`|Parametro `Boolean` facoltativo.<br /><br /> Se questo parametro è `true`, agli assembly compilati verrà assegnato un nome fisso.|  
|`Force`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, la directory di destinazione, se già presente, verrà sovrascritta.  Il contenuto esistente andrà perduto.  Il valore predefinito è `false`.  Questo parametro corrisponde all'opzione **\-f** di aspnet\_compiler.exe.|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore della chiave con nome sicuro.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico del file di chiave con nome sicuro.|  
|`MetabasePath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso completo della metabase IIS dell'applicazione.  Non è possibile combinare questo parametro con il parametro `VirtualPath` o `PhysicalPath`.  Questo parametro corrisponde all'opzione **\-m** di aspnet\_compiler.exe.|  
|`PhysicalPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico dell'applicazione da compilare.  Se questo parametro non è specificato, la metabase IIS viene utilizzata per individuare l'applicazione.  Questo parametro corrisponde all'opzione **\-p** di aspnet\_compiler.exe.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica l'elemento TargetFrameworkMoniker tramite il quale viene indicata la versione di .NET Framework del file aspnet\_compiler.exe da utilizzare.  Accetta solo moniker di .NET Framework.|  
|`TargetPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso fisico in cui viene eseguita la compilazione dell'applicazione.  Se questo parametro non è specificato, l'applicazione viene precompilata sul posto.|  
|`Updateable`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, l'applicazione precompilata risulterà aggiornabile.  Il valore predefinito è `false`.  Questo parametro corrisponde all'opzione **\-u** di aspnet\_compiler.exe.|  
|`VirtualPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso virtuale dell'applicazione da compilare.  Se il parametro `PhysicalPath` è specificato, il percorso fisico viene utilizzato per individuare l'applicazione.  In caso contrario, viene utilizzata la metabase IIS e si presuppone che l'applicazione sia disponibile nel sito predefinito.  Questo parametro corrisponde all'opzione **\-v** di aspnet\_compiler.exe.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Esempio  
 Nell'esempio di codice riportato di seguito l'attività `AspNetCompiler` viene utilizzata per precompilare un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)