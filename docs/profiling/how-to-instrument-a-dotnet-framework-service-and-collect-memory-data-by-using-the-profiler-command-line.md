---
title: "Procedura: instrumentare un servizio .NET Framework e raccogliere dati di memoria tramite la riga di comando del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: instrumentare un servizio .NET Framework e raccogliere dati di memoria tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento viene illustrato come utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per instrumentare un servizio di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e raccogliere dati sull'utilizzo della memoria.  È possibile raccogliere dati sull'allocazione di memoria o sia i dati sull'allocazione di memoria sia quelli sulla durata degli oggetti.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Non è possibile eseguire il profilo di un servizio con il metodo di strumentazione se il servizio non può essere riavviato dopo l'avvio del computer, ad esempio un servizio che viene avviato all'avvio del sistema operativo.  
>   
>  Gli strumenti da riga di comando degli strumenti di profilatura sono contenuti nella sottodirectory \\Team Tools\\Performance Tools della directory di installazione di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Nei computer a 64 bit gli strumenti sono disponibili nelle versioni a 32 e 64 bit.  Per utilizzare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.  Per ulteriori informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Avvio della sessione di profilo  
 Per raccogliere dati di prestazioni da un servizio [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], utilizzare lo strumento [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) per inizializzare le variabili di ambiente appropriate e lo strumento [VSInstr.exe](../profiling/vsinstr.md) per creare una copia instrumentata del file binario del servizio.  
  
 È necessario riavviare il computer che ospita il servizio per configurarlo per il profilo.  È inoltre necessario avviare manualmente il servizio da Gestione controllo servizi.  Avviare il profiler, quindi avviare il servizio [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Quando viene eseguito il componente instrumentato, i dati di memoria vengono raccolti automaticamente in un file di dati.  È possibile sospendere e riprendere la raccolta dei dati durante la sessione di profilo.  
  
 Per terminare una sessione di profilo, chiudere il servizio e arrestare in modo esplicito il profiler.  Nella maggior parte dei casi, è consigliabile cancellare le variabili di ambiente di profilo alla fine di una sessione.  
  
#### Per avviare il profilo di un servizio .NET Framework  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Utilizzare lo strumento **VSInstr** per generare una versione instrumentata del file binario del servizio.  
  
3.  Utilizzare Gestione controllo servizi per sostituire il file binario originale con la versione instrumentata.  Assicurarsi che il tipo di avvio del servizio sia impostato su Manuale.  
  
4.  Inizializzare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv** {**\/globaltracegc** &#124; **\/globaltracegclife**}  
  
    -   **\/globaltracegc** e **\/globaltracegclife** consentono la raccolta di dati sull'allocazione di memoria e la durata degli oggetti.  
  
        |Opzione|Descrizione|  
        |-------------|-----------------|  
        |**\/globaltracegc**|Raccoglie unicamente i dati sull'allocazione di memoria.|  
        |**\/globaltracegclife**|Raccoglie i dati sull'allocazione di memoria e sulla durata degli oggetti.|  
  
5.  Riavviare il computer.  
  
6.  Aprire una finestra del prompt dei comandi.  
  
7.  Avviare il profiler.  Tipo:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:trace**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   L'opzione **\/start: contention** consente di inizializzare il profiler.  
  
    -   L'opzione **\/output:**`OutputFile` è obbligatoria con **\/start**.  `OutputFile` specifica il nome e il percorso del file dei dati di profilo \(vsp\).  
  
     È possibile utilizzare qualsiasi opzione riportata di seguito con l'opzione **\/start:sample**.  
  
    > [!NOTE]
    >  Le opzioni **\/user** e **\/crosssession** sono in genere obbligatorie per i servizi.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Specifica il dominio e il nome utente dell'account proprietario del processo di lavoro ASP.NET.  Questa opzione è obbligatoria se il processo è in esecuzione come un utente diverso dall'utente connesso.  Il proprietario del processo è elencato nella colonna Nome utente della scheda Processi di Gestione attività di Windows.|  
    |[\/crosssession](../profiling/crosssession.md)|Abilita il profilo dei processi in altre sessioni di accesso.  Questa opzione è obbligatoria se l'applicazione ASP.NET è in esecuzione in una sessione diversa.  L'ID di sessione è elencato nella colonna ID sessione della scheda Processi di Gestione attività di Windows.  È possibile specificare **\/CS** come abbreviazione per **\/crosssession**.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Specifica il numero di secondi di attesa prima che il profiler venga inizializzato prima che venga restituito un errore.  Se `Interval` non è specificato, il profiler attenderà un periodo di tempo indefinito.  Per impostazione predefinita, **\/start** viene immediatamente restituito.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Per avviare il profiler con la raccolta dei dati in pausa, aggiungere l'opzione **\/globaloff** alla riga di comando **\/start**.  Utilizzare **\/globalon** per riprendere il profilo.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Raccoglie informazioni dal contatore delle prestazioni del processore specificato in Config.  Le informazioni del contatore vengono aggiunte ai dati raccolti a ogni evento di profilo.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifica un contatore delle prestazioni Windows di cui raccogliere i dati durante il profilo.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Utilizzare unicamente con **\/wincounter**.  Specifica il numero di millisecondi tra gli eventi di raccolta dati del contatore delle prestazioni Windows.  Il valore predefinito è 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifica un evento Traccia eventi per Windows \(ETW\) di cui raccogliere i dati durante il profilo.  Gli eventi ETW vengono raccolti in un file separato con estensione etl.|  
  
8.  Se necessario, avviare il servizio.  
  
9. Connettere il profiler al servizio.  Tipo:  
  
     **VSPerfCmd \/attach:** `PID` &#124;`ProcessName`  
  
    -   Specifica l'ID o il nome del processo del servizio.  È possibile visualizzare gli ID e i nomi di tutti i processi in esecuzione in Gestione attività di Windows.  
  
## Controllo della raccolta di dati  
 Quando il servizio è in esecuzione, è possibile controllare la raccolta dei dati avviando e interrompendo la scrittura di dati nel file utilizzando le opzioni di **VSPerfCmd.exe**.  Controllando la raccolta dei dati, è possibile raccogliere dati per una parte specifica dell'esecuzione del programma, ad esempio l'avvio o l'arresto dell'applicazione.  
  
#### Per avviare e interrompere la raccolta dei dati  
  
-   Le coppie seguenti di opzioni di **VSPerfCmd** avviano e interrompono la raccolta dei dati.  Specificare ogni opzione in una riga di comando separata.  È possibile attivare e disattivare più volte la raccolta dei dati.  
  
    |Opzione|Descrizione|  
    |-------------|-----------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Avvia \(**\/globalon**\) o interrompe \(**\/globaloff**\) la raccolta dei dati per tutti i processi.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Avvia \(**\/processon**\) o interrompe \(**\/processoff**\) la raccolta dei dati per il processo specificato dall'ID processo \(`PID`\).|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID`  [\/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Avvia \(**\/threadon**\) o interrompe \(**\/threadoff**\) la raccolta dei dati per il thread specificato dall'ID thread \(`TID`\).|  
  
## Fine della sessione di profilo  
 Per terminare una sessione di profilo, chiudere l'applicazione che esegue il componente instrumentato, quindi avviare l'opzione **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) per disattivare il profiler e chiudere il file dei dati di profilo.  Il comando **VSPerfClrEnv \/globaloff** cancella le variabili di ambiente di profilo.  
  
#### Per terminare una sessione di profilo  
  
1.  Arrestare il servizio da Gestione controllo servizi.  
  
2.  Arrestare il profiler.  Tipo:  
  
     **VSPerfCmd \/shutdown**  
  
3.  Dopo avere completato tutte le attività di profilo, cancellare le variabili di ambiente di profilo.  Tipo:  
  
     **VSPerfClrEnv \/globaloff**  
  
     Sostituire il modulo instrumentato con l'originale.  Se necessario, riconfigurare il tipo di avvio del servizio.  
  
4.  Riavviare il computer.  
  
## Vedere anche  
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)