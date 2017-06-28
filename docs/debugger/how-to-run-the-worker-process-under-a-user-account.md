---
title: "Procedura: eseguire il processo di lavoro con un account utente | Microsoft Docs"
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
  - "account utente, aspnet_wp.exe"
  - "Il debug di applicazioni Web ASP.NET,"
  - "strumenti, aspnet_wp.exe"
  - "ASP.NET, strumenti"
  - "aspnet_wp.exe"
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il processo di lavoro con un account utente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per configurare il computer in modo da poter eseguire processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] (aspnet_wp.exe o w3wp.exe) con un account utente, attenersi alla procedura riportata di seguito.  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Per eseguire aspnet_wp.exe con un account utente  
  
1.  Aprire il file machine.config, che si trova sul computer nella cartella CONFIG, nel percorso in cui è stato installato l'ambiente runtime.  
  
2.  Trovare il &lt;processModel&gt; sezione e modificare gli attributi utente e password specificando il nome e la password dell'account utente desiderato aspnet_wp.exe venga eseguito.  
  
3.  Salvare il file machine.config.  
  
4.  In [!INCLUDE[winxpsvr](../debugger/includes/winxpsvr_md.md)]IIS 6.0 è installato per impostazione predefinita. Il processo di lavoro corrispondente è w3wp.exe. Per eseguirlo in modalità IIS 6.0 con aspnet_wp.exe come processo di lavoro, è necessario attenersi alla procedura riportata di seguito:  
  
    1.  Fare clic sul pulsante **Start**, scegliere **Strumenti di amministrazione** e infine **Internet Information Services**.  
  
    2.  Nella finestra di dialogo **Internet Information Services** , fare clic con il pulsante destro del mouse sulla cartella **Siti Web** e scegliere **Proprietà**.  
  
    3.  Nella finestra di dialogo **Proprietà siti Web** scegliere **Servizio**.  
  
    4.  Selezionare **Esegui il servizio WWW in modalità isolamento IIS 6.0**.  
  
    5.  Chiudere la finestra di dialogo **Proprietà** e **Gestione servizi Internet**.  
  
5.  Aprire un prompt dei comandi di Windows e reimpostare il server eseguendo:  
  
    ```  
    iisreset  
    ```  
    oppure  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6.  Individuare la cartella dei file temporanei di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , che dovrebbe trovarsi nello stesso percorso della cartella CONFIG. Fare clic con il pulsante destro del mouse sulla cartella dei file temporanei di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , quindi scegliere **Proprietà** dal menu di scelta rapida.  
  
7.  Nella finestra di dialogo **Proprietà file ASP.NET temporanei** scegliere la scheda **Sicurezza** .  
  
8.  Scegliere **Avanzate**.  
  
9. Nella finestra di dialogo **Impostazioni avanzate di sicurezza per file ASP.Net temporanei** fare clic sul pulsante **Aggiungi**.  
  
    Verrà visualizzata la finestra di dialogo per la selezione di utenti, computer o gruppi **** .  
  
10. Digitare il nome utente nella casella **Immettere il nome dell'oggetto da selezionare** quindi scegliere **OK**. Il nome utente deve seguire il formato NomeDominio\NomeUtente.  
  
11. Nella finestra di dialogo **Voce di autorizzazione per file ASP.NET temporanei** , assegnare all'utente **Controllo completo**, quindi scegliere **OK** per chiudere la finestra di dialogo **Voce di autorizzazione per file ASP.NET temporanei** .  
  
12. Verrà visualizzata la finestra di dialogo **Sicurezza** , in cui verrà chiesto di confermare la modifica delle autorizzazioni in una cartella di sistema. Scegliere **Sì**.  
  
13. Scegliere **OK** per chiudere la finestra di dialogo **Proprietà file ASP.NET temporanei** .  
  
## <a name="see-also"></a>Vedere anche  
[Debug di ASP.NET: Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)  
  