---
title: "Procedura: individuare il nome del processo ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "debug ASP.NET, processo ASP.NET"
  - "processo ASP.NET"
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: individuare il nome del processo ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per connettersi a un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in esecuzione, è necessario conoscere il nome del processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
-   Se si esegue IIS 6.0 o IIS 7.0, il nome sarà w3wp.exe.  
  
-   Se si esegue una versione precedente di IIS, il nome sarà invece aspnet\_wp.exe.  
  
 Per applicazioni compilate utilizzando [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] o versioni successive, il codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] può risiedere nel file system ed essere eseguito sul server di prova WebDev.WebServer.exe.  In tal caso, è necessario connettersi a WebDev.WebServer.exe anziché al processo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Questo scenario è valido solo per il debug locale.  
  
 Le applicazioni ASP più obsolete vengono eseguite nel processo IIS inetinfo.exe quando sono in esecuzione all'interno del processo.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per determinare se il codice di progetto risiede nel file system o in IIS  
  
1.  In Visual Studio, aprire **Esplora soluzioni**, se non è già aperto.  
  
2.  Selezionare il nodo superiore che contiene il nome dell'applicazione.  
  
3.  Se il titolo della finestra **Proprietà** contiene un percorso di file, il codice dell'applicazione risiede nel file system.  
  
     In caso contrario, il titolo della finestra **Proprietà** conterrà il nome del sito Web.  
  
### Per determinare la versione di IIS in cui l'applicazione è in esecuzione  
  
1.  Individuare **Strumenti di amministrazione** ed eseguirlo.  In base al sistema operativo, potrebbe essere un'icona all'interno del **Pannello di controllo** o una voce di menu visibile quando si fa clic su **Start**.  
  
     In Windows XP il **Pannello di controllo** può essere disponibile nella visualizzazione classica o per categoria.  Nella visualizzazione per categorie è necessario scegliere **Passa alla visualizzazione classica** o **Prestazioni e manutenzione** per visualizzare l'icona **Strumenti di amministrazione**.  
  
2.  Da **Strumenti di amministrazione** eseguire Internet Information Services.  Viene visualizzata una finestra di dialogo MMC.  
  
3.  Se nel riquadro sinistro sono elencati più computer, selezionare quello in cui risiede il codice dell'applicazione.  
  
4.  La versione di IIS è indicata nella colonna **Versione** del riquadro destro.  
  
## Vedere anche  
 [Prerequisiti per il debug remoto di applicazioni Web](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Preparazione al debug di ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)