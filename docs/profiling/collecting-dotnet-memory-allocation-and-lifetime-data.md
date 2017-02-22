---
title: "Raccolta di dati di durata e allocazione di memoria .NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET (metodo di profilatura della memoria)"
  - "strumenti per la profilatura, metodo memoria .NET"
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di dati di durata e allocazione di memoria .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è supportata la raccolta di dati sull'allocazione di memoria .NET e sulla durata di oggetti allo scopo di rilevare i problemi di prestazioni correlati alla memoria che si verificano nell'applicazione.  
  
-   I dati sull'allocazione di memoria .NET includono le dimensioni e il numero di oggetti di memoria .NET Framework che sono stati allocati.  
  
-   I dati sulla durata degli oggetti includono invece le dimensioni e il numero di oggetti di memoria .NET Framework recuperati nelle tre generazioni di Garbage Collection.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 È possibile raccogliere dati tramite il metodo di profilo basato su campionamento o su strumentazione.  
  
-   Quando si utilizza il metodo di campionamento, il profiler tiene traccia di tutti gli oggetti e di tutte le allocazioni di memoria .NET generati dal processo avviato o connesso al profiler.  
  
-   Quando si utilizza il metodo di strumentazione, il profiler tiene traccia solo degli oggetti e delle allocazioni di memoria .NET generati dai moduli instrumentati.  
  
> [!IMPORTANT]
>  Quando si raccolgono dati di memoria .NET \(allocazioni, durata degli oggetti o entrambe\) utilizzando il metodo di campionamento, tutti gli eventi di campionamento specificati dall'utente vengono ignorati e gli eventi di allocazione di memoria appropriati vengono utilizzati per raccogliere dati.  
  
 Se si abilita il profilo dell'allocazione di memoria .NET, si abilita anche la visualizzazione Allocazione.  Se si abilita il profilo dei dati sulla durata degli oggetti .NET, si abilita anche la visualizzazione Durata oggetti.  Per ulteriori informazioni, vedere [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md) e [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md).  
  
 Per informazioni sulla raccolta dei dati di memoria .NET tramite gli strumenti da riga di comando disponibili negli strumenti di profilatura, vedere Utilizzo dei metodi di memoria .NET per raccogliere i dati sull'allocazione di memoria e sulla durata degli oggetti in [Utilizzo di metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### Per raccogliere dati di memoria .NET  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo *Performance Session***Pagine delle proprietà** , fare clic sulla scheda **Generale** e selezionare la casella di controllo **Raccogliere le informazioni sull'allocazione dell'oggetto .NET**.  
  
3.  Per raccogliere i dati sulla durata degli oggetti .NET, selezionare la casella di controllo **Raccogliere anche le informazioni sulla durata dell'oggetto .NET**.  
  
## Attività comuni  
 È possibile specificare opzioni aggiuntive nella finestra di dialogo **Pagine delle proprietà** di *Performance Session* della sessione di prestazioni.  Per aprire questa finestra di dialogo:  
  
-   In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e scegliere **Proprietà**.  
  
 Le attività nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo *Performance Session* **Pagine delle proprietà** quando si raccolgono i dati di memoria .NET.  
  
|Attività|Contenuto correlato|  
|--------------|-------------------------|  
|Nella pagina **Generale**, specificare i dettagli di denominazione per il file dei dati di profilo \(vsp\) generato.|-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Nella pagina **Avvio** scegliere l'applicazione da avviare se si dispone di più progetti EXE nella soluzione del codice.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Interazione tra livelli**, aggiungere i dati di chiamata ADO.NET all'esecuzione di profilo.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Eventi Windows** specificare uno o più eventi Traccia eventi per Windows \(ETW\) da raccogliere con i dati di campionamento.|-   [Procedura: Raccogliere dati ETW \(Event Tracing for Windows\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Nella pagina **Contatori Windows**, specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilo come contrassegni.|-   [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework di cui eseguire il profilo se i moduli dell'applicazione utilizzano più versioni.  Per impostazione predefinita, viene eseguito il profilo della prima versione caricata.|-   [Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side\-by\-side](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## Attività di strumentazione  
 Le attività nella tabella seguente descrivono le opzioni della finestra di dialogo **Pagine delle proprietà** specifiche del profilo eseguito con il metodo di strumentazione.  
  
|Attività|Contenuto correlato|  
|--------------|-------------------------|  
|Nella pagina **Binari**, specificare un percorso per le copie instrumentate dei moduli.  Per impostazione predefinita, i binari originali vengono spostati in una cartella di backup.|-   [Procedura: Rilocare file binari instrumentati](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Nella pagina **Strumentazione**, escludere le piccole funzioni dal profilo per ridurre il sovraccarico di profilo, eseguire il profilo del codice JavaScript nelle pagine Web ASP.NET e specificare i comandi da eseguire in un prompt dei comandi prima e dopo il processo di strumentazione.|-   [Procedura: Escludere o includere funzioni brevi nella strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Procedura: Profilare codice JavaScript \(ECMA\) nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Procedura: Specificare comandi pre\- e post\-strumentazione](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Nella pagina **Contatori CPU**, specificare uno o più contatori di prestazioni del processore da aggiungere ai dati di profilo.|-   [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|Nella pagina **Avanzate** specificare le opzioni aggiuntive VSInstr.exe desiderate, ad esempio le opzioni per includere o escludere funzioni specifiche.  Per ulteriori informazioni sulle opzioni VSInstr, vedere [VSInstr](../profiling/vsinstr.md).|-   [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Procedura: Limitare la strumentazione a specifiche funzioni](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)   
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)