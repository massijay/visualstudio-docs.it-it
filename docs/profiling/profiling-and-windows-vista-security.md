---
title: "Profilatura e sicurezza in Windows Vista | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, sicurezza"
  - "strumenti per le prestazioni, sicurezza"
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Profilatura e sicurezza in Windows Vista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A seconda delle impostazioni delle autorizzazioni di accesso utente di [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] rese disponibili dall'amministratore di un computer, un singolo utente può o meno disporre dell'autorizzazione di sicurezza necessaria per profilare un processo nel computer.  Nei seguenti esempi vengono illustrate le possibili differenze fra utenti:  
  
-   Se l'amministratore ha impostato l’avvio del driver e del servizio, alcuni utenti possono accedere a funzionalità di profilatura avanzate.  
  
-   Gli utenti di dominio possono accedere soltanto ad esempi di analisi.  
  
-   Alcuni utenti possono negare l’accesso alla profilatura a tutti gli altri utenti.  
  
 Per ulteriori informazioni sulle opzioni ADMIN, vedere [VSPerfCmd](../profiling/vsperfcmd.md).  
  
## Profilatura tra sessioni  
 La *profilatura tra sessioni* consente di profilare un processo che viene eseguito in una differente sessione di accesso.  Ad esempio, la maggior parte dei servizi vengono eseguiti nella sessione 0 e gli utenti non possono effettuare esecuzioni direttamente nella sessione 0.  Utilizzando il pulsante **Connetti a processo** nella barra degli strumenti di Esplora prestazioni o l'opzione \/attach dello strumento della riga di comando VSPerfCmd, è possibile profilare la maggior parte dei processi nelle diverse sessioni di accesso.  
  
 È possibile vedere un elenco dei processi disponibili impostando le opzioni di visibilità relative alla profilatura tra processi incrociati.  Queste opzioni sono disponibili nella finestra **Connetti a processo** visualizzata quando si fa clic su **Connetti a processo**:  
  
-   **Mostra i processi di tutti gli utenti**  
  
     Se questa opzione non è selezionata, vengono visualizzati solo i processi di proprietà dell'utente corrente.  Quando si seleziona **Mostra i processi di tutti gli utenti**, nell'elenco vengono riportati i processi di tutti gli utenti.  
  
-   **Mostra processi in tutte le sessioni**  
  
     Se questa opzione non è selezionata, nell'elenco vengono visualizzati i processi della sessione corrente.  Se l'opzione è selezionata, vengono visualizzati tutti i processi di tutte le sessioni.  
  
## Vedere anche  
 [Cenni preliminari](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [How to: Attach to a Running Process](http://msdn.microsoft.com/it-it/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)