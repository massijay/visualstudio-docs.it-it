---
title: "Procedura: connettere il profiler a un&#39;applicazione Web ASP.NET per raccogliere statistiche dell&#39;applicazione tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettere il profiler a un&#39;applicazione Web ASP.NET per raccogliere statistiche dell&#39;applicazione tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione Web ASP.NET e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  L'aggiunta di dati di interazione tra livelli a un'esecuzione di profilatura richiede procedure specifiche con gli strumenti di profilatura da riga di comando.  Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
>   
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati di prestazioni da un'applicazione Web ASP.NET, è necessario inizializzare le variabili di ambiente appropriate e riavviare il computer che ospita l'applicazione Web ASP.NET per configurare il server Web per il profilo.  
  
 Connettere il profiler al processo di lavoro ASP.NET che ospita il sito Web.  Quando il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso all'applicazione profilata e che venga arrestato in modo esplicito.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Avvio del profiler e connessione a un'applicazione Web ASP.NET  
  
#### Per connettere il profiler a un'applicazione Web ASP.NET  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Inizializzare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv \/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** abilita il campionamento.  
  
    -   **\/samplelineoff** disabilita l'assegnazione dei dati raccolti a righe specifiche del codice sorgente.  Quando viene specificata questa opzione, i dati vengono assegnati solo alle funzioni.  
  
3.  Riavviare il computer.  
  
4.  Avviare il profiler.  Digitare:**VSPerfCmd** [\/start](../profiling/start.md)**:sample** [\/output](../profiling/output.md)**:**`OutputFile`\[`Options`\]  
  
    -   L'opzione  **\/start:sample** consente di inizializzare il profiler.  
  
    -   L'opzione **\/output:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:sample**.  
  
    > [!NOTE]
    >  Le opzioni **\/user** e **\/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET.  Questa opzione è obbligatoria se il processo è in esecuzione come un utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.  Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa.  L'identificatore di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
5.  Avviare l'applicazione Web ASP.NET nel modo usuale.  
  
6.  Connettere il profiler a un processo di lavoro ASP.NET.  Digitare:**VSPerfCmd** [\/attach](../profiling/attach.md)**:**{`PID` &#124;`ProcName`} \[`Sample Event`\] \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` specifica l'ID del processo di lavoro ASP.NET; `ProcName` specifica il nome del processo di lavoro.  È possibile visualizzare gli ID e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   Per impostazione predefinita, i dati di prestazioni vengono campionati ogni 10.000.000 cicli di clock del processore non interrotti, ovvero  circa 100 volte al secondo su un processore da 1 GHz.  È possibile specificare una delle opzioni **VSPerfCmd** seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.  
  
    |Evento di campionamento|Descrizione|  
    |-----------------------------|-----------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Imposta l'evento di campionamento sugli errori di pagina.  Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni.  Il valore predefinito è 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[`:``Interval`\]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo \(syscall\).  Se si specifica `Interval`, imposta il numero di chiamate tra campioni.  Il valore predefinito è 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Specifica la versione di Common Language Runtime \(CLR\) di cui eseguire il profilo quando più di una versione del runtime è caricata in un'applicazione.|  
  
    -   **targetclr:** `Version` specifica la versione di Common Language Runtime \(CLR\) da profilare quando più di una versione del runtime è caricata in un'applicazione.  Parametro facoltativo.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file tramite le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie seguenti di opzioni di **VSPerfCmd** avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` **\/processoff:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato da `PID`.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da `PID` o dal nome del processo \(ProcName\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato un processo particolare.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilatura, chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], quindi utilizzare il comando **IISReset** di Internet Information Services \(IIS\) per chiudere il processo di lavoro di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Chiamare l'opzione **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file dei dati di profilatura.  
  
 Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo.  È necessario riavviare il computer per applicare le nuove impostazioni di ambiente.  
  
 Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo, ma la configurazione del sistema non viene reimpostata finché non viene riavviato il computer.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Digitare **VSPerfCmd \/detach**  
  
         In alternativa  
  
    -   Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Arrestare il profiler.  Digitare:**VSPerfCmd** [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Facoltativo\) Cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
4.  Riavviare il computer.  
  
## Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)