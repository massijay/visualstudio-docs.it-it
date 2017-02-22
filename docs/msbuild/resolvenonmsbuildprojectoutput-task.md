---
title: "ResolveNonMSBuildProjectOutput Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "MSBuild, ResolveNonMSBuildProjectOutput task"
  - "ResolveNonMSBuildProjectOutput task [MSBuild]"
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveNonMSBuildProjectOutput Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina i file di output per riferimenti a progetti non MSBuild.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `ResolveNonMSBuildProjectOutput`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa XML contenente gli output di progetto risolti.|  
|`ProjectReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]`  obbligatorio.<br /><br /> Specifica i riferimenti al progetto.|  
|`ResolvedOutputPaths`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di percorsi di riferimento risolti \(e conserva gli attributi di riferimento al progetto originali\).|  
|`UnresolvedProjectReferences`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene l'elenco di elementi di riferimento al progetto che non è possibile risolvere utilizzando l'elenco prerisolto di output.<br /><br /> Poiché in Visual Studio vengono prerisolti unicamente i progetti non MSBuild, i riferimenti ai progetti riportati in questo elenco sono in formato MSBuild.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)