---
title: "Procedura: Impostare le autorizzazioni per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilatura, impostazione delle autorizzazioni"
  - "sicurezza [Visual Studio ALM], impostazione delle autorizzazioni"
  - "autorizzazioni [Visual Studio ALM], profilatura"
  - "strumenti per la profilatura, impostazione di autorizzazioni di profilatura"
  - "strumenti per le prestazioni, impostazioni di autorizzazioni di profilatura"
ms.assetid: 69f27896-8f46-4ef3-bfb7-726d95304f3a
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Impostare le autorizzazioni per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene descritto come vengono concesse le autorizzazioni di sicurezza necessarie per la profilatura dall'amministratore di un computer a un utente o un gruppo che non dispone di autorizzazioni di amministratore sul computer.  
  
 Secondo un principio di base della sicurezza, le applicazioni devono essere eseguite con le autorizzazioni strettamente necessarie.  Questo principio vale anche per gli utenti,  ai quali non devono essere concesse le autorizzazioni specifiche degli amministratori se sono in grado di operare in modo efficace con i privilegi del gruppo Utenti anziché queli del gruppo Amministratori.  Nella prima procedura, "Per creare un account utente con autorizzazioni di utente", viene illustrato come creare un account utente per un membro del gruppo Utenti.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 I membri di tale gruppo richiedono l'accesso a cartelle e file presenti sul disco che sono condivisi da altri membri del team.  Nella seconda procedura, "Per concedere l'accesso ai file di progetto condivisi", viene illustrato come garantire questo tipo di accesso.  
  
 I membri del gruppo Utenti possono eseguire gli strumenti di profilatura se viene loro concesso di accedere al driver software di tali strumenti.  Nell'ultima procedura, "Per concedere l'accesso al driver per la creazione di profili", viene illustrato come garantire accesso al driver in questione.  
  
> [!NOTE]
>  Per eseguire le operazioni contenute nelle procedure indicate di seguito sono necessarie autorizzazioni di amministratore.  
  
### Per creare un account utente con autorizzazioni di utente  
  
1.  Fare clic con il pulsante destro del mouse su **Risorse del computer** e quindi scegliere **Gestione**.  
  
     Verrà aperta la finestra **Gestione computer**.  
  
2.  Espandere **Utenti e gruppi locali**.  
  
3.  Fare clic sulla cartella **Utenti** con il pulsante destro del mouse e quindi scegliere **Nuovo utente**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo utente**.  
  
4.  Inserire nei campi della finestra di dialogo le informazioni relative all'account utente creato.  Specificare una password.  Facoltativamente, selezionare la casella di controllo che richiede all'utente la modifica della password al successivo accesso.  
  
5.  Fare clic su **Crea** e quindi su **Chiudi**.  
  
     Il nuovo utente verrà visualizzato nel gruppo Utenti, ovvero un gruppo di utenti che non dispone di autorizzazioni di amministratore.  
  
### Per concedere l'accesso ai file di progetto condivisi  
  
1.  In Esplora risorse individuare la cartella radice della struttura ad albero di cartelle relativa ai file di progetto utilizzati dall'utente e condivisi dal team del progetto.  
  
     Il percorso della cartella potrebbe essere simile al seguente:  
  
    ```  
    D:\ourProject  
    ```  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella e quindi scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Proprietà \<nome della cartella\>**.  
  
3.  Fare clic sulla scheda **Sicurezza**.  
  
4.  Fare clic sul nome dell'account utente nella casella **Utenti e gruppi**.  
  
5.  Nel riquadro **Autorizzazioni per \<nome utente\>** selezionare la casella di controllo **Controllo completo**.  
  
6.  Scegliere **OK**.  
  
     In questo modo all'utente vengono concesse le autorizzazioni per la struttura ad albero di cartelle condivise che ha inizio con la cartella selezionata nel passaggio 5.  
  
### Per concedere l'accesso al driver per la creazione di profili  
  
1.  Aprire un prompt dei comandi come amministratore.  
  
2.  Passare alla directory seguente:  
  
    ```  
    <drive>:\Program Files\Microsoft Visual Studio 10\Team Tools\Performance Tools  
    ```  
  
3.  Eseguire il comando seguente:  
  
    ```  
    vsperfcmd /admin:driver,start /admin:service,start  
    ```  
  
     Questo comando consente di installare e avviare il driver relativo agli strumenti di profilatura.  
  
     Questo comando avvia il driver e il servizio di profilatura in modo che utenti non amministratori possono utilizzare funzionalità di profilatura disponibili nello spazio di processo utente.  Solo un amministratore può eseguire il comando; non è possibile per gli utenti senza privilegi di amministratore.  
  
     Gli effetti derivanti dall'esecuzione di questo passaggio vengono annullati dopo il riavvio del computer, a meno che non venga eseguito anche l'ultimo passaggio della procedura in corso.  
  
4.  Eseguire il comando per consentire a un utente o un gruppo che non dispone dell'accesso di amministratore al computer di accedere alla profilatura della funzionalità del driver:  
  
    ```  
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>  
    ```  
  
     Questo comando garantisce l'accesso agli strumenti di profilatura \<nome utente\> o il \<nome gruppo\>.  L'opzione \<right\> determina la funzionalità di profilatura alla quale l'utente può accedere  L'opzione \<right\> può corrispondere a uno o più valori tra quelli riportati di seguito:  
  
    -   FullAccess \- consente l'accesso a tutti i metodi di profilatura, tra cui la raccolta dei dati di prestazioni della profilatura tra sessioni, mediante campionamento e dei servizi.  
  
    -   SampleProfiling \- consente l'accesso ai metodi di profilatura mediante campionamento  
  
    -   CrossSession \- consente l'accesso alla profilatura tra sessioni richiesta per la profilatura dei servizi.  
  
5.  \(Facoltativo\) Per conservare i risultati di uno dei passaggi precedenti dopo il riavvio del computer, eseguire il seguente comando:  
  
    ```  
    vsperfcmd /admin:driver,autostart,on  
    ```  
  
 Dopo aver effettuato l'accesso, gli utenti specificati saranno in grado di utilizzare gli strumenti di profilatura senza autorizzazioni di amministratore.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md)