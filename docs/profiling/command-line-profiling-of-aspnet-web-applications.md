---
title: "Profilatura tramite riga di comando di applicazioni Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ASP.NET (profilatura di applicazioni)"
  - "strumenti per la profilatura, applicazioni ASP.NET"
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilatura tramite riga di comando di applicazioni Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono illustrate le procedure e le opzioni per la raccolta di dati delle prestazioni per le applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] utilizzando gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da riga di comando.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Raccogliere facilmente dati di profilatura ASP.NET di base:** utilizzare lo strumento **VSPerfASPNETCmd** per raccogliere dati di campionamento, strumentazione, memoria .NET, conflitto o di interazione tra livelli senza i requisiti di configurazione e i riavvii di Internet Information Services \(IIS\)  necessari per **VSPerfCmd**.  **VSPerfASPNETCmd** non consente di raccogliere dati aggiuntivi o di controllare la raccolta dei dati. **Note:**  **VSPerfASPNETCmd** è lo strumento da riga di comando preferito da utilizzare con il profiler autonomo per profilare siti Web ASP.NET.|-   [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Raccogliere statistiche dell'applicazione:** utilizzare il metodo di campionamento per raccogliere le statistiche sulle prestazioni.  Il campionamento dei dati è utile per l'analisi dei problemi di utilizzo della CPU e per comprendere le caratteristiche generali delle prestazioni di un'applicazione.|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Raccogliere dati di intervallo dettagliati:** utilizzare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate.  I dati di strumentazione sono utili per l'analisi dei problemi di IO e per l'analisi dettagliata degli scenari di applicazioni.|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Raccogliere dati di memoria .NET:** utilizzare il campionamento o la strumentazione per raccogliere dati sull'allocazione di memoria .NET che illustrano le dimensioni e il numero degli oggetti allocati.  È inoltre possibile raccogliere dati sulla durata degli oggetti che illustrano le dimensioni e il numero degli oggetti recuperati in ogni generazione Garbage Collection.|-   [Raccolta di dati di memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Raccogliere dati di concorrenza:** utilizzare il metodo di concorrenza per raccogliere i dati sui conflitti di risorse. **Note:**  La raccolta di dati su attività del thread e visualizzazione non è supportata per le applicazioni Web.|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati di prestazioni relativi alle chiamate sincrone di [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] effettuate dall'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] a un database di Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Attività correlate  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo di applicazioni \(client\) autonome**|-   [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Eseguire il profilo di servizi**|-   [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)|