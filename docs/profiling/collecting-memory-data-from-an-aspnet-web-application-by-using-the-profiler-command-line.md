---
title: "Raccolta di dati di memoria da un&#39;applicazione Web ASP.NET tramite la riga di comando del profiler | Microsoft Docs"
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
  - ".NET (metodo di profilatura della memoria)"
  - "strumenti di profilatura, .NET (metodo di memoria)"
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di dati di memoria da un&#39;applicazione Web ASP.NET tramite la riga di comando del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono illustrate le procedure e le opzioni per la raccolta di dati sull'allocazione di memoria e sulla durata di oggetti per un'applicazione Web ASP.NET tramite lo strumento da riga di comando **VSPerfCmd**.  
  
> [!NOTE]
>  Lo strumento **VSPerfCmd** fornisce l'accesso completo alla funzionalità degli strumenti di profilatura, incluse le operazioni di pausa e ripresa della profilatura e la raccolta di dati aggiuntivi da contatori di prestazioni di Windows e del processore.  È inoltre possibile utilizzare lo strumento da riga di comando **VSPerfASPNETCmd** quando questa funzionalità non è necessaria.  Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer.  Per ulteriori informazioni, vedere [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Connettere il profiler a un'applicazione ASP.NET in esecuzione**|-   [Procedura: collegare il profiler a un'applicazione Web ASP.NET per raccogliere dati di memoria](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentare file binari compilati in modo statico**|-   [Procedura: instrumentare un'applicazione ASP.NET compilata in modo statico e raccogliere dati di memoria](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentare file binari compilati in modo dinamico**|-   [Procedura: instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## Attività correlate  
  
### Profilo di applicazioni Web ASP.NET  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo tramite il metodo di campionamento**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Eseguire il profilo tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Eseguire il profilo di conflitti di risorse e attività dei thread**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Profilo di dati di memoria .NET Framework  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo di applicazioni \(client\) autonome**|-   [Raccolta di dati di memoria .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Eseguire il profilo di servizi**|-   [Raccolta di dati di memoria .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### Analisi dei rapporti e delle visualizzazioni dei dati di memoria .NET  
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)  
  
## Riferimento  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)