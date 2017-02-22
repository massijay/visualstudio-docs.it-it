---
title: "Raccolta di dati di concorrenza per un servizio tramite la riga di comando del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di dati di concorrenza per un servizio tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo di concorrenza degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di raccogliere dati su conflitti di risorse e attività dei thread che mostrano l'utilizzo della CPU, i conflitti dei thread, la migrazione dei thread, i ritardi di sincronizzazione, le aree di sovrapposizione delle operazioni di I\/O e altri eventi di sistema.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Connettersi a un servizio .NET in esecuzione**|-   [Procedura: collegare il profiler a un servizio .NET per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Aggiungere dati di interazione tra livelli**|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Connettersi a un servizio C\/C\+\+ in esecuzione**|-   [Procedura: collegare il profiler a un servizio nativo per raccogliere dati di concorrenza](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## Attività correlate  
  
### Profilo dei servizi Windows  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Eseguire il profilo tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Eseguire il profilo dell'allocazione di memoria .NET e dell'operazione di Garbage Collection**|-   [Raccolta di dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Profilo dei dati di concorrenza  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Profilo di applicazioni autonome**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Eseguire il profilo di applicazioni Web ASP.NET**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Analisi dei rapporti e delle visualizzazioni dei dati di concorrenza  
 [Visualizzazioni dei dati su conflitti tra risorse](../profiling/resource-contention-data-views.md)  
  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)  
  
## Riferimento  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)