---
title: "VSPerfCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "riga di comando, strumenti"
  - "strumenti della riga di comando, VSPerfCmd (strumento)"
  - "strumenti di prestazioni, VSPerfCmd (strumento)"
  - "strumenti di profilatura, VSPerfCmd"
  - "VSPerfCmd (strumento)"
ms.assetid: 778bc105-7643-46c4-a338-f3620e31125a
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento **VSPerfCmd.exe** consente di avviare e interrompere la raccolta dei dati relativi alle prestazioni  e utilizza la sintassi seguente:  
  
```  
VSPerfCmd [/U] [/options]  
```  
  
 Nelle tabelle seguenti vengono descritte le opzioni dello strumento **VSPerfCmd.exe**.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**U**|L'output della console reindirizzato viene scritto come Unicode.  Deve essere la prima opzione specificata.|  
|[Inizia](../profiling/start.md) **:** `mode`|Avvia il servizio di profilatura nella modalità specificata.|  
|[Output](../profiling/output.md) **:** `filename`|Specifica il nome del file di output.  Utilizzare solo con **Start**.|  
|[CrossSession&#124;CS](../profiling/crosssession.md)|Abilita la profilatura tra sessioni di Windows.  Utilizzare solo con **Start Attach or Launch**.|  
|[Utente](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Consente all'account specificato di accedere al servizio profiler.  Utilizzare solo con **Start**.|  
|[WaitStart](../profiling/waitstart.md)\[**:**`n`\]|Attende l'inizializzazione del logger di raccolta dei dati.  Se si specifica `n`, **VSPerfCmd** attende al massimo `n` secondi.  Se `n` non viene specificato, l'attesa di **VSPerfCmd** è infinita.  In questo modo viene semplificato l'utilizzo di **VSPerfCmd** come parte di un processo batch.|  
|[Contatore](../profiling/counter.md) **:** `cfg`|Quando si utilizza il metodo di profilatura tramite campionamento, specifica un contatore CPU e il numero di eventi da utilizzare come intervallo di campionamento.  È possibile campionare solo il valore di un contatore.<br /><br /> Quando si utilizza il metodo di profilatura tramite strumentazione, specifica un contatore CPU di cui raccogliere di dati per ogni punto di strumentazione.  Utilizzare solo con **Start:**`Trace`, **Attach**  o **Launch**.|  
|[QueryCounters](../profiling/querycounters.md)|Visualizza un elenco di contatori CPU validi per il computer corrente.|  
|[WinCounter](../profiling/wincounter.md) **:** *path*|Specifica un evento del contatore delle prestazioni di Windows da includere con i dati di contrassegno del profilo.  Utilizzare solo con **Start**.|  
|[AutoMark](../profiling/automark.md) **:** *n*|Specifica l'intervallo di tempo \(in millisecondi\) tra gli eventi di raccolta dei dati del contatore delle prestazioni di Windows.  Utilizzare con **WinCounter**.|  
|[Eventi](../profiling/events-vsperfcmd.md) **:** `option`|Controlla la raccolta di eventi ETW \(Event Tracing for Windows\) specificati.  I dati ETW vengono raccolti in un file con estensione itl, che non è il file di dati di profilatura \(con estensione vsp\).|  
|[Stato](../profiling/status.md)|Visualizza lo stato del profiler, informazioni sui processi attualmente profilati e gli account che dispongono dell'autorità per controllare il profiler.|  
|[Shutdown](../profiling/shutdown.md)\[**:**`n`\]|Chiude il file di dati di profilatura e disattiva il profiler.|  
|[GlobalOn](../profiling/globalon-and-globaloff.md)|Riprende la raccolta dei dati dopo una chiamata a **VSPerfCmd GlobalOff**.|  
|[GlobalOff](../profiling/globalon-and-globaloff.md)|Interrompe la raccolta di tutti i dati, ma senza terminare la sessione di profilatura.|  
|[ProcessOn](../profiling/processon-and-processoff.md) **:** `pid`|Riprende la raccolta dei dati per il processo specificato in seguito alla sospensione della profilatura per una chiamata a **VSPerfCmd ProcessOff**.|  
|[ProcessOff](../profiling/processon-and-processoff.md) **:** `pid`|Interrompe la raccolta dei dati per il processo specificato.|  
|[ThreadOn e ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Riprende la profilatura per il processo specificato in seguito alla sospensione a causa di una chiamata a **VSPerfCmd ThreadOff**.  Utilizzare **ThreadOn** solo quando si esegue la profilatura con il metodo di strumentazione.|  
|[ThreadOn e ThreadOff](../profiling/threadon-and-threadoff.md) **:** *tid*|Sospende la profilatura per il thread specificato.  Utilizzare **ThreadOff** solo quando si esegue la profilatura con il metodo di strumentazione.|  
|[Contrassegno](../profiling/mark.md) **:** *MarkNum*\[**,***MarkText***\]**|Inserisce un contrassegno nel file di dati di profilatura, con testo facoltativo.|  
  
## Opzioni del metodo di campionamento  
 Le opzioni seguenti sono disponibili solo quando si utilizza il metodo di profilatura tramite campionamento.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|[Avvio](../profiling/launch.md) **:** *Executable*|Avvia l'applicazione specificata e la profilatura.|  
|[Args](../profiling/args.md) **:** *Arguments*|Specifica gli argomenti della riga di comando da passare all'applicazione avviata.|  
|[Console](../profiling/console.md)|Avvia il comando specificato in una nuova finestra del prompt dei comandi.|  
|[Attach](../profiling/attach.md) **:** *PID*\[**,***PID*\]|Avvia la profilatura dei processi specificati.  È possibile identificare i processi tramite l'ID di processo o il nome di processo.|  
|[Detach](../profiling/detach.md)\[**:***PID*\[,*PID*\]\]|Interrompe la profilatura dei processi specificati.  È possibile identificare i processi tramite l'ID di processo o il nome di processo.  Se non è specificato alcun processo, viene interrotta la profilatura per tutti i processi.|  
|[GC](../profiling/gc-vsperfcmd.md)\[**:**{**Allocation** `&#124;` **Lifetime**}\]|Raccoglie i dati relativi all'allocazione di memoria .NET e alla durata degli oggetti.  Utilizzare solo con l'opzione **VSPerfCmd Launch**.|  
  
### Opzioni relative agli intervalli di campionamento  
 Le opzioni seguenti consentono di specificare il tipo e la durata degli intervalli di campionamento.  Il valore predefinito è **Timer**.  È inoltre possibile specificare un contatore CPU come intervallo utilizzando l'opzione **Counter**.  È possibile specificare queste opzioni solo con **Launch** o con la prima opzione **Attach** di una sessione di profilatura.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|[PF](../profiling/pf.md)\[**:***n*\]|Esegue il campionamento su ogni n errore di pagina \(impostazione predefinita \= 10\).|  
|[Sys](../profiling/sys-vsperfcmd.md)\[**:***n*\]|Esegue il campionamento su ogni n chiamata di sistema \(impostazione predefinita \= 10\).|  
|[Timer](../profiling/timer.md)\[**:***n*\]|Esegue il campionamento a ogni ennesimo ciclo del processore \(impostazione predefinita \= 10000000\).|  
  
## Opzioni del dispositivo della modalità kernel e del componente del servizio  
 Le opzioni Admin seguenti supportano la profilatura di componenti del servizio o di driver di dispositivo in modalità kernel.  Tali opzioni consentono di impostare autorizzazioni di profilatura e di controllare il servizio o il driver di dispositivo profilato.  
  
 Le opzioni Admin devono essere eseguite al prompt dei comandi, eseguito con credenziali amministrative.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Admin:Security** \<**ALLOW&#124;DENY**\> *Right*\[ *Right*\] \<*User*&#124;*Group*\>|Consente o nega all'utente o al gruppo specificato di accedere ai servizi di profilatura.<br /><br /> `Right` può essere:<br /><br /> CrossSession: consente all'utente di accedere al servizio per eseguire profilatura tra sessioni.<br /><br /> SampleProfiling: consente all'utente di accedere al driver per abilitare la profilatura mediante campionamento.  Viene utilizzata anche per accedere a informazioni relative alla transizione del kernel durante la profilatura.<br /><br /> FullAccess: consente all'utente di accedere alla CrossSession e alla SampleProfiling.|  
|**Admin:Security, List**|Elenca la stato corrente dei servizi di profilatura e le autorizzazioni utente.|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>\<**START**&#124;**STOP**&#124;**INSTALL**&#124;**UNINSTALL**\>|Avvia, interrompe, installa o disinstalla il componente del servizio di profilatura \(servizio\) o il driver di periferica della modalità kernel \(driver\).|  
|**Admin:**  `` \<*Service*&#124;*Driver*\>**AutoStart** `` \<**ON**&#124;**OFF**\>|Abilitare o disabilitare automaticamente l’avvio del servizio di profilatura \(servizio\) o del driver di periferica della modalità kernel \(driver\) dopo un riavvio.|  
  
## VSPerfCmd \/Driver  
 L'opzione **VSPerfCmd \/Driver** è obsoleta.  Utilizzare le opzioni **VsPerfCmd Admin** per questa funzionalità.  
  
## Vedere anche  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfReport](../profiling/vsperfreport.md)