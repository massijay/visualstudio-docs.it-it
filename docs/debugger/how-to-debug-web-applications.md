---
title: "Procedura: eseguire il debug di applicazioni Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Web Form ASP.NET, debug"
  - "ASP.NET, debug di applicazioni Web"
  - "debug di applicazioni Web ASP.NET, durante lo sviluppo"
  - "servizi Web, debug"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura: eseguire il debug di applicazioni Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è la tecnologia principale per lo sviluppo di applicazioni Web in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornisce potenti strumenti per il debug di applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a livello locale o su un server remoto.  In questo argomento viene descritto come eseguire il debug di un progetto [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in fase di sviluppo.  Per informazioni su come eseguire il debug di un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] già distribuita su un server di produzione, vedere [Debug di applicazioni Web distribuite](../debugger/debugging-deployed-web-applications.md).  
  
 Per eseguire il debug di un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
-   È necessario disporre delle autorizzazioni richieste.  Per ulteriori informazioni, vedere [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
-   Il debug di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] deve essere attivato in **Proprietà progetto**.  
  
-   Il file di configurazione dell'applicazione \(Web.config\) deve essere impostato sulla modalità debug.  La modalità di debug fa in modo che [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] generi simboli per i file generati dinamicamente e consente al debugger di creare un allegato all'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] configura automaticamente questa impostazione quando si avvia il debug, se il progetto è stato creato dal modello dei progetti Web.  
  
-   Per ulteriori informazioni, vedere [Procedura: attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### Per eseguire il debug di un'applicazione Web durante lo sviluppo  
  
1.  Dal menu **Debug** scegliere **Avvia** per avviare il debug dell'applicazione Web.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila il progetto applicazione Web, distribuisce l'applicazione se necessario, avvia il server di sviluppo ASP.NET se il debug viene eseguito a livello locale e si connette al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Utilizzare il debugger  per impostare e rimuovere punti di interruzione, eseguire singole istruzioni e compiere altre operazioni di debug, come per qualsiasi altra applicazione.  
  
     Per ulteriori informazioni, vedere [Nozioni di base sul debugger](../debugger/debugger-basics.md).  
  
3.  Dal menu **Debug** scegliere **Termina debug** per terminare la sessione di debug; in alternativa, dal menu **File** di Internet Explorer, scegliere **Chiudi**.  
  
## Vedere anche  
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Procedura: attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)