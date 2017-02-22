---
title: "Propriet&#224; della sessione di prestazioni | Microsoft Docs"
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
  - "strumenti per la profilatura, proprietà"
  - "proprietà (pagine), strumenti per la profilatura"
  - "strumenti per le prestazioni, proprietà della sessione di prestazioni"
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Propriet&#224; della sessione di prestazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una **sessione di prestazioni** consente di configurare le impostazioni che determinano la modalità di profilo dell'applicazione  e di memorizzare i rapporti generati per una sessione di profilo.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Creare una **sessione di prestazioni**, eseguendo la **Creazione guidata sessione di prestazioni** o creando manualmente una sessione.  La **Sessione prestazioni** viene visualizzata in **Esplora prestazioni** una volta creata la **Sessione prestazioni**.  
  
 Per visualizzare le proprietà della **sessione di prestazioni**, selezionare il nome della sessione in **Esplora prestazioni**, fare clic con il pulsante destro del mouse e scegliere **Proprietà**.  
  
 La sessione di prestazioni presenta le pagine delle proprietà seguenti:  
  
## Generale  
 Queste impostazioni consentono di selezionare il metodo di profilatura, aggiungere i dati della durata e della raccolta dell'oggetto .NET e specificare la posizione e le convenzioni di denominazione predefinite del rapporto.  
  
 Per ulteriori informazioni, vedere:  
  
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)  
  
 [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## Avvio  
 Queste impostazioni consentono di scegliere da un elenco di binari e di specificare il relativo ordine di avvio.  
  
 Per ulteriori informazioni, vedere [Procedura: Specificare l'inizio del file binario](../profiling/how-to-specify-the-binary-to-start.md).  
  
## Campionamento  
 Quando si utilizza il metodo di analisi mediante campionamento, queste impostazioni consentono di selezionare l'intervallo di campionamento e l'evento di esempio.  Un evento di esempio viene utilizzato per raccogliere i dati di analisi in un intervallo specifico.  Se, ad esempio, l'evento di esempio è costituito dai cicli di clock e l'intervallo di campionamento è impostato su 10.000.000, i dati di analisi verranno raccolti ogni 10 milioni di cicli di clock.  Sono disponibili i quattro tipi di eventi di esempio riportati di seguito.  
  
-   Cicli di clock per i problemi legati alla CPU  
  
-   Errori di pagina per i problemi relativi alla memoria  
  
-   Chiamate di sistema per i problemi associati all'I\/O  
  
-   Contatori di prestazioni per i problemi di prestazioni ridotte  
  
-   Eventi di esempio aggiuntivi possono essere specificati in base ai contatori delle prestazioni disponibili.  
  
 Per ulteriori informazioni, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md).  
  
## Binary  
 Queste impostazioni consentono di specificare se si desidera rilocare il binario instrumentato in un'altra posizione.  Se, ad esempio, si esegue il profilo di My.DLL e si sceglie di non rilocare il binario instrumentato, viene creata una copia di backup di My.DLL denominata My.Orig.DLL.  Successivamente My.DLL viene modificato con l'inserimento di controlli per la raccolta di dati.  Se si sceglie di rilocare il binario instrumentato, il binario originale non viene rinominato e il binario instrumentato viene copiato nel percorso specificato in modo da essere utilizzato durante la strumentazione.  
  
 Per ulteriori informazioni, vedere [Procedura: Specificare l'inizio del file binario](../profiling/how-to-specify-the-binary-to-start.md).  
  
## Interazioni tra livelli  
 Per ulteriori informazioni, vedere [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md).  
  
## Strumentazione  
 Queste impostazioni consentono di raccogliere dati sulle prestazioni per il codice JScript nelle pagine Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e specificare gli eventi **pre\-strumentazione** e **post\-strumentazione** che devono verificarsi prima o dopo il processo di strumentazione.  
  
 Per ulteriori informazioni, vedere:  
  
 [Procedura: Profilare codice JavaScript \(ECMA\) nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Procedura: Specificare comandi pre\- e post\-strumentazione](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## Contatori della CPU  
 Queste impostazioni consentono di raccogliere dati sui contatori di prestazioni CPU quando si utilizza il metodo di profilo basato su strumentazione.  I contatori di prestazioni portabili sono disponibili indipendentemente dalla progettazione o dal produttore della CPU.  Gli eventi piattaforma sono specifici della progettazione e del produttore della CPU.  Per ulteriori informazioni sui contatori di prestazioni relativi al processore, vedere la documentazione relativa al processore specifico.  
  
 Per ulteriori informazioni, vedere [Procedura: Raccogliere i dati dei contatori CPU](../profiling/how-to-collect-cpu-counter-data.md).  
  
## Eventi Windows  
 Durante l'analisi, è possibile raccogliere i dati dai provider di tracce eventi.  Per visualizzare tali dati è possibile utilizzare lo strumento della riga di comando VSPerfReport.exe `/calltrace`.  Per ulteriori informazioni su Event Tracing for Windows \(ETW\), vedere [Sulla traccia degli eventi](http://go.microsoft.com/fwlink/?linkid=90752).  
  
 Per ulteriori informazioni, vedere:  
  
 [Procedura: Raccogliere dati ETW \(Event Tracing for Windows\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## Contatori Windows  
 Questa opzione consente di raccogliere dati dai contatori Performance Monitor di Windows.  Per raccogliere questi dati, selezionare la casella di controllo **Raccogli contatori delle prestazioni Windows**.  L'intervallo di raccolta può essere impostato nella casella **Intervallo di raccolta**.  Potrebbero essere inoltre disponibili **Categoria del contatore** e **Istanza**.  Sono disponibili alcuni contatori predefiniti di Performance Monitor di Windows.  
  
 Per ulteriori informazioni, vedere [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
## Avanzate  
 Queste impostazioni consentono di aggiungere opzioni al processo di strumentazione specificando uno o più opzioni dello strumento di analisi della riga di comando [VSInstr](../profiling/vsinstr.md).  È inoltre possibile specificare la versione di Common Runtime di cui eseguire il profilo quando l'applicazione utilizza più di una versione.  
  
 Per ulteriori informazioni, vedere:  
  
 [Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side\-by\-side](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## Vedere anche  
 [Cenni preliminari](../profiling/overviews-performance-tools.md)   
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)