---
title: "Procedura: connettere il profiler a un&#39;applicazione Web ASP.NET per raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettere il profiler a un&#39;applicazione Web ASP.NET per raccogliere dati di concorrenza tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione ASP.NET e raccogliere dati di concorrenza di thread e processi.  
  
 Gli strumenti da riga di comando degli Strumenti di Profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di Visual Studio.  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare il profiler a un prompt dei comandi, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra **Prompt dei comandi** oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Per raccogliere dati sulla concorrenza, allegare il profiler al processo di lavoro ASP.NET che ospita il sito Web.  Quando il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso all'applicazione e che venga arrestato in modo esplicito.  Nella maggior parte dei casi, è necessario cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
## Connessione del profiler  
  
#### Per connettere il profiler a un'applicazione ASP.NET  
  
1.  Avviare il profiler digitando il comando seguente:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency \/output:**`OutputFile` \[`Options`\]  
  
    -   L'opzione [\/start](../profiling/start.md) inizializza il profiler per raccogliere dati sui conflitti di risorse.  
  
    -   L'opzione [\/output](../profiling/output.md)**:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione nella tabella seguente con l'opzione **\/start** .  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|Specifica il dominio e il nome utente facoltativi dell'account per ottenere l'accesso al profiler.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
2.  Avviare l'applicazione ASP.NET nel modo usuale.  
  
3.  Connettere il profiler al processo di lavoro ASP.NET digitando il comando seguente:**VSPerfCmd \/attach:**`PID` \[**\/targetclr:**`Version`\]  
  
    -   `PID` specifica l'ID o il nome del processo di lavoro ASP.NET.  È possibile visualizzare gli ID processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` specifica la versione del Common Language Runtime \(CLR\) da profilare quando vengono caricate più versioni del runtime in un'applicazione.  Questo parametro è facoltativo.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura di dati nel file utilizzando le opzioni di VSPerfCmd.exe.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni VSPerfCmd nella tabella seguente avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da ID processo \(`PID`\) o da nome processo \(*ProcName*\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato alcun processo.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, non deve essere in corso alcuna raccolta di dati.  È possibile interrompere la raccolta dei dati da un'applicazione di cui viene eseguita il profilo con il metodo di concorrenza riavviando il processo di lavoro ASP.NET oppure richiamando l'opzione **VSPerfCmd \/detach**.  È quindi possibile richiamare l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilo.  Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo, ma la configurazione del sistema non viene reimpostata finché non viene riavviato il computer.  
  
#### Per terminare una sessione di profilo  
  
1.  Dissociare il profiler dall'applicazione di destinazione chiudendolo o digitando quanto segue a un prompt dei comandi:  
  
     **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler digitando il comando seguente a un prompt dei comandi:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Vedere anche  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)