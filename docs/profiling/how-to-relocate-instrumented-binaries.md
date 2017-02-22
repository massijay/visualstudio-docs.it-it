---
title: "Procedura: Rilocare file binari instrumentati | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "file binari, instrumentati"
  - "strumentazione, file binari instrumentati"
  - "binari instrumentati e rilocazione"
  - "strumenti per la profilatura, file binari instrumentati"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Rilocare file binari instrumentati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durante la strumentazione, i probe vengono inseriti nel file binario per misurare le prestazioni dell'applicazione. Se si sceglie di rilocare il file binario instrumentato, una copia del file binario originale viene instrumentata e inserita nella posizione specificata. Questa opzione è utile se non si vuole che il profiler rinomini il file binario originale. Se il file binario non viene rilocato, la versione originale di tale file verrà sovrascritta.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Per rilocare il file binario instrumentato  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni, quindi fare clic su **Proprietà**.  
  
2.  Nella **Pagine delle proprietà** fare clic sulle proprietà di **Binario**.  
  
3.  Selezionare la casella di controllo **Rilocare binari instrumentati**.  
  
4.  Specificare la posizione per il file binario instrumentato.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)