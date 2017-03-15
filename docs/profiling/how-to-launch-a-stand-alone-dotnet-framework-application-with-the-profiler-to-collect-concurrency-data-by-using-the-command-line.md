---
title: "Procedura: avviare un&#39;applicazione .NET Framework autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: avviare un&#39;applicazione .NET Framework autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare un'applicazione \(client\) autonoma .NET Framework e raccogliere dati di concorrenza di thread e processi.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Quando il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso all'applicazione e che venga arrestato in modo esplicito.  
  
## Avvio dell'applicazione con il profiler  
 Per avviare un'applicazione di destinazione .NET Framework con il profiler, utilizzare VSPerfClrEnv.exe per impostare le variabili di profilo di .NET Framework.  Utilizzare quindi le opzioni **\/start** e **\/launch** di VSPerfCmd per inizializzare il profiler e avviare l'applicazione.  È possibile specificare **\/start** e **\/launch** e le opzioni relative in un'unica riga di comando.  È inoltre possibile aggiungere l'opzione **\/globaloff** alla riga di comando per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione.  Utilizzare quindi **\/globalon** in una riga di comando separata per avviare la raccolta dei dati.  
  
#### Per avviare un'applicazione con il profiler  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Avviare il profiler.  Tipo:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   L'opzione [\/start](../profiling/start.md) consente di inizializzare il profiler.  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|Abilita la raccolta dei dati di esecuzione thread e dei conflitti di risorse.|  
        |**\/start:concurrency,resourceonly**|Abilita la raccolta dei soli dati dei conflitti di risorse.|  
        |**\/start:concurrency,threadonly**|Abilita la raccolta dei soli dati di esecuzione thread.|  
  
    -   L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:concurrency** .  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Specifica il dominio e il nome utente facoltativi dell'account per ottenere l'accesso al profiler.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
3.  Avviare l'applicazione di destinazione.  Tipo:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\] \[`Sample Event`\]  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/launch**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|  
    |[\/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Specifica la versione di Common Language Runtime \(CLR\) di cui eseguire il profilo quando più di una versione del runtime è caricata in un'applicazione.|  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura di dati nel file utilizzando le opzioni di VSPerfCmd.exe.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
1.  Le coppie seguenti di opzioni di VSPerfCmd.exe avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da ID processo \(`PID`\) o da nome processo \(ProcName\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato un processo particolare.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, non deve essere in corso alcuna raccolta di dati.  È possibile interrompere la raccolta dei dati di concorrenza chiudendo l'applicazione profilata o richiamando l'opzione **VSPerfCmd \/detach**.  È quindi possibile richiamare l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilo.  Il comando **VSPerfClrEnv \/off** cancella le variabili di ambiente di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione.  
  
    -   Chiudere l'applicazione di destinazione.  
  
         In alternativa  
  
    -   Digitare **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Vedere anche  
 [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)