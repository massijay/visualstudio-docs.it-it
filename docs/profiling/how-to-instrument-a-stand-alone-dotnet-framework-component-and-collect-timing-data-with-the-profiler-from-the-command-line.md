---
title: "Procedura: instrumentare un componente autonomo .NET Framework e raccogliere dati di intervallo con il profiler tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: instrumentare un componente autonomo .NET Framework e raccogliere dati di intervallo con il profiler tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un componente .NET Framework, ad esempio un file con estensione exe o dll, e raccogliere dati di intervallo dettagliati.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra Prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Aggiungere dati di interazione a livelli a un'esecuzione del profilo richiede procedure specifiche con gli strumenti di profilatura della riga di comando.  Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Per raccogliere dati di intervallo dettagliati da un componente .NET Framework tramite il metodo di strumentazione, utilizzare lo strumento [VSInstr.exe](../profiling/vsinstr.md) per generare una versione instrumentata del componente e lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente di profilo.  Avviare il profiler.  
  
 Quando viene eseguito il componente instrumentato, i dati di intervallo vengono raccolti automaticamente in un file di dati.  È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilo.  
  
 Per terminare una sessione di profilo, chiudere l'applicazione di destinazione e arrestare in modo esplicito il profiler.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Avvio della sessione di profilo  
  
#### Per avviare il profilo mediante il metodo di strumentazione  
  
1.  Aprire una finestra del prompt dei comandi.  Se necessario, aggiungere la directory degli strumenti del profiler alla variabile di ambiente PATH.  Il percorso non viene aggiunto all'installazione.  
  
2.  Utilizzare lo strumento **VSInstr** per generare una versione instrumentata dell'applicazione di destinazione.  
  
3.  Inizializzare le variabili di ambiente di profilo di .NET Framework.  Tipo:  
  
     **VSPerfClrEnv \/traceon**  
  
4.  Avviare il profiler.  Tipo:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   L'opzione [\/start](../profiling/start.md)**:trace** consente di inizializzare il profiler.  
  
    -   L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:trace**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo profilato.  Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni.  Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa.  L'identificatore di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Avvia il profiler con la raccolta dei dati in pausa.  Utilizzare [\/globalon](../profiling/globalon-and-globaloff.md) per riprendere il profilo.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Raccoglie informazioni dal contatore delle prestazioni del processore specificato in `Config`.  Le informazioni del contatore vengono aggiunte ai dati raccolti a ogni evento di profilatura.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
5.  Avviare l'applicazione di destinazione dalla finestra del prompt dei comandi.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file dei dati del profiler tramite le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni seguenti avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Avvia \(**\/threadon**\) o interrompe \(**\/threadoff**\) la raccolta dei dati per il thread specificato dall'ID thread \(`TID`\).|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, chiudere l'applicazione che esegue il componente instrumentato.  Chiamare l'opzione **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file dei dati di profilatura.  Il comando **VSPerfClrEnv \/off** cancella le variabili di ambiente di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Chiudere l'applicazione di destinazione.  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Facoltativo\) Cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv \/off**  
  
## Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)