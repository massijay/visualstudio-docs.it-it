---
title: "Procedura: Connettere e disconnettere il profiler a processi in esecuzione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.attach"
helpviewer_keywords: 
  - "strumenti per le prestazioni, connessione del processo"
  - "strumenti per la profilatura, disconnessione del processo"
  - "strumenti per la profilatura, connessione del processo"
  - "strumenti per le prestazioni, disconnessione del processo"
  - "profiler"
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# Procedura: Connettere e disconnettere il profiler a processi in esecuzione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il profiler può essere utilizzato per la connessione o la disconnessione da un processo in esecuzione per facilitare la raccolta e il campionamento di dati relativi alle prestazioni.  Questo metodo può essere utilizzato nell’analisi di un processo per evitare di raccogliere dati sul tempo di caricamento dell'applicazione o per monitorare le prestazioni di un processo dopo il raggiungimento di uno stato specifico.  
  
> [!NOTE]
>  I passaggi indicati di seguito sono relativi alle operazioni di connessione e disconnessione dei processi nell'ambiente di sviluppo integrato \(IDE\) di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Per ulteriori informazioni sulle modalità di utilizzo degli strumenti della riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md).  Per informazioni su come profilare i servizi, vedere [Profilatura di servizi](../profiling/command-line-profiling-of-services.md).  
  
 I processi disponibili per l'analisi dipendono dalle autorizzazioni di accesso a livello utente impostate dall'amministratore del computer.  Un account utente può, ad esempio, disporre di autorizzazione per alcuni dei seguenti elementi:  
  
-   Funzionalità di analisi avanzate, quando l'amministratore ha impostato l’avvio del driver e del servizio.  
  
-   Solo esempi di analisi \(utenti di dominio\).  
  
-   Accesso all’accesso negato a tutti gli utenti.  
  
 Per ulteriori informazioni, vedere [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md) e per le opzioni amministratore [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### Per connettersi a un processo in esecuzione  
  
1.  Scegliere **Profiler** dal menu **Analizza**, quindi fare clic su **Connetti\/Disconnetti**.  
  
     \- oppure \-  
  
     In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Connetti\/Disconnetti**.  
  
     Verrà visualizzata la finestra di dialogo **Connettere profiler a processo**.  
  
2.  Fare clic sul nome del processo a cui si desidera effettuare la connessione.  
  
3.  Scegliere **Connetti**.  
  
### Per eseguire la disconnessione da un processo in esecuzione  
  
1.  Scegliere **Profiler** dal menu **Analizza**, quindi fare clic su **Connetti\/Disconnetti**.  
  
     \- oppure \-  
  
     In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Connetti\/Disconnetti**.  
  
     Verrà visualizzata la finestra di dialogo **Connettere profiler a processo**.  
  
2.  Fare clic sul nome dell'immagine da cui eseguire la disconnessione.  
  
3.  Scegliere **Disconnetti**.  
  
## Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Panoramica delle sessioni di prestazioni](../profiling/performance-session-overview.md)   
 [Procedura: Avviare e terminare la profilatura](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)