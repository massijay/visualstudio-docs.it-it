---
title: "Connessione a processi in esecuzione con il debugger di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.processes.attach"
  - "vs.debug.process"
  - "vs.debug.programs"
  - "vs.debug.detaching"
  - "vs.debug.processes"
  - "vs.debug.error.attach"
  - "vs.debug.remotemachine"
dev_langs: 
  - "C++"
  - "CSharp"
  - "FSharp"
  - "VB"
  - "c++"
helpviewer_keywords: 
  - "debug remoto, connessione a programmi"
  - "processi, connessione a processi in esecuzione"
  - "Finestra di dialogo Connetti a processo"
  - "debug [Visual Studio], connessione a processi"
  - "debugger, processi"
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 57
caps.handback.revision: 53
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Connessione a processi in esecuzione con il debugger di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Collegamento del debugger di Visual Studio a un processo è spesso utile quando un'applicazione non sia stato avviato da Visual Studio, ma si desidera eseguire il debug. Ad esempio, è possibile collegare a un processo IIS o un servizio Windows che ospita un'applicazione .NET. Il processo a che è collegare potrebbe essere locale o remoto. Un altro esempio è che se si esegue l'app senza il debugger rileva un'eccezione, è quindi possibile collegare al processo di esecuzione dell'applicazione per avviare il debug.

Per alcuni tipi di applicazione (ad esempio applicazioni Windows Store), è non collegato direttamente a un nome di processo, ma utilizzare il **Debug pacchetto applicazione installato** menu opzione (vedere la tabella).

Per identificare se è necessario connettersi a un processo per lo scenario, alcuni degli scenari di debug più comuni sono mostrate di seguito. Dove sono disponibili ulteriori istruzioni, vengono forniti i collegamenti.

|Scenario|Eseguire il debug (metodo)|Nome processo|Nota e collegamenti|
|-|-|-|-|
|Eseguire il debug di qualsiasi tipo supportato dal computer locale, a partire da Visual Studio|Debug con F5 standard|N/D|Vedere [Introduzione con il debugger](../debugger/getting-started-with-the-debugger.md)|
|Eseguire il debug remoto ASP.NET 4 o 4.5 in un server IIS|Utilizzare gli strumenti remoti e Connetti a processo|w3wp.exe|Vedere [ASP.NET di debug remoto in un computer remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Eseguire il debug remoto ASP.NET di base su un server IIS|Utilizzare gli strumenti remoti e Connetti a processo|DNX.exe|Per la distribuzione di app, vedere [pubblica in IIS](https://docs.asp.net/en/latest/publishing/iis.html). Per il debug, vedere [ASP.NET di debug remoto in un computer remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Eseguire il debug di altri tipi di app supportati in un processo del server|Utilizzare gli strumenti remoti (se server è remoto) e connettersi al processo|Iexplore.exe o altri processi|Se necessario, utilizzare Task Manager per identificare il processo. Vedere [debug remoto](../debugger/remote-debugging.md) e nelle sezioni successive di questo argomento|
|Debug remoto di un'applicazione desktop Windows|F5 e remote Tools|N/D| Vedere [debug remoto](../debugger/remote-debugging.md)|
|Un'app Windows universale (UWP), OneCore, HoloLens o IoT di debug remoto|Eseguire il debug pacchetto applicazione installata|N/D|Utilizzare **Debug / altre destinazioni Debug / Debug pacchetto applicazione installato** anziché **Connetti a processo**|
|Il debug di un'app Windows universale (UWP), OneCore, HoloLens o IoT non è stato avviato da Visual Studio|Eseguire il debug pacchetto applicazione installata|N/D|Utilizzare **Debug / altre destinazioni Debug / Debug pacchetto applicazione installato** anziché **Connetti a processo**|
  
> [!WARNING]
>  Per connettersi a un'app universale di Windows scritta in JavaScript, per prima cosa è necessario abilitare il debug per l'app. Vedere [Attach the debugger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) in Windows Dev Center.  
  
> [!NOTE]
>  Affinché il debugger possa connettersi a codice scritto in C++, è necessario che venga generato l'elemento `DebuggableAttribute`. È possibile aggiungere automaticamente questo elemento al codice mediante il collegamento all'opzione del linker [/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute) .

## <a name="what-debugger-features-can-i-use"></a>Le funzionalità del debugger è possibile utilizzare?

Per utilizzare le funzionalità complete del debugger di Visual Studio (come raggiungere i punti di interruzione), il file eseguibile deve corrispondere esattamente origine locale e simboli (ovvero, il debugger deve essere in grado di caricare il corretto [(.pbd) i file di simboli](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Per impostazione predefinita, questo richiede una build di debug.

Per scenari di debug remoti, è necessario che il codice sorgente una copia del codice sorgente già aperto in Visual Studio. I file binari compilati app nel computer remoto devono provenire dalla stessa compilazione come sul computer locale.

In alcuni scenari di debug locale, è possibile eseguire il debug in Visual Studio senza accesso all'origine se i file di simboli corretto sono presenti con l'app (per impostazione predefinita, è necessaria una build di debug). Per ulteriori informazioni, vedere [specificare simboli e file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Per le applicazioni desktop di Windows, è anche possibile eseguire il debug di app in esecuzione utilizzando il debugger JIT (Visual Studio apre e si interrompe il codice dell'applicazione dopo che si verifica un errore).

##  <a name="a-namebkmkattachtoaprocessonaremotecomputera-attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Connettersi a un processo in un computer remoto  
 Per connettersi a un processo, è necessario conoscere il nome del processo. Per le applicazioni ASP.NET sono state distribuite a IIS, vedere [ASP.NET di debug remoto in un computer remoto IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) o [pubblica in IIS](https://docs.asp.net/en/latest/publishing/iis.html) per le applicazioni ASP.NET di base. Per le altre applicazioni, è possibile trovare il nome del processo in Gestione attività.
  
 Quando si usa la finestra di dialogo **Connetti a processo** , è possibile selezionare un altro computer configurato per il debug remoto. Per ulteriori informazioni, vedere [debug remoto](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md). Dopo avere selezionato un computer remoto, è possibile visualizzare l'elenco dei processi disponibili in esecuzione in tale computer e connettersi a uno o più di questi processi per eseguire il debug.
  
 **Per selezionare un computer remoto:**  

1. In Visual Studio selezionare **Debug / Connetti a processo**.

2.  Nella finestra di dialogo **Connetti a processo** selezionare il tipo di connessione appropriato nell'elenco **Trasporto** . Per la maggior parte dei casi è possibile usare l'impostazione**Predefinito** .

    L'impostazione **Trasporto** viene mantenuta tra una sessione di debug e l'altra. 
  
3.  Usare la casella di riepilogo **Qualificatore** per scegliere il nome del computer remoto in uno dei seguenti modi:  
  
    1.  Digitare il nome nella casella di riepilogo **Qualificatore** .
    
        >**Nota** Se nei passaggi successivi, è possibile connettersi utilizzando il nome del computer remoto, utilizzare l'indirizzo IP. (Il numero di porta potrebbe essere visualizzate automaticamente dopo aver selezionato il processo. È possibile inoltre inserire manualmente. Nella figura riportata di seguito, 4020 è la porta predefinita per il debugger remoto.)  
  
    2.  Fare clic sulla freccia a discesa della casella di riepilogo **Qualificatore** e selezionare il nome del computer dall'elenco a discesa.  
  
    3.  Scegliere il pulsante **Trova** accanto all'elenco**Qualificatore** per aprire la finestra di dialogo **Seleziona connessione debugger remoto** . Nella finestra di dialogo **Seleziona connessione debugger remoto** sono elencati tutti i dispositivi presenti nella subnet locale e qualsiasi dispositivo connesso direttamente al computer tramite un cavo Ethernet. Fare clic sul computer o sul dispositivo desiderati e scegliere **Seleziona**. 
    
    ![DBG_Basics_Attach_To_Process](../debugger/media/dbg_basics_attach_to_process.png "DBG_Basics_Attach_To_Process") 
  
     L'impostazione **Qualificatore** viene invece mantenuta tra due sessioni di debug solo il qualificatore consente di stabilire correttamente una connessione di debug.
     
4.  Fare clic su **Aggiorna**.

      L'elenco **Processi disponibili** viene visualizzato automaticamente quando si apre la finestra di dialogo **Processi** . I processi possono essere avviati e interrotti in background mentre la finestra di dialogo è aperta. È quindi possibile che il contenuto non sia sempre aggiornato. Per visualizzare i processi correnti, è possibile aggiornare l'elenco in qualsiasi momento usando il pulsante **Aggiorna**. 
     
4.  Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .  
  
     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .
     
5.  Scegliere **Connetti**.  
  
##  <a name="a-namebkmkattachtoarunningprocessa-attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Connettersi a un processo in esecuzione nel computer locale  
 Per connettersi a un processo, è necessario conoscere il nome del processo.  È possibile trovare il nome del processo in Gestione attività.  
  
1.  In Visual Studio selezionare **Debug / Connetti a processo**.
  
2.  Nella finestra di dialogo **Connetti a processo** individuare il programma con il quale si desidera stabilire una connessione nell'elenco **Processi disponibili** .  
  
     Se il processo viene eseguito con un account utente diverso, selezionare la casella di controllo **Mostra processi di tutti gli utenti** .
  
3.  Nella casella **Connetti a** verificare che sia presente il tipo di codice di cui eseguire il debug. L'impostazione predefinita **Automatico** tenta di determinare il tipo di codice di cui si desidera eseguire il debug. Per impostare manualmente il tipo di codice, eseguire le operazioni seguenti  
  
    1.  Nella finestra di dialogo **Connetti a** scegliere **Seleziona**.  
  
    2.  Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare i tipi da sottoporre a debug.  
  
    3.  Fare clic su **OK**.  
  
4.  Scegliere **Connetti**.

## <a name="additional-info"></a>Informazioni aggiuntive

Durante l'esecuzione del debug è possibile essere connessi a più di un programma, ma in un dato momento solo uno di tali programmi potrà essere attivo nel debugger. È possibile impostare il programma attivo nella barra degli strumenti **Posizione di debug** o nella finestra **Processi** . Per altre informazioni, vedere [Procedura: Impostare il processo corrente](http://msdn.microsoft.com/it-it/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
Se si tenta di connettersi a un processo appartenente a un account utente non attendibile, verrà visualizzata una finestra di dialogo contenente un avviso di sicurezza per chiedere conferma dell'operazione. Per ulteriori informazioni vedere [avviso di sicurezza: la connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sospette o non si è certi, non collegare questo processo](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
In alcuni casi, quando viene eseguito il debug in una sessione di Desktop remoto (Servizi terminal), nell'elenco **Processi disponibili** non vengono visualizzati tutti i processi disponibili. Se si esegue Visual Studio con un account utente limitato, nell'elenco **Processi disponibili** non verranno visualizzati i processi in esecuzione nella Sessione 0 utilizzata per i servizi e gli altri processi del server, incluso w3wp.exe. È possibile risolvere il problema eseguendo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] con un account amministratore o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla console del server invece di una sessione di Servizi Terminal. Se non è possibile adottare una di queste soluzioni alternative, una terza opzione consiste nel connettersi al processo eseguendo `vsjitdebugger.exe -p` *ProcessId* dalla riga di comando di Windows. È possibile determinare l'ID processo usando tlist.exe. Per ottenere tlist.exe, scaricare e installare gli strumenti di debug per Windows disponibili in  [Download di WDK e WinDbg](http://go.microsoft.com/fwlink/?LinkId=168279).
  
##  <a name="a-namebkmktroubleshootattacherrorsa-troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Risolvere gli errori di connessione  
 I processi in esecuzione a cui il debugger tenta di connettersi possono contenere uno o più tipi di codice. I tipi di codice a cui il debugger può connettersi vengono visualizzati e selezionati nella finestra di dialogo **Seleziona tipo di codice** .  
  
 In alcuni casi il debugger riesce a connettersi a un tipo di codice ma non a un altro. Questa situazione può verificarsi quando si tenta di stabilire una connessione a un processo in esecuzione in un computer remoto, nel quale potrebbero essere stati installati i componenti per il debug remoto solo per alcuni tipi di codice. Può inoltre verificarsi quando si tenta di stabilire una connessione a due o più processi per il debug diretto di un database. Durante il debug SQL è supportata esclusivamente la connessione a un singolo processo.  
  
 Se il debugger è in grado di connettersi solo ad alcuni tipi di codice, verrà visualizzato un messaggio che identifica i tipi per i quali la connessione ha avuto esito negativo.  
  
 Se il debugger riesce a connettersi ad almeno un tipo di codice, è possibile procedere con il debug del processo. Sarà possibile eseguire il debug solo dei tipi di codice con i quali è stata stabilita una connessione. Il messaggio di esempio sopra riportato segnala che non è stato possibile stabilire una connessione al tipo di codice di script. Non sarà quindi possibile eseguire il debug del codice di script nel processo. Il codice di script del processo verrà comunque eseguito, ma non sarà possibile impostare punti di interruzione, visualizzare dati o eseguire altre operazioni di debug nello script.  
  
 Se si desidera ottenere informazioni più specifiche sulla causa che ha impedito al debugger di connettersi a un tipo di codice, è possibile provare a ripetere la connessione solo a quel tipo di codice.  
  
 **Per ottenere informazioni specifiche sulla causa dell'errore collegare un tipo di codice**  
  
1.  Disconnettersi dal processo. Scegliere **Disconnetti tutto** dal menu **Debug**.  
  
2.  Riconnettersi al processo, selezionando un solo tipo di codice.  
  
    1.  Nella finestra di dialogo **Connetti a processo** selezionare il processo nell'elenco **Processi disponibili** .  
  
    2.  Fare clic su **Seleziona**.  
  
    3.  Nella finestra di dialogo **Seleziona tipo di codice** selezionare il pulsante di opzione **Esegui il debug di questi tipi di codice** e il tipo di codice per cui si è verificato il problema di connessione. Deselezionare tutti gli altri codici.  
  
    4.  Fare clic su **OK**. La finestra di dialogo **Seleziona tipo di codice** verrà chiusa.  
  
    5.  Nella finestra di dialogo **Connetti a processo** scegliere **Connetti**.  
  
     La connessione non verrà eseguita e verrà visualizzato un messaggio di errore specifico.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di più processi](../debugger/debug-multiple-processes.md)   
 [Il debug Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Debug remoto](../debugger/remote-debugging.md)