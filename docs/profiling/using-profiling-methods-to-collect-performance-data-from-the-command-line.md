---
title: "Utilizzo di metodi di profilatura per raccogliere dati di prestazioni tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5613fafc-f298-4e7a-9a2d-a853b61cdf9c
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Utilizzo di metodi di profilatura per raccogliere dati di prestazioni tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La scelta degli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e delle relative opzioni dipende da fattori quali il tipo di applicazione che si sta profilando, il metodo di profilatura che si desidera utilizzare e dal codice in cui è stata scritta l'applicazione di destinazione, ovvero codice nativo o codice di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 In questo argomento sono contenuti gli argomenti relativi alle procedure della riga di comando in base al metodo di profilo scelto.  
  
## In questo argomento  
 [Utilizzando il metodo di campionamento per raccogliere statistiche sulle prestazioni](#BKMK_Using_the_sampling_method_to_collect_performance_statistics)  
  
 [Utilizzo del metodo di strumentazione per raccogliere dati di intervallo dettagliati](#BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data)  
  
 [Utilizzo dei metodi di memoria.NET per raccogliere i dati sulla durata dell'allocazione di memoria e](#BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data)  
  
 [Utilizzando il metodo di concorrenza per raccogliere i dati su attività dei conflitti di thread e delle risorse](#BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data)  
  
 [Aggiungere dati di interazione tra livelli a un'esecuzione della profilatura](#BKMK_Adding_tier_interaction_data_to_a_profiling_run)  
  
##  <a name="BKMK_Using_the_sampling_method_to_collect_performance_statistics"></a> Utilizzando il metodo di campionamento per raccogliere statistiche sulle prestazioni  
 Il metodo di campionamento degli strumenti di profilatura raccoglie dati di prestazioni a intervalli specificati nell'esecuzione di una profilatura.  Attraverso il campionamento dei dati è possibile acquisire informazioni dettagliate sui problemi di prestazioni associati alla CPU, nonché esplorare le prestazioni di un'applicazione.  
  
 È possibile avviare il profiler e l'applicazione contemporaneamente oppure connettere il profiler a un'istanza in esecuzione di un'applicazione.  
  
|Task|Tipo di applicazione di destinazione|  
|----------|------------------------------------------|  
|**Avviare un'applicazione**|-   [Applicazioni autonome](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Connettersi a un processo in esecuzione**|-   [Applicazioni autonome .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Applicazioni autonome native](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)<br />-   [Applicazioni Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)<br />-   [Servizi nativi](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Using_the_instrumentation_method_to_collect_detailed_timing_data"></a> Utilizzo del metodo di strumentazione per raccogliere dati di intervallo dettagliati  
 Il metodo di strumentazione degli strumenti di profilatura consente di raccogliere dati di prestazioni da copie di binari dell'applicazione che contengono probe software per registrare informazioni sulle prestazioni.  I dati di strumentazione vengono raccolti all'inizio e alla fine di ogni funzione instrumentata e a ogni chiamata ad altre funzioni dalla funzione instrumentata.  Il metodo di strumentazione è utile per individuare i problemi di prestazioni di I\/O, ad esempio quelli correlati all'utilizzo del disco.  
  
 Creare il file binario instrumentato con lo strumento [VInstr.exe](../profiling/vsinstr.md).  Dopo avere inizializzato il profiler, i dati vengono raccolti automaticamente dai file binari instrumentati quando si esegue l'applicazione di destinazione.  
  
 **Tipo di applicazione di destinazione**  
  
-   [Componenti autonomi .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Componenti autonomi nativi](../profiling/how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line.md)  
  
-   [Applicazioni Web ASP.NET compilate in modo statico](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Applicazioni Web ASP.NET compilate in modo dinamico](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)  
  
-   [Servizi .NET](../profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
-   [Servizi nativi](../profiling/how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line.md)  
  
##  <a name="BKMK_Using__NET_memory_methods_to_collect_memory_allocation_and_object_lifetime_data"></a> Utilizzo dei metodi di memoria.NET per raccogliere i dati sulla durata dell'allocazione di memoria e  
 Il metodo di memoria .NET degli strumenti di profilatura consente di raccogliere dati sull'allocazione di memoria di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] e informazioni sulla durata di oggetti in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 È possibile avviare l'applicazione di destinazione tramite il profiler, connettere il profiler a un'istanza in esecuzione di un'applicazione e creare versioni instrumentate dell'applicazione per raccogliere dati di intervallo dettagliati e dati di memoria di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
|Task|Tipo di applicazione di destinazione|  
|----------|------------------------------------------|  
|**Avviare un'applicazione**|-   [Applicazioni .NET Framework autonome](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line.md)|  
|**Connettersi a un processo in esecuzione**|-   [Applicazioni autonome .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Applicazioni Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentare moduli**|-   [Componenti autonomi .NET Framework](../profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line.md)<br />-   [Applicazioni Web ASP.NET compilate in modo statico](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Applicazioni Web ASP.NET compilate in modo dinamico](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)<br />-   [Servizi .NET](../profiling/how-to-instrument-a-dotnet-framework-service-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
##  <a name="BKMK_Using_the_concurrency_method_to_collect_resource_contention_and_thread_activity_data"></a> Utilizzando il metodo di concorrenza per raccogliere i dati su attività dei conflitti di thread e delle risorse  
 Il metodo di concorrenza degli strumenti di profilatura consente di raccogliere dati sui conflitti di risorse e sull'attività dei thread da applicazioni multithread.  
  
 È possibile avviare l'applicazione utilizzando il profiler oppure connettere il profiler a un'istanza in esecuzione di un'applicazione.  
  
|Task|Tipo di applicazione di destinazione|  
|----------|------------------------------------------|  
|**Avviare un'applicazione**|-   [Applicazione .NET Framework autonoma](../profiling/how-to-launch-a-stand-alone-dotnet-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Applicazione nativa autonoma](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Connettersi a un processo in esecuzione**|-   [Applicazione autonoma .NET Framework](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Applicazione autonoma nativa](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Applicazione Web ASP.NET](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servizio .NET](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)<br />-   [Servizio nativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
##  <a name="BKMK_Adding_tier_interaction_data_to_a_profiling_run"></a> Aggiungere dati di interazione tra livelli a un'esecuzione della profilatura  
 Aggiungere dati di interazione tra livelli a un'esecuzione del profilo richiede le procedure specifiche con gli strumenti di profilatura della riga di comando.  Vedere [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)  
  
## Vedere anche  
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)