---
title: "FindInList Task | Microsoft Docs"
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
helpviewer_keywords: 
  - "FindInList task [MSBuild]"
  - "MSBuild, FindInList task"
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# FindInList Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In un elenco specificato cerca un elemento con itemspec corrispondente.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività [FindInList Task](../msbuild/findinlist-task.md).  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`CaseSensitive`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, per la ricerca verrà applicata la distinzione tra maiuscole e minuscole; in caso contrario, tale distinzione non verrà applicata.  Il valore predefinito è `true`.|  
|`FindLastMatch`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene restituita l'ultima corrispondenza; in caso contrario, viene restituita la prima corrispondenza.  Il valore predefinito è `false`.|  
|`ItemFound`|Parametro di output di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Primo elemento corrispondente individuato nell'elenco, se disponibile.|  
|`ItemSpecToFind`|Parametro `String` obbligatorio.<br /><br /> itemspec da cercare.|  
|`List`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Elenco nel quale cercare l'itemspec.|  
|`MatchFileNameOnly`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, la corrispondenza si riferisce solo alla parte del nome file dell'itemspec; in caso contrario, si riferisce a tutto l'itemspec.  Il valore predefinito è `true`.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)