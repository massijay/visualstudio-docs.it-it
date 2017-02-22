---
title: "ResolveKeySource Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ResolveKeySource task [MSBuild]"
  - "MSBuild, ResolveKeySource task"
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResolveKeySource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina l'origine delle chiavi con nome sicuro.  
  
## Parametri dell'attività  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `ResolveKeySource`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AutoClosePasswordPromptShow`|Parametro `Int32` facoltativo.<br /><br /> Ottiene o imposta il periodo di tempo, in secondi, per la visualizzazione del messaggio di conto alla rovescia.|  
|`AutoClosePasswordPromptTimeout`|Parametro `Int32` facoltativo.<br /><br /> Ottiene o imposta il periodo di tempo, in secondi, di attesa prima della chiusura della finestra di dialogo di richiesta della password.|  
|`CertificateFile`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta il percorso del file di certificato.|  
|`CertificateThumbprint`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta l'identificazione digitale del certificato.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Ottiene o imposta il percorso del file di chiave.|  
|`ResolvedKeyContainer`|Parametro di output `String` facoltativo.<br /><br /> Ottiene o imposta il contenitore di chiavi risolto.|  
|`ResolvedKeyFile`|Parametro di output `String` facoltativo.<br /><br /> Ottiene o imposta il file di chiave risolto.|  
|`ResolvedThumbprint`|Parametro di output `String` facoltativo.<br /><br /> Ottiene o imposta l'identificazione digitale del certificato risolto.|  
|`ShowImportDialogDespitePreviousFailures`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, viene mostrata la finestra di dialogo di importazione nonostante gli errori precedenti.|  
|`SuppressAutoClosePasswordPrompt`|Parametro `Boolean` facoltativo.<br /><br /> Ottiene o imposta un valore booleano che specifica se la finestra di dialogo di richiesta della password non deve chiudersi automaticamente.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)