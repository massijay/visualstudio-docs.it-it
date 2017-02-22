---
title: "Procedura: connettersi a file script | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "processi, connessione a script"
  - "debug remoto, connessione a script"
  - "debug di script, connessione a script"
  - "script, connessione a"
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettersi a file script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come connettere manualmente il debugger di Visual Studio a un file script per l'esecuzione del debug.  
  
### Per connettersi a un processo in esecuzione  
  
1.  Scegliere **Connetti a processo** dal menu **Debug**. Se non è aperto alcun progetto, scegliere **Connetti a processo** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Connetti a processo** analizzare l'elenco **Processi disponibili** e individuare il processo di script al quale ci si desidera connettere.  È possibile identificare i processi di script esaminando la colonna **Tipo**.  
  
    1.  Se il processo di cui si desidera eseguire il debug è in esecuzione in un altro computer, sarà necessario innanzitutto selezionare il computer remoto.  Per ulteriori informazioni, vedere [How to: Select a Remote Computer](http://msdn.microsoft.com/it-it/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti**.  
  
    3.  Se la connessione è stata effettuata mediante **Connessione desktop remoto**, selezionare la casella di controllo **Mostra processi in tutte le sessioni**.  
  
3.  Fare clic sul processo al quale ci si desidera connettere.  
  
4.  Nella casella **Connetti a** verrà visualizzato **Codice script** o **Automatico: codice script**.  Se viene visualizzata una voce diversa, attenersi alla seguente procedura:  
  
    1.  Fare clic su **Seleziona**.  
  
    2.  Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare **Script**.  
  
    3.  Scegliere **OK**.  
  
5.  Scegliere **Connetti**.  
  
     A questo punto, è possibile che venga visualizzato un avviso in cui viene comunicato che il debug degli script è disabilitato in Internet Explorer.  In tal caso, vedere [Avviso: debug degli script disabilitato](../debugger/warning-script-debugging-disabled.md).  
  
 L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi**.  I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta.  È quindi possibile che il contenuto non sia sempre aggiornato.  Per visualizzare i processi correnti, è possibile aggiornare l'elenco in qualsiasi momento utilizzando il pulsante **Aggiorna**.  
  
 Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger.  È possibile impostare il programma attivo nella barra degli strumenti Posizione di debug.  Per ulteriori informazioni, vedere [How to: Set the Current Process](http://msdn.microsoft.com/it-it/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Tutti i comandi di esecuzione del menu **Debug** hanno effetto sul programma attivo.  È possibile interrompere l'esecuzione di qualsiasi programma sottoposto a debug dalla finestra di dialogo Processi. Vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione.  Per ulteriori informazioni, vedere [Avviso di sicurezza: può essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 In alcuni casi, quando viene eseguito il debug in una sessione di Servizi terminal \(Desktop remoto\), nell'elenco Processi disponibili non vengono visualizzati tutti i processi disponibili.  Se in [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] o versioni più recenti si esegue Visual Studio come utente con limitazioni, nell'elenco Processi disponibili non verranno visualizzati i processi in esecuzione nella Sessione 0, utilizzata per i servizi e gli altri processi del server tra cui w3wp.exe.  È possibile risolvere il problema eseguendo Visual Studio con un account di amministratore o dalla console del server invece di una sessione di Servizi Terminal.  Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo digitando vsjitdebugger.exe \-p IDProcesso dalla riga di comando di Windows.  È possibile determinare l'ID processo utilizzando tlist.exe.  Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows disponibili sul sito [Centro sviluppatori Windows \- Hardware](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## Vedere anche  
 [Debug di script sul lato client](../debugger/client-side-script-debugging.md)   
 [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Avviso di sicurezza: può essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)