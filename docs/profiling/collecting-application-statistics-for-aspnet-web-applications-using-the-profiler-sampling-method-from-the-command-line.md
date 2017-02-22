---
title: "Raccolta di statistiche di applicazioni Web ASP.NET usando il metodo di campionamento del profiler tramite la riga di comando | Microsoft Docs"
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
  - "strumenti per la profilatura, metodo di campionamento"
  - "profilatura del campionamento (metodo)"
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Raccolta di statistiche di applicazioni Web ASP.NET usando il metodo di campionamento del profiler tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono illustrate le procedure e le opzioni per la raccolta di statistiche sulle prestazioni per un'applicazione Web ASP.NET tramite lo strumento da riga di comando **VSPerfASPNETCmd** e **VSPerfCmd** command\-line tool il metodo di profilatura del campionamento.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Sebbene lo strumento **VSPerfCmd** fornire completato l'accesso alle funzionalità degli strumenti di profilatura, incluse le operazioni di pausa e ripresa della profilatura e la raccolta di dati aggiuntivi dal processore e i contatori delle prestazioni di Windows, è possibile utilizzare lo strumento da riga di comando **VSPerfASPNETCmd** quando questa funzionalità non è necessaria.  Lo strumento da riga di comando **VSPerfASPNETCmd** è il metodo preferito da utilizzare per profilare siti Web ASP.NET tramite il profiler autonomo.  Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer.  Per ulteriori informazioni, vedere [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Connettere il profiler a un'applicazione ASP.NET**|-   [Procedura: collegare il profiler a un'applicazione Web ASP.NET per raccogliere statistiche dell'applicazione](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## Attività correlate  
  
### Profilo di applicazioni Web ASP.NET  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo tramite il metodo di strumentazione**|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line.md)|  
|**Eseguire il profilo dell'allocazione di memoria e dell'operazione di Garbage Collection**|-   [Raccolta di dati di memoria](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Eseguire il profilo di conflitti di risorse e attività dei thread**|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### Metodo di campionamento  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo di applicazioni \(client\) autonome**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|-   **Eseguire il profilo di servizi**|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### Analisi dei rapporti e delle visualizzazioni dei dati di campionamento  
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)