---
title: "Raccolta di statistiche sulle prestazioni tramite il campionamento | Microsoft Docs"
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
  - "strumenti per la profilatura, campionamento"
  - "profilatura del campionamento (metodo)"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di statistiche sulle prestazioni tramite il campionamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, il metodo di campionamento degli strumenti di profilatura di [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] raccoglie informazioni di profilo ogni 10.000.000 cicli del processore \(circa ogni centesimo di secondo in un computer da 1 GHz\).  Il metodo di campionamento è utile per individuare i problemi correlati all'utilizzo del processore ed è il metodo consigliato per l'avvio della maggior parte delle analisi delle prestazioni.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 È possibile specificare il metodo di campionamento tramite una delle procedure riportate di seguito:  
  
-   Nella prima pagina della procedura guidata profilo, fare clic su **Campionamento CPU \(consigliato\)**.  
  
-   Scegliere **Campionamento** nell'elenco **Metodo** sulla barra degli strumenti **Esplora prestazioni**.  
  
-   Nella pagina **Generale** della finestra di dialogo delle proprietà per la sessione di prestazioni, fare clic su **Campionamento**.  
  
## Attività comuni  
 È possibile specificare opzioni aggiuntive nella finestra di dialogo **Pagine delle proprietà** di *Performance Session* della sessione di prestazioni.  Per aprire questa finestra di dialogo:  
  
-   In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni e scegliere **Proprietà**.  
  
 Le attività riportate nella tabella seguente descrivono le opzioni che è possibile specificare nella finestra di dialogo **Pagine delle proprietà** di *Performance Session* quando si esegue il profilo tramite il metodo di campionamento.  
  
|Attività|Contenuto correlato|  
|--------------|-------------------------|  
|Nella pagina **Generale**, aggiungere la raccolta di dati relativi alla durata e all'allocazione di memoria .NET e specificare i dettagli di denominazione per il file dei dati di profilo \(vsp\) generato.|-   [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Nella pagina **Campionamento**, modificare la frequenza di campionamento, l'evento di campionamento dai cicli di clock del processore a un altro contatore delle prestazioni del processore o modificare entrambe le impostazioni.|-   [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md)|  
|Nella pagina **Avvio**, specificare l'applicazione da avviare e l'ordine di avvio se si dispone di più progetti EXE nella soluzione del codice.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Interazione tra livelli**, aggiungere le informazioni di chiamata ADO.NET ai dati raccolti nell'esecuzione di profilo.|-   [Raccolta di dati di interazione tra livelli](../profiling/collecting-tier-interaction-data.md)|  
|Nella pagina **Eventi Windows** specificare uno o più eventi Traccia eventi per Windows \(ETW\) da raccogliere con i dati di campionamento.|-   [Procedura: Raccogliere dati ETW \(Event Tracing for Windows\)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Nella pagina **Contatori Windows**, specificare uno o più contatori di prestazioni del sistema operativo da aggiungere ai dati di profilo come contrassegni.|-   [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Nella pagina **Avanzate** specificare la versione del runtime di .NET Framework di cui eseguire il profilo se i moduli dell'applicazione utilizzano più versioni.  Per impostazione predefinita, viene eseguito il profilo della prima versione caricata.|-   [Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side\-by\-side](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|