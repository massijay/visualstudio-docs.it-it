---
title: "Prerequisiti per il debug remoto di applicazioni Web | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug di applicazioni Web ASP.NET, server remoti"
  - "debug remoto, prerequisiti"
  - "server remoti, debug di applicazioni Web"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prerequisiti per il debug remoto di applicazioni Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debugger [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di eseguire il debug di un'applicazione Web in modo trasparente nel computer locale o in un server remoto.  Il debugger funziona nello stesso modo e consente di utilizzare le stesse funzionalità in entrambi i computer.  Esistono tuttavia alcuni prerequisiti per la corretta esecuzione del debug remoto.  
  
-   I componenti per il debug remoto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] devono essere installati nel server di cui si desidera eseguire il debug.  Per ulteriori informazioni, vedere [Impostazione del debug remoto](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
-   Per impostazione predefinita, il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] viene eseguito come processo utente ASPNET.  Di conseguenza, per eseguire il debug è necessario disporre dei privilegi di amministratore per il computer in cui viene eseguito [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Il nome del processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] varia in base allo scenario di debug e alla versione di IIS.  Per ulteriori informazioni, vedere [Procedura: individuare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)