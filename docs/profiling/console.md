---
title: "Console | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Console** di VSPerfCmd.exe avvia l'applicazione specificata in una nuova finestra del prompt dei comandi.  **Console** può essere utilizzata solo con l'opzione **Launch** di VSPerfCmd.  Se l'applicazione non è un'applicazione della riga di comando, **Console** non ha alcun effetto.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### Parametri  
 Nessuno  
  
## Opzioni obbligatorie  
 L'opzione **Console** può essere specificata unicamente in una riga di comando che contiene anche l'opzione **Launch**.  
  
 **Launch:** `AppName`  
 Avvia il profiler e l'applicazione specificata da `AppName`.  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)