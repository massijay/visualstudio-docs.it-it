---
title: "Uso degli strumenti per la profilatura dalla riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "riga di comando, strumenti per le prestazioni"
  - "strumenti da riga di comando, strumenti per le prestazioni"
  - "strumenti per la profilatura, riga di comando"
  - "strumenti, riga di comando"
  - "riga di comando, strumenti"
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Uso degli strumenti per la profilatura dalla riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare gli strumenti da riga di comando disponibili negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per profilare applicazioni al prompt dei comandi e automatizzare la profilatura tramite file batch e script.  È inoltre possibile generare file di rapporti a un prompt dei comandi.  È possibile utilizzare il profiler autonomo leggero per raccogliere dati in computer su cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Impostare il percorso di simboli:** per visualizzare i nomi di funzioni e parametri, il profiler deve disporre dell'accesso ai file di simboli \(.pdb\) dei binari profilati.  Questi file devono includere i file di simboli per il sistema operativo e le applicazioni Microsoft che si desidera visualizzare nell'analisi.  È possibile utilizzare il server di simboli di Microsoft pubblico per accertarsi di disporre dei file .pdb corretti per i binari Microsoft.|-   [Procedura: specificare percorsi dei file di simboli tramite la riga di comando](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profilare l'applicazione:** gli strumenti e le opzioni da riga di comando utilizzati per profilare un'applicazione di destinazione dipendono dal tipo di applicazione, dal metodo di profilatura e dal tipo di destinazione \(applicazione gestita o nativa\).|-   [Utilizzo di metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)|  
|**Creare rapporti .xml e .csv:** la profilatura al prompt dei comandi crea file di dati che possono essere visualizzati nell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  È inoltre possibile generare file con estensione xml o con valori delimitati da virgole \(con estensione csv\) dei dati mediante lo strumento da riga di comando VSPerfReport.|-   [Creazione di rapporti del profiler tramite la riga di comando](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilare codice nei computer senza Visual Studio:** è possibile utilizzare il profiler autonomo degli strumenti di profilatura per raccogliere dati per le applicazioni su computer in cui non è installato [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|-   [Procedura: installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## Riferimento  
 [Riferimenti agli strumenti di profilatura della riga di comando](../profiling/command-line-profiling-tools-reference.md)  
  
## Vedere anche  
 [Utilizzo degli strumenti di profilatura](../profiling/performance-explorer.md)