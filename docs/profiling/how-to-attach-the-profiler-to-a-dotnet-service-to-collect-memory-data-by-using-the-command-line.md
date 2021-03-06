---
title: "Procedura: connettere il profiler a un servizio .NET per raccogliere dati di memoria tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettere il profiler a un servizio .NET per raccogliere dati di memoria tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un servizio [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e raccogliere dati sull'utilizzo della memoria.  È possibile raccogliere dati sul numero e la dimensione delle allocazioni di memoria nonché sulla durata degli oggetti di memoria.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati di memoria da un servizio [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], utilizzare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate nel computer che ospita il servizio.  È necessario riavviare il computer per configurarlo per il profilo.  
  
 Utilizzare quindi lo strumento [VSPerfCmd](../profiling/vsperfcmd.md) per connettere il profiler al processo del servizio.  Quando il profiler è connesso al servizio, è possibile sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso al servizio e che venga arrestato in modo esplicito.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Connessione del profiler  
  
#### Per connettere il profiler a un servizio .NET Framework  
  
1.  Se necessario, installare il servizio.  
  
2.  Aprire una finestra del prompt dei comandi.  
  
3.  Inizializzare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv** {**\/globalsamplegc \/globalsamplegclife**}\[**\/samplelineoff**\]  
  
    -   Le opzioni **\/globalsamplegclife** e **\/globalsamplegclife** specificano il tipo di dati di memoria da raccogliere.  Specificare una sola delle seguenti opzioni.  
  
     **\/globalsamplegc**  
     Abilita la raccolta dei dati sull'allocazione di memoria.  
  
     **\/globalsamplegclife**  
     Abilita la raccolta dei dati relativi sia all'allocazione della memoria che alla durata degli oggetti.  
  
    -   L'opzione **\/samplelineoff** disabilita la raccolta dei dati del numero di riga del codice sorgente.  
  
4.  Riavviare il computer per impostare la nuova configurazione dell'ambiente.  
  
5.  Se necessario, avviare il servizio.  
  
6.  Aprire una finestra del prompt dei comandi.  Se necessario, aggiungere il percorso del profiler alla variabile di ambiente PATH.  
  
7.  Avviare il profiler.  Tipo:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   L'opzione **\/start:sample** consente di inizializzare il profiler.  
  
    -   L'opzione **\/output:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare una o più delle opzioni riportate di seguito con l'opzione **\/start:sample**.  
  
    > [!NOTE]
    >  Le opzioni **\/user** e **\/crosssession** sono in genere obbligatorie per i servizi.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo.  Questa opzione è obbligatoria se il processo è in esecuzione come un utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.  Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa.  L'ID di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente facoltativi dell'account di accesso in cui viene eseguito il servizio.  L'account di accesso è elencato nella colonna Accedi come del servizio in Gestione controllo servizi di Windows.|  
    |[\/crosssession&#124;cs](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
8.  Connettere il profiler al servizio.  Tipo:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   Specificare l'ID o il nome del processo del servizio.  È possibile visualizzare gli ID e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   **targetclr:** `Version` specifica la versione di Common Language Runtime \(CLR\) da profilare quando più di una versione del runtime è caricata in un'applicazione.  Parametro facoltativo.  
  
## Controllo della raccolta di dati  
 Quando il servizio è in esecuzione, è possibile utilizzare le opzioni di **VSPerfCmd.exe** per interrompere e avviare la scrittura dei dati nel file di dati del profiler.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie seguenti di opzioni di **VSPerfCmd** avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da ID processo o da nome processo.  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato un processo particolare.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, non deve essere in corso alcuna raccolta di dati.  È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di campionamento interrompendo il servizio o chiamando l'opzione **VSPerfCmd \/detach**.  Si chiama quindi l'opzione **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file dei dati di profilo.  Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo, ma la configurazione del sistema non viene reimpostata finché non viene riavviato il computer.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Arrestare il servizio.  
  
         In alternativa  
  
    -   Digitare **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Facoltativo\) Cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  Riavviare il computer.  
  
## Vedere anche  
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)