---
title: "Procedura: Avviare e terminare la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.wizard.summarypage"
helpviewer_keywords: 
  - "strumenti per la profilatura, avvio di sessioni"
  - "sessioni di prestazioni, avvio"
  - "sessioni di prestazioni, termine"
  - "strumenti per la profilatura, chiusura di sessioni"
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Avviare e terminare la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Prima di avviare la profilatura, è necessario aggiungere il binario di destinazione da profilare alla sessione di prestazioni.  A tale scopo, fare clic con il pulsante destro del mouse su **Destinazioni** in **Esplora prestazioni** e quindi scegliere **Aggiungi binario di destinazione**.  Nella finestra di dialogo **Aggiungi binario di destinazione** selezionare il nome file e scegliere **Apri**.  In questo modo verrà aggiunto un nuovo binario.  
  
### Per avviare la profilatura  
  
1.  Fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni nella finestra **Esplora prestazioni** e scegliere una delle opzioni seguenti:  
  
    -   **Avvio con profilatura** : avvia l'applicazione e comincia immediatamente la profilatura.  
  
    -   **Avvio con profilatura sospeso** \- avvia l'applicazione ma non comincia la profilatura.  È possibile avviare la profilatura selezionando **Riprendi raccolta** nella finestra **Controllo raccolta dati** .  Per ulteriori informazioni, vedere [Procedura: sospendere e riprendere la profilatura](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### Per terminare la profilatura  
  
-   Il metodo consigliato per terminare una sessione di profilatura consiste nella chiusura dell'applicazione.  Per terminare immediatamente la profilatura, scegliere **Interrompi** nella barra degli strumenti di **Esplora prestazioni**.  
  
## Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Procedura: sospendere e riprendere la profilatura](../profiling/how-to-pause-and-resume-performance-data-collection.md)