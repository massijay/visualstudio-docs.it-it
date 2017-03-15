---
title: "Procedura: avviare un&#39;applicazione .NET Framework autonoma con il profiler per raccogliere dati di memoria tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: avviare un&#39;applicazione .NET Framework autonoma con il profiler per raccogliere dati di memoria tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per avviare un'applicazione \(client\) autonoma .NET Framework e raccogliere dati di memoria.  
  
 Una sessione di profilo si suddivide in tre parti:  
  
-   Avvio dell'applicazione con il profiler.  
  
-   Raccolta dei dati di profilo.  
  
-   Fine della sessione di profilo.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra Prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Avvio dell'applicazione con il profiler  
 Per avviare un'applicazione di destinazione tramite il profiler, utilizzare le opzioni di **VSPerfCmd.exe \/start** e **\/launch** per inizializzare il profiler e avviare l'applicazione.  È possibile specificare **\/start** e **\/launch** e le opzioni relative in un'unica riga di comando.  
  
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
  
3.  Avviare l'applicazione di destinazione.  Tipo:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `appName` **\/gc:**{**allocation**&#124;**lifetime**}\[`Options`\]  
  
    -   L'opzione [\/gc](../profiling/gc-vsperfcmd.md)**:**`Keyword` è obbligatoria per raccogliere i dati di memoria .NET Framework.  Il parametro keyword specifica se raccogliere i dati sull'allocazione di memoria o se raccogliere sia i dati sull'allocazione di memoria sia quelli sulla durata degli oggetti.  
  
        |Parola chiave|Descrizione|  
        |-------------------|-----------------|  
        |**allocation**|Raccoglie unicamente i dati sull'allocazione di memoria.|  
        |**lifetime**|Raccoglie sia i dati sull'allocazione di memoria sia quelli sulla durata degli oggetti.|  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/launch**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Specifica una stringa che contiene gli argomenti della riga di comando da passare all'applicazione di destinazione.|  
    |[\/console](../profiling/console.md)|Avvia l'applicazione della riga di comando di destinazione in una finestra separata.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Specifica la versione di Common Language Runtime \(CLR\) di cui eseguire il profilo quando più di una versione del runtime è caricata in un'applicazione.|  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file utilizzando le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni seguenti avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:** `PID` [\/detach](../profiling/detach.md)|**\/attach** inizia a raccogliere dati per il processo specificato da `PID` \(l'ID di processo\).  **\/detach** interrompe la raccolta dei dati per tutti i processi.|  
  
-   È inoltre possibile utilizzare l'opzione **VSPerfCmd.exe** [\/mark](../profiling/mark.md) per inserire un contrassegno di profilo nel file di dati.  Il comando **\/mark** aggiunge un identificatore, un timestamp e una stringa di testo facoltativa definita dall'utente.  I contrassegni possono essere utilizzati per filtrare i dati.  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso a tutti i processi profilati e che venga arrestato in modo esplicito.  È possibile disconnettere il profiler da un'applicazione profilata con il metodo di campionamento chiudendo l'applicazione o richiamando l'opzione **VSPerfCmd \/detach**.  Chiamare quindi l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilatura.  Il comando **VSPerfClrEnv \/off** cancella le variabili di ambiente di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Chiudere l'applicazione di destinazione.  
  
         In alternativa  
  
    -   Digitare **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)