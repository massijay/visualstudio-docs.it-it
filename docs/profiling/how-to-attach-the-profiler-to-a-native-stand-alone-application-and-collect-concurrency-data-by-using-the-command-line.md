---
title: "Procedura: connettere il profiler a un&#39;applicazione autonoma nativa e raccogliere dati di concorrenza tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 12d3e0f3-4b74-4e66-8fbf-8ac99bd4f91c
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: connettere il profiler a un&#39;applicazione autonoma nativa e raccogliere dati di concorrenza tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per connettere il profiler a un'applicazione autonoma \(C\/C\+\+\) nativa e raccogliere dati su conflitti di thread.  
  
> [!NOTE]
>  Gli strumenti da riga di comando degli Strumenti di Profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di Visual Studio.  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra **Prompt dei comandi** oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Quando il profiler è connesso all'applicazione, è possibile sospendere e riprendere la raccolta dei dati.  Per terminare una sessione di profilo, è necessario che il profiler non sia più connesso all'applicazione e che venga arrestato in modo esplicito.  
  
## Connessione del profiler a un'applicazione nativa in esecuzione  
  
#### Per connettere il profiler a un'applicazione nativa in esecuzione  
  
1.  Al prompt dei comandi digitare il comando seguente:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**  
  
     È possibile utilizzare qualsiasi opzione riportata nella tabella seguente con l'opzione **\/start:concurrency**.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`Username`|Specifica il dominio e il nome utente facoltativi dell'account per ottenere l'accesso al profiler.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
2.  Connettere il profiler all'applicazione di destinazione digitando il comando seguente:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`}  
  
     `PID` specifica l'ID processo dell'applicazione di destinazione.  È possibile visualizzare gli ID processo di tutti i processi in esecuzione in Gestione attività di Windows.  
  
## Controllo della raccolta di dati  
 Quando l'applicazione di destinazione è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura di dati nel file utilizzando le opzioni di VSPerfCmd.exe.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie di opzioni nella tabella seguente avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach** avvia la raccolta di dati per il processo specificato da ID processo \(`PID`\) o da nome processo \(*ProcName*\).  **\/detach** interrompe la raccolta di dati per il processo specificato o per tutti i processi se non è specificato alcun processo.|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, non deve essere in corso alcuna raccolta di dati.  È possibile interrompere la raccolta dei dati da un'applicazione profilata con il metodo di campionamento chiudendo l'applicazione o richiamando l'opzione **VSPerfCmd \/detach**.  Richiamare quindi l'opzione **VSPerfCmd \/shutdown** per disattivare il profiler e chiudere il file dei dati di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Disconnettere il profiler dall'applicazione di destinazione chiudendolo o digitando il comando seguente:  
  
     **VSPerfCmd \/detach**  
  
2.  Arrestare il profiler digitando il comando seguente:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)