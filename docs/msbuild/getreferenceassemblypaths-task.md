---
title: "GetReferenceAssemblyPaths Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# GetReferenceAssemblyPaths Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Restituisce i percorsi dell'assembly di riferimento dei vari framework.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `GetReferenceAssemblyPaths`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parametro di output `String[]` facoltativo.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`.  Se l'oggetto `TargetFrameworkMoniker` è null oppure vuoto, questo percorso sarà `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parametro di output `String[]` facoltativo.<br /><br /> Restituisce il percorso, in base al parametro `TargetFrameworkMoniker`, senza considerare la parte del profilo del moniker.  Se l'oggetto `TargetFrameworkMoniker` è null oppure vuoto, questo percorso sarà `String.Empty`.|  
|`TargetFrameworkMoniker`|Parametro `String` facoltativo.<br /><br /> Specifica il moniker della versione di .NET Framework di destinazione associata ai percorsi degli assembly di riferimento.|  
|`RootPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso radice da utilizzare per generare il percorso dell'assembly di riferimento.|  
|`BypassFrameworkInstallChecks`|Parametro [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) facoltativo.<br /><br /> Se `true`, vengono ignorati i controlli di base eseguiti per impostazione predefinita tramite `GetReferenceAssemblyPaths` per assicurarsi che siano installati determinati framework di runtime, a seconda del framework di destinazione.|  
|`TargetFrameworkMonikerDisplayName`|Parametro di output `String` facoltativo.<br /><br /> Specifica il nome visualizzato per il moniker della versione di .NET Framework di destinazione.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)