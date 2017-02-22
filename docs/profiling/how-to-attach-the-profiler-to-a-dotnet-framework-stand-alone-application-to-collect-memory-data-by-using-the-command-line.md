---
title: "Procedura: connettere il profiler a un&#39;applicazione .NET Framework autonoma per raccogliere dati di memoria tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettere il profiler a un&#39;applicazione .NET Framework autonoma per raccogliere dati di memoria tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] per connettere il profiler a un'applicazione \(client\) autonoma .NET Framework in esecuzione e raccogliere dati di memoria.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra Prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per connettersi a un'applicazione .NET Framework e raccogliere dati di memoria, è necessario utilizzare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate prima dell'avvio dell'applicazione di destinazione.  Quando il profiler è connesso all'applicazione, è possibile utilizzare lo strumento **VSPerfCmd.exe** per sospendere e riprendere la raccolta dei dati.  
  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso a tutti i processi profilati e che venga arrestato in modo esplicito.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Connessione del profiler  
  
#### Per connettere il profiler a un'applicazione .NET Framework in esecuzione  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Inizializzare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv** {**\/samplegc** &#124; **\/samplegclife**} \[**\/samplelineoff**\]  
  
    -   Le opzioni **\/samplegc** e **\/samplegclife** specificano se raccogliere unicamente i dati sull'allocazione della memoria oppure i dati sull'allocazione della memoria e sulla durata degli oggetti.  È necessario specificare una sola opzione.  
  
        |Opzione|Descrizioni|  
        |-------------|-----------------|  
        |**\/samplegc**|Raccoglie unicamente i dati sull'allocazione di memoria.|  
        |**\/samplegclife**|Raccoglie sia i dati sull'allocazione di memoria sia quelli sulla durata degli oggetti.|  
  
    -   L'opzione **\/samplelineoff** disabilita la raccolta dei dati del numero di riga del codice sorgente.  
  
3.  Avviare il profiler.  Tipo:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   L'opzione [\/start](../profiling/start.md)**:sample** consente di inizializzare il profiler.  
  
    -   L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:sample**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo profilato.  Questa opzione è obbligatoria solo se il processo è in esecuzione come utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession &#124; \/cs](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni.  Questa opzione è obbligatoria se l'applicazione è in esecuzione in una sessione diversa.  L'identificatore di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
  
4.  Se necessario, avviare l'applicazione di destinazione nel modo usuale.  
  
5.  Connettere il profiler all'applicazione di destinazione.  Tipo:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` specifica l'ID processo dell'applicazione di destinazione.  `ProcessName` specifica il nome del processo.  Si noti che se si specifica che sono in esecuzione `ProcessName` e più processi con lo stesso nome, i risultati sono imprevedibili.  È possibile visualizzare gli ID processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   **\/targetclr:** `Version` specifica la versione di Common Language Runtime \(CLR\) di cui eseguire il profilo quando più di una versione del runtime è caricata in un'applicazione.  Parametro facoltativo.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura dei dati nel file utilizzando le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni seguenti avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato da `PID`.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da `PID` o dal nome del processo \(ProcName\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato un processo particolare.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso a tutti i processi profilati e che venga arrestato in modo esplicito.  È possibile disconnettere il profiler da un'applicazione profilata con il metodo di campionamento chiudendo l'applicazione o richiamando l'opzione **VSPerfCmd \/detach**.  Chiamare quindi l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilatura.  Il comando **VSPerfClrEnv \/off** cancella le variabili di ambiente di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Effettuare una delle operazioni seguenti per disconnettere il profiler dall'applicazione di destinazione:  
  
    -   Digitare **VSPerfCmd \/detach**  
  
         In alternativa  
  
    -   Chiudere l'applicazione di destinazione.  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Facoltativo\) Cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfCmd \/off**  
  
## Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)