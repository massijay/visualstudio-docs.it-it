---
title: "Procedura: instrumentare un&#39;applicazione Web ASP.NET compilata staticamente e raccogliere dati di memoria tramite la riga di comando del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: instrumentare un&#39;applicazione Web ASP.NET compilata staticamente e raccogliere dati di memoria tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene descritto come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un sito Web o un componente Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] precompilato e raccogliere dati relativi all'allocazione di memoria .NET, alla durata di oggetti e dati di intervallo dettagliati.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati da un componente Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] tramite il metodo di strumentazione, utilizzare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente.  Nel computer che ospita il componente, sostituire la versione non instrumentata del componente con la versione instrumentata.  Utilizzare quindi lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profiling globali e quindi riavviare il computer.  Avviare il profiler.  
  
 Quando viene eseguito il componente instrumentato, i dati di intervallo vengono raccolti automaticamente in un file di dati.  È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilo.  
  
 Per terminare una sessione di profilo, chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] che ospita il componente e arrestare in modo esplicito il profiler.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Avvio del profilo  
  
#### Per instrumentare un componente Web ASP.NET e avviare il profilo  
  
1.  Utilizzare lo strumento **VSInstr** per generare una versione instrumentata dell'applicazione di destinazione.  Se necessario, sostituire i file binari dell'applicazione nel computer host ASP.NET con i file binari instrumentati.  
  
2.  Aprire una finestra del prompt dei comandi.  
  
3.  Inizializzare le variabili di ambiente di profilo .NET.  In una finestra del prompt dei comandi, digitare:  
  
     **VSPerfClrEnv \/globaltracegc**  
  
     In alternativa  
  
     **VSPerfClrEnv \/globaltracegclife**  
  
    -   **\/globaltracegc** raccoglie dati di intervallo e allocazione di memoria .NET.  
  
    -   **\/globaltracegclife** raccoglie dati relativi all'allocazione di memoria .NET, alla durata di oggetti e dati di intervallo dettagliati.  
  
4.  Riavviare il computer.  
  
5.  Aprire una finestra del prompt dei comandi.  
  
6.  Avviare il profiler.  In una finestra del prompt dei comandi, digitare:  
  
     **VSPerfCmd \/start:trace \/output:**`OutputFile` \[`Options`\]  
  
    -   L'opzione [\/start](../profiling/start.md)**:trace** consente di inizializzare il profiler.  
  
    -   L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:trace**.  
  
    > [!NOTE]
    >  Le opzioni **\/user** e **\/crosssession** sono in genere obbligatorie per le applicazioni ASP.NET.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente facoltativi dell'account proprietario del processo di lavoro ASP.NET.  Questa opzione è obbligatoria se il processo è in esecuzione come un utente diverso dall'utente connesso. Il nome è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni.  Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa.  L'ID di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **\/globaloff** alla riga di comando **\/start**.  Utilizzare **\/globalon** per riprendere il profilo.|  
  
7.  Aprire il sito Web che contiene il componente instrumentato.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file utilizzando le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni seguenti avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Avvia \(**\/threadon**\) o interrompe \(**\/threadoff**\) la raccolta dei dati per il thread specificato dall'ID thread \(`TID`\).|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilatura, chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], quindi utilizzare il comando **IISReset** di Internet Information Services \(IIS\) per chiudere il processo di lavoro di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Chiamare l'opzione **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file dei dati di profilo.  Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo.  È necessario riavviare il computer per applicare le nuove impostazioni di ambiente.  
  
#### Per terminare una sessione di profilo  
  
1.  Chiudere l'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Chiudere il processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Tipo:  
  
     **IISReset \/stop**  
  
3.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
4.  \(Facoltativo\)  Cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfCmd \/globaloff**  
  
5.  Riavviare il computer.  Se necessario, riavviare IIS.  Tipo:  
  
     **IISReset \/start**  
  
## Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)