---
title: "Configurazione di sessioni di prestazioni per gli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attività comuni, prestazioni"
  - "attività comuni, strumenti per la profilatura"
  - "strumenti per la profilatura, attività comuni"
  - "prestazioni, raccolta dei dati"
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 36
---
# Configurazione di sessioni di prestazioni per gli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è possibile raccogliere un'ampia gamma di dati di prestazioni per numerosi tipi di applicazioni.  In questa sezione viene illustrato come utilizzare la Creazione guidata sessione di prestazionie le proprietà della sessione e del binario di destinazione allo scopo di configurare gli strumenti di profiling per raccogliere dati di interesse.  Le proprietà di configurazione degli strumenti di profilatura possono essere utilizzate anche per controllare la quantità di dati raccolti in un'esecuzione della profilatura.  Per ulteriori informazioni, vedere [Controllo della raccolta di dati](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  In molti casi, l'utilizzo delle proprietà predefinite della Creazione guidata sessione di prestazioni rappresenta un modo efficiente di raccogliere dati di profilatura.  Per ulteriori informazioni, vedere [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md) e [Introduzione](../profiling/getting-started-with-performance-tools.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Impostare le opzioni di profilatura di base:** è necessario configurare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] per utilizzare il server di simboli Microsoft.  In questo modo è possibile accertarsi di avere accesso a simboli quali nomi di funzioni e parametri per la versione corrente di Windows e di altre applicazioni Microsoft.  È inoltre possibile specificare altre opzioni generali prima di avviare una sessione di profilatura, ad esempio autorizzazioni di sistema per gli strumenti di profilatura e nomi dei file dei dati di profilatura.|-   [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Procedura: Serializzare le informazioni sui simboli](../profiling/how-to-serialize-symbol-information.md)<br />-   [Procedura: Impostare la sessione di profilatura corrente](../profiling/how-to-set-the-current-session.md)<br />-   [Procedura: Impostare le autorizzazioni per la profilatura](../profiling/how-to-set-permissions.md)<br />-   [Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Specificare i dati che si desidera raccogliere:** le procedure utilizzate per configurare una sessione di profilatura dipendono dal tipo di applicazione di destinazione da profilare e dal tipo di dati sulle prestazioni che si desidera raccogliere.|-   [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)<br />-   [Raccolta di statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Procedura: Profilare codice JavaScript \(ECMA\) nelle pagine Web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Raccolta di dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Raccolta di dati aggiuntivi relativi alle prestazioni](../profiling/collecting-additional-performance-data.md)|  
|**Impostare opzioni di configurazione avanzate:** quando si profilano applicazioni per .NET Framework che caricano più versioni di CLR, è possibile specificare quali controllano la versione da profilare.  Quando si dispone di più file con estensione exe in una sessione di prestazioni, è possibile impostare l'ordine iniziale dei binari.|-   [Procedura: Specificare il runtime di .NET Framework da profilare negli scenari di esecuzione side\-by\-side](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Procedura: Specificare l'inizio del file binario](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## Sezioni correlate  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)  
  
## Vedere anche  
 [Utilizzo degli strumenti di profilatura](../profiling/performance-explorer.md)