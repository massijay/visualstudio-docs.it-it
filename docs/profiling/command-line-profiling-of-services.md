---
title: "Profilatura dei servizi tramite riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, servizi"
  - "profilatura di servizi"
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Profilatura dei servizi tramite riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono illustrate le procedure e le opzioni per la raccolta dei dati delle prestazioni per i servizi di Windows utilizzando gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da riga di comando.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Raccogliere statistiche dell'applicazione:** utilizzare il metodo di campionamento per raccogliere le statistiche sulle prestazioni.  Il campionamento dei dati è utile per l'analisi dei problemi relativi all'utilizzo della CPU e per capire le caratteristiche generali delle prestazioni di un'applicazione.|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Raccogliere dati di intervallo dettagliati:** utilizzare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate.  I dati di strumentazione sono utili per l'analisi dei problemi di IO e per l'analisi dettagliata degli scenari di applicazioni.|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Raccogliere dati di memoria .NET:** utilizzare il campionamento o la strumentazione per raccogliere dati sull'allocazione di memoria .NET che illustrano le dimensioni e il numero degli oggetti allocati.  È inoltre possibile raccogliere dati sulla durata degli oggetti che illustrano le dimensioni e il numero degli oggetti recuperati in ogni generazione Garbage Collection.|-   [Raccolta di dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Raccogliere dati di concorrenza:** utilizzare il metodo di concorrenza per raccogliere i dati dei conflitti di risorse e dell'attività dei thread che riguardano l'utilizzo della CPU, i conflitti di thread, la migrazione dei thread, i ritardi della sincronizzazione, le aree di I\/O sovrapposte e altri eventi di sistema.|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati di prestazioni relativi alle chiamate sincrone ADO.NET effettuate dal servizio a un database di Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## Attività correlate  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo di applicazioni \(client\) autonome**|-   [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Eseguire il profilo di applicazioni ASP.NET**|-   [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|