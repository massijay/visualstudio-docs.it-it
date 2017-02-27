---
title: "VCMessage Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.vcmessage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "VCMessage task (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), VCMessage task"
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# VCMessage Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Avviso dei log e messaggi di errore durante una compilazione.  
  
## Note  
 Questa attività aiuta a implementare MSBuild per Visual C\+\+ e non deve essere chiamata dall'utente.  Per ulteriori informazioni, vedere <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività **VCMessage** .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Arguments**|Parametro **String** facoltativo.<br /><br /> Un elenco delimitato da punti e virgola di messaggi da visualizzare.|  
|**Code**|Parametro **String** obbligatorio.<br /><br /> Un numero di errore che qualifica il messaggio.|  
|**Type**|Parametro **String** facoltativo.<br /><br /> Specifica il tipo di messaggio da generare.  Specificare `"Avviso"` per generare un messaggio di avviso o `"Errore"` per generare un messaggio di errore.|  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)