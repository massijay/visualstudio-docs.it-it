---
title: "FormatVersion Task | Microsoft Docs"
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
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# FormatVersion Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aggiunge il numero di revisione al numero di versione.  
  
-   Caso 1: Input: Version\=\<undefined\>;  Revision\=\<don't care\>;   Output: OutputVersion\="1.0.0.0"  
  
-   Caso 2: Input: Version\="1.0.0.\*"  Revision\="5"  Output: OutputVersion\="1.0.0.5"  
  
-   Caso 3: Input: Version\="1.0.0.0"  Revision\=\<don't care\>;  Output: OutputVersion\="1.0.0.0"  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `FormatVersion`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`FormatType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di formato.<br /><br /> -   "Version" \= versione.<br />-   "Path" \= sostituire "." con "\_";|  
|`OutputVersion`|Parametro di output `String` facoltativo.<br /><br /> Specifica la versione di output nella quale è incluso il numero di revisione.|  
|`Revision`|Parametro `Int32` facoltativo.<br /><br /> Specifica la revisione alla quale accodare la versione.|  
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa del numero di versione da formattare.|  
  
## Note  
 Oltre a disporre dei parametri elencati nella tabella, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)