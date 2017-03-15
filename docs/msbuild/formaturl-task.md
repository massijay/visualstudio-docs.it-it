---
title: "FormatUrl Task | Microsoft Docs"
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
  - "MSBuild, FormatUrl task"
  - "FormatUrl task [MSBuild]"
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatUrl Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Converte un URL in un formato URL corretto.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `FormatUrl`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`InputUrl`|Parametro `String` facoltativo.<br /><br /> Specifica l'URL da formattare.|  
|`OutputUrl`|Parametro di output `String` facoltativo.<br /><br /> Specifica l'URL formattato.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)