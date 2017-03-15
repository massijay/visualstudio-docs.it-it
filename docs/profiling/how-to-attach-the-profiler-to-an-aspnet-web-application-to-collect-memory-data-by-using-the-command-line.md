---
title: "Procedura: connettere il profiler a un&#39;applicazione Web ASP.NET per raccogliere dati di memoria tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettere il profiler a un&#39;applicazione Web ASP.NET per raccogliere dati di memoria tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene descritto come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e raccogliere i dati relativi al numero e alla dimensione delle allocazioni della memoria .NET Framework.  È inoltre possibile raccogliere dati sulla durata degli oggetti di memoria .NET Framework.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra Prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere i dati delle prestazioni da un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], è necessario utilizzare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate nel computer che ospita l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  È quindi necessario riavviare il computer per configurare il server Web per la profilatura.  
  
 Utilizzare quindi lo strumento [VSPerfCmd.exe](../profiling/vsperfcmd.md) per connettere il profiler al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che ospita il sito Web.  Quando il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso all'applicazione e che venga arrestato in modo esplicito.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Connessione del profiler  
  
#### Per connettere il profiler a un'applicazione Web ASP.NET  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Inizializzare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   Le opzioni **\/globalsamplegc** e **\/globalsamplegclife** specificano il tipo di dati di memoria da raccogliere.  
  
         Specificare una sola delle seguenti opzioni.  
  
        |Opzione|Descrizione|  
        |-------------|-----------------|  
        |**\/globalsamplegc**|Abilita la raccolta dei dati sull'allocazione di memoria.|  
        |**\/globalsamplegclife**|Abilita la raccolta dei dati relativi sia all'allocazione della memoria che alla durata degli oggetti.|  
  
    -   L'opzione **\/samplelineoff** disabilita l'assegnazione dei dati raccolti a righe specifiche del codice sorgente.  Se viene specificata questa opzione, i dati vengono assegnati a livello di funzione.  
  
3.  Riavviare il computer per impostare la nuova configurazione dell'ambiente.  
  
4.  Aprire una finestra del prompt dei comandi.  Se necessario, impostare la variabile di ambiente del percorso del profiler.  
  
5.  Avviare il profiler.  Tipo:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   L'opzione **\/start:sample** consente di inizializzare il profiler.  
  
    -   L'opzione **\/output:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:sample**.  
  
    > [!NOTE]
    >  Le opzioni **\/user** e **\/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET.  Questa opzione è obbligatoria se il processo è in esecuzione come un utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.  Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa.  L'identificatore di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|Specifica il numero di secondi di attesa prima che il profiler venga inizializzato prima che venga restituito un errore.  Se `Interval` non è specificato, il profiler attenderà un periodo di tempo indefinito.  Per impostazione predefinita, **\/start** viene immediatamente restituito.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
6.  Avviare l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nel modo usuale.  
  
7.  Connettere il profiler a un processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Tipo:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   L'ID processo `(PID)` specifica l'ID o il nome del processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  È possibile visualizzare gli ID processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   **\/targetclr:** `Version`  specifica la versione di Common Language Runtime \(CLR\) da profilare quando più di una versione del runtime è caricata in un'applicazione.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file dei dati del profiler tramite le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie seguenti di opzioni di **VSPerfCmd** avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dal `PID`.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;:`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato dall'ID processo o dal nome processo.  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato un processo particolare.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso all'applicazione Web.  È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di campionamento riavviando il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] o chiamando l'opzione **VSPerfCmd \/detach**.  Chiamare quindi l'opzione **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file dei dati di profilatura.  Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo, ma la configurazione del sistema non viene reimpostata finché non viene riavviato il computer.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Digitare **VSPerfCmd** [\/detach](../profiling/detach.md)  
  
         In alternativa  
  
    -   Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Tipo:  
  
     **IISReset \/stop**  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Facoltativo\) Cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
4.  Riavviare il computer.  Se necessario, riavviare Internet Information Services \(IIS\).  Tipo:  
  
     **IISReset \/start**  
  
## Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)