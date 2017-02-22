---
title: "Preparazione al debug: applicazioni Web ASP.NET | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "debug [Visual Studio], applicazioni Web"
  - "debug di applicazioni Web ASP.NET"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Preparazione al debug: applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il modello di sito Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] consente di creare un'applicazione Web Form.  Quando si crea un sito Web mediante questo modello, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vengono definite automaticamente le impostazioni predefinite per il debug.  Nella finestra di dialogo **Proprietà progetto** è possibile specificare se si desidera che la pagina Web sia una pagina di avvio.  Quando si avvia il debug di un sito Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]con queste impostazioni predefinite, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene avviato automaticamente Internet Explorer e il debugger viene connesso al processo di lavoro di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(aspnet\_wp.exe o w3wp.exe\).  Per ulteriori informazioni, vedere [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
### Per creare un'applicazione Web Form  
  
1.  Scegliere **Nuovo sito Web** dal menu **File**.  
  
2.  Nella finestra di dialogo **Nuovo sito Web** selezionare **Sito Web** [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
3.  Scegliere **OK**.  
  
### Per eseguire il debug del Web Form  
  
1.  Impostare uno o più punti di interruzione nelle funzioni e nei gestori eventi.  
  
     Per ulteriori informazioni, vedere [Breakpoints and Tracepoints](http://msdn.microsoft.com/it-it/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Quando viene raggiunto un punto di interruzione, eseguire il codice un'istruzione alla volta all'interno della funzione.  Osservare l'esecuzione del codice finché non si individua il problema.  
  
     Per ulteriori informazioni, vedere [Stepping](http://msdn.microsoft.com/it-it/8791dac9-64d1-4bb9-b59e-8d59af1833f9) e [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md).  
  
## Modifica delle configurazioni predefinite  
 Se si desidera, è possibile modificare le configurazioni di debug e di rilascio predefinite create da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere [Procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### Per modificare la configurazione di debug predefinita  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul sito Web e scegliere **Pagine delle proprietà** per visualizzare la finestra di dialogo corrispondente.  
  
2.  Fare clic su **Opzioni di avvio**.  
  
3.  Impostare **Azione di avvio** sulla pagina Web da visualizzare per prima.  
  
4.  In **Debugger** assicurarsi che l'opzione **Debug ASP.NET** sia selezionata.  
  
     Per ulteriori informazioni, vedere [Impostazioni delle pagine delle proprietà per i progetti Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)