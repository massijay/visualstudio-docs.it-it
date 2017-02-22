---
title: "SetEnv Task | Microsoft Docs"
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
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), tasks"
  - "SetEnv task (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# SetEnv Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Imposta o elimina il valore di una variabile di ambiente specificata.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività **SetEnv** .  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|**Name**|Parametro **String** obbligatorio.<br /><br /> Nome di una variabile di ambiente.|  
|**OutputEnvironmentVariable**|Parametro di output **String** facoltativo.<br /><br /> Contiene il valore assegnato alla variabile di ambiente specificata dal parametro **Name**.|  
|**Prefix**|Parametro `Boolean` obbligatorio.<br /><br /> Se `true`, concatena il valore del parametro **Value** prima della variabile di ambiente specificata dal parametro **Name** e assegna il risultato alla variabile di ambiente.  Se `false`, assegna solo il valore del parametro **Value** alla  variabile di ambiente.|  
|**Target**|Parametro **String** facoltativo.<br /><br /> Specifica il percorso in cui viene archiviata una variabile di ambiente.  Specificare "`Utente`" o "`Computer`".<br /><br /> Per ulteriori informazioni, vedere "EnvironmentVariableTarget Enumeration" sul sito Web di [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Value**|Parametro **String** facoltativo.<br /><br /> Valore assegnato alla variabile di ambiente specificata dal parametro **Name**.  Se **Value** è vuoto e la variabile esiste, tale variabile sarà eliminata.  Se la variabile non esiste, non si verificherà alcun errore, anche se non è possibile eseguire l'operazione.<br /><br /> Per ulteriori informazioni, vedere "Environment::SetEnvironmentVariable Method" sul sito Web di  [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Note  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)