---
title: "SGen Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#SGen"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "SGen task [MSBuild]"
  - "MSBuild, SGen task"
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SGen Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Crea un assembly di serializzazione XML per i tipi presenti nell'assembly specificato.  Questa attività incapsula lo strumento XML Serializer Generator Tool \(Sgen.exe\).  Per ulteriori informazioni, vedere [Strumento per la generazione di serializzatori XML \(Sgen.exe\)](../Topic/XML%20Serializer%20Generator%20Tool%20\(Sgen.exe\).md).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `SGen`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`BuildAssemblyName`|Parametro `String` obbligatorio.<br /><br /> Assembly per il quale generare il codice di serializzazione.|  
|`BuildAssemblyPath`|Parametro `String` obbligatorio.<br /><br /> Percorso dell'assembly per il quale generare il codice di serializzazione.|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, specifica che si desidera ottenere un assembly firmato completamente.  Se è impostato su `false`, specifica che si desidera inserire nell'assembly solo la chiave pubblica.<br /><br /> Questo parametro ha effetto soltanto se viene utilizzato con il parametro `KeyFile` o `KeyContainer`.|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore che contiene una coppia di chiavi.  In questo modo l'assembly verrà firmato inserendo una chiave pubblica nel relativo manifesto.  L'assembly finale verrà quindi firmato con la chiave privata.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica una coppia di chiavi o una chiave pubblica da utilizzare per firmare un assembly.  Durante la compilazione la chiave pubblica verrà inserita nel manifesto dell'assembly, mentre l'assembly finale verrà firmato con la chiave privata.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta la piattaforma del compilatore utilizzata per generare l'assembly di output.  Il parametro può essere impostato su `x86`, `x64` o `anycpu`.  Il valore predefinito è `anycpu`.|  
|`References`|Parametro `String[]` facoltativo.<br /><br /> Specifica gli assembly a cui fanno riferimento i tipi che richiedono la serializzazione XML.|  
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio resgen.exe.|  
|`SerializationAssembly`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'assembly di serializzazione generato.|  
|`SerializationAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'assembly di serializzazione generato.|  
|`ShouldGenerateSerializer`|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, tramite l'attività SGen dovrebbe essere generato un assembly di serializzazione.|  
|`Timeout`|Parametro `Int32` facoltativo.<br /><br /> Specifica l'intervallo di tempo, in millisecondi, al termine del quale l'eseguibile dell'attività verrà interrotto.  Il valore predefinito è `Int.MaxValue`, con cui viene indicato che non è stato specificato alcun periodo di timeout.|  
|`ToolPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso da cui l'attività carica il file eseguibile sottostante \(sgen.exe\).  Se questo parametro non è specificato, viene utilizzato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Types`|Parametro `String[]` facoltativo.<br /><br /> Ottiene o imposta un elenco di tipi specifici per i quali generare il codice di serializzazione.  Tramite SGen viene generato il codice di serializzazione solo per questi tipi.|  
|`UseProxyTypes`|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, tramite l'attività SGen viene generato il codice di serializzazione solo per i tipi proxy del servizio Web XML.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [MSBuild Concepts](../msbuild/msbuild-concepts.md)