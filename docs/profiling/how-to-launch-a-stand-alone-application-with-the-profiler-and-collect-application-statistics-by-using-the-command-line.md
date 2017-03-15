---
title: "Procedura: avviare un&#39;applicazione autonoma con il profiler e raccogliere statistiche dell&#39;applicazione tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: avviare un&#39;applicazione autonoma con il profiler e raccogliere statistiche dell&#39;applicazione tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare un'applicazione \(client\) autonoma e raccogliere statistiche sulle prestazioni tramite il metodo di campionamento.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Aggiungere dati di interazione a livelli a un'esecuzione del profilo richiede procedure specifiche con gli strumenti di profilatura della riga di comando.  Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
 Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  È possibile eseguire gli strumenti di profilatura su un computer in cui è installato Visual Studio da una finestra di comando di Visual Studio.  
  
1.  Se si eseguono gli strumenti di profilatura su un computer in cui è installato Visual Studio una finestra di comando di Visual Studio imposta i percorsi corretti.  Nel menu **Strumenti**, scegliere **prompt dei comandi di VS**  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli Strumenti di Profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di Visual Studio.  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Avvio dell'applicazione con il profiler  
 Per avviare un'applicazione di destinazione tramite il profiler, utilizzare le opzioni **\/start** e **\/launch** di VSPerfCmd per inizializzare il profiler e avviare l'applicazione.  È possibile specificare **\/start** e **\/launch** e le opzioni relative in un'unica riga di comando.  
  
 È inoltre possibile aggiungere l'opzione **\/globaloff** per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione.  Utilizzare quindi **\/globalon** per avviare la raccolta dei dati.  
  
#### Per avviare un'applicazione con il profiler  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Avviare il profiler.  Tipo:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   L'opzione [\/start](../profiling/start.md)**:sample** consente di inizializzare il profiler.  
  
    -   L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:sample**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
3.  Avviare l'applicazione di destinazione.  Digitare:**VSPerfCmd \/launch:**`appName` \[`Options`\] \[`Sample Event`\]  
  
     È possibile utilizzare una o più opzioni riportate di seguito con l'opzione **\/launch**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|  
    |[\/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|  
  
     Per impostazione predefinita, i dati di prestazioni vengono campionati ogni 10.000.000 cicli di clock del processore non interrotti, ovvero  circa una volta ogni 10 secondi su un processore da 1 GHz.  È possibile specificare una delle opzioni seguenti per modificare l'intervallo dei cicli di clock o per specificare un evento di campionamento diverso.  
  
    |Evento di campionamento|Descrizione|  
    |-----------------------------|-----------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Imposta l'intervallo di campionamento sul numero di cicli di clock non interrotti specificato da `Interval`.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Imposta l'evento di campionamento sugli errori di pagina.  Se si specifica `Interval`, imposta il numero di errori di pagina tra campioni.  Il valore predefinito è 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[**:**`Interval`\]|Imposta l'evento di campionamento sulle chiamate di sistema dal processo al kernel del sistema operativo \(syscall\).  Se si specifica `Interval`, imposta il numero di chiamate tra campioni.  Il valore predefinito è 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Imposta l'evento e l'intervallo di campionamento sul contatore delle prestazioni del processore e sull'intervallo specificati in `Config`.|  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file dei dati del profiler tramite le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni seguenti avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da `PID` o dal nome del processo \(ProcName\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato un processo particolare.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso ai processi profilati e che venga arrestato in modo esplicito.  È possibile disconnettere il profiler da un'applicazione profilata con il metodo di campionamento chiudendo l'applicazione o richiamando l'opzione **VSPerfCmd \/detach**.  Chiamare quindi l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilo.  Il comando **VSPerfClrEnv \/off** cancella le variabili di ambiente di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Chiudere l'applicazione di destinazione.  
  
         In alternativa  
  
    -   Digitare **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)