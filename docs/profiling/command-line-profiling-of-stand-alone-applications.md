---
title: "Profilatura della riga di comando di applicazioni autonome | Microsoft Docs"
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
  - "strumenti per la profilatura, applicazioni autonome"
  - "profilatura di applicazioni autonome"
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Profilatura della riga di comando di applicazioni autonome
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione vengono illustrate le procedure e le opzioni per la raccolta dei dati delle prestazioni per le applicazioni \(client\) autonome utilizzando gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da riga di comando.  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Raccogliere statistiche dell'applicazione:** utilizzare il metodo di campionamento per raccogliere le statistiche sulle prestazioni.  Il campionamento dei dati è utile per l'analisi dei problemi relativi all'utilizzo della CPU e per capire le caratteristiche generali delle prestazioni di un'applicazione.|-   [Raccolta di statistiche dell'applicazione tramite campionamento](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Raccogliere dati di intervallo dettagliati:** utilizzare il metodo di strumentazione per raccogliere informazioni di intervallo dettagliate.  I dati di strumentazione sono utili per l'analisi dei problemi di I\/O e per l'analisi dettagliata degli scenari di applicazioni.|-   [Raccolta di dati di intervallo dettagliati tramite strumentazione](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**Raccogliere dati di memoria .NET:** utilizzare il campionamento o la strumentazione per raccogliere dati sull'allocazione di memoria .NET che illustrano le dimensioni e il numero degli oggetti allocati.  È inoltre possibile raccogliere dati sulla durata degli oggetti che illustrano le dimensioni e il numero degli oggetti recuperati in ogni generazione Garbage Collection.|-   [Raccolta di dati di memoria .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Raccogliere dati di concorrenza:** utilizzare il metodo di concorrenza per raccogliere i dati dei conflitti di risorse e dell'attività dei thread che riguardano l'utilizzo della CPU, i conflitti di thread, la migrazione dei thread, i ritardi della sincronizzazione, le aree di I\/O sovrapposte e altri eventi di sistema.|-   [Raccolta di dati di concorrenza](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Aggiungere dati di interazione tra livelli:** è possibile aggiungere dati di prestazioni relativi alle chiamate sincrone ADO.NET effettuate dall'applicazione a un database di Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)].  Aggiungere dati di interazione tra livelli a un'esecuzione del profilo richiede le procedure specifiche con gli strumenti di profilatura della riga di comando.|-   [Raccolta di dati di interazione tra livelli](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Fare una prova:**  utilizzare procedure dettagliate per eseguire il profilo di un'applicazione client di esempio tramite il metodo di strumentazione o campionamento.|-   [Procedura dettagliata: Profilatura dalla riga di comando tramite campionamento](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Procedura dettagliata: Profilatura dalla riga di comando tramite strumentazione](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## Attività correlate  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Eseguire il profilo di applicazioni ASP.NET**|-   [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Eseguire il profilo di servizi**|-   [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)|