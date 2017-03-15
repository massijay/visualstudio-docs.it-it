---
title: "Procedura: avviare un&#39;applicazione nativa autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: avviare un&#39;applicazione nativa autonoma con il profiler per raccogliere dati di concorrenza tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare un'applicazione \(client\) autonoma .NET Framework nativa e raccogliere dati di concorrenza di thread e processi.  
  
 Una sessione di profilo è costituita dalle parti seguenti:  
  
-   Avvio dell'applicazione con il profiler  
  
-   Controllo della raccolta di dati  
  
-   Fine della sessione di profilo  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare il profiler a un prompt dei comandi, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra **Prompt dei comandi** oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Avvio dell'applicazione con il profiler  
 Per avviare un'applicazione di destinazione tramite il profiler, utilizzare le opzioni di [VSPerfCmd.exe](../profiling/vsperfcmd.md) **\/start** e **\/launch** per inizializzare il profiler e avviare l'applicazione.  È possibile specificare **\/start** e **\/launch** e le opzioni relative.  È inoltre possibile aggiungere l'opzione **\/globaloff** per sospendere la raccolta dei dati all'avvio dell'applicazione di destinazione.  Utilizzare quindi **\/globalon** per avviare la raccolta dei dati.  
  
#### Per avviare un'applicazione con il profiler  
  
1.  Al prompt dei comandi digitare il comando seguente:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata nella tabella seguente con l'opzione **\/start:concurrency** .  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
2.  Avviare l'applicazione di destinazione digitando:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\]  
  
     È possibile utilizzare qualsiasi opzione riportata nella tabella seguente con l'opzione **\/launch**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|  
    |[\/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Specifica la versione di Common Language Runtime \(CLR\) di cui eseguire il profilo se l'applicazione carica più di una versione del CLR.|  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura di dati nel file utilizzando le opzioni di VSPerfCmd.exe.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni nella tabella seguente avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da ID processo \(`PID`\) o da nome processo \(*ProcName*\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato alcun processo.|  
  
-   È inoltre possibile utilizzare l'opzione **VSPerfCmd.exe** [\/mark](../profiling/mark.md) per inserire un contrassegno di profilo nel file di dati.  Il comando **\/mark** aggiunge un identificatore, un timestamp e una stringa di testo facoltativa definita dall'utente.  I contrassegni possono essere utilizzati per filtrare i dati nelle visualizzazioni dati e nei rapporti del profiler.  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, non deve essere in corso alcuna raccolta di dati.  È possibile interrompere la raccolta dei dati di concorrenza chiudendo l'applicazione profilata o richiamando l'opzione **VSPerfCmd \/detach**.  È quindi possibile richiamare l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Dissociare il profiler dall'applicazione di destinazione chiudendolo o digitando il comando seguente a un prompt dei comandi:  
  
     **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler digitando il comando seguente a un prompt dei comandi:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)