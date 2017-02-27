---
title: "Controllo della raccolta dei dati negli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attività avanzate per strumenti di profilatura"
  - "strumenti di profilatura, attività avanzate"
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Controllo della raccolta dei dati negli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consentono di controllare quando i dati di profilatura vengono raccolti durante una sessione di prestazioni e di specificare le funzioni che vengono profilate.  In questa sezione viene descritto come avviare e interrompere la raccolta di dati da **Esplora prestazioni** e dalle finestre **Controllo raccolta dati** e come limitare gli oggetti di cui vengono raccolti i dati di profilatura.  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Avviare e interrompere la profilatura:** è possibile avviare la profilatura di un'applicazione all'avvio di quest'ultima oppure collegare il profiler a un processo già in esecuzione.  Quando l'applicazione di destinazione è in esecuzione, è possibile sospendere e riprendere la raccolta dei dati.  La sessione di profilatura può essere terminata chiudendo l'applicazione di destinazione o disconnettendo il profiler da un processo in esecuzione.|-   [Procedura: Avviare e terminare la profilatura](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Procedura: Connettere e disconnettere il profiler a processi in esecuzione](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Procedura: sospendere e riprendere la profilatura](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Configurare la profilatura di strumentazione per limitare i dati raccolti:** è possibile utilizzare le proprietà di configurazione della sessione di prestazioni per limitare i dati raccolti nelle esecuzioni della profilatura con il metodo di strumentazione.  È possibile includere o escludere file dll, spazi dei nomi, classi e funzioni specifici.  È inoltre possibile escludere funzioni che non soddisfano una soglia di dimensioni specificata.|-   [Procedura: Limitare la strumentazione a specifiche DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Procedura: Limitare la strumentazione a specifiche funzioni](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Procedura: Escludere o includere funzioni brevi nella strumentazione](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## Sezioni correlate  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)  
  
## Vedere anche  
 [Utilizzo degli strumenti di profilatura](../profiling/performance-explorer.md)