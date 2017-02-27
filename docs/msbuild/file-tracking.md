---
title: "File Tracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, file tracking"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# File Tracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il rilevamento di file registra le chiamate al file system di Windows per un processo e i relativi processi figlio.  Chiamando le funzioni elencate di seguito, i programmi controllano quando è necessario attivare e disattivare la registrazione e specificano il file di log da utilizzare.  
  
## In questa sezione  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Arresta il rilevamento del contesto corrente.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Riprende il rilevamento dopo una chiamata a [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Imposta il numero di thread da utilizzare per il rilevamento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Inizia un nuovo contesto di rilevamento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Inizia un nuovo contesto di rilevamento con una radice specificata.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Termina il rilevamento e rilascia le risorse utilizzate.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Sospende temporaneamente il rilevamento.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Scrive i log di rilevamento per tutti i contesti.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Scrive il log di rilevamento per il contesto corrente.