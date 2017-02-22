---
title: "Procedura: Raccogliere dati dei contatori CPU tramite il metodo di strumentazione | Microsoft Docs"
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
  - "vs.performance.property.cpucounters"
helpviewer_keywords: 
  - "strumenti per la profilatura, uso di contatori della CPU portatili"
  - "strumenti per le prestazioni, contatori della CPU portatili"
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Raccogliere dati dei contatori CPU tramite il metodo di strumentazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un contatore di eventi CPU viene utilizzato per raccogliere i dati relativi alle prestazioni dell'hardware.  In questo argomento viene illustrato come raccogliere i dati del contatore degli eventi quando si utilizza il metodo di profilatura tramite strumentazione.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Si verificano due tipi di eventi del contatore CPU:  
  
-   Eventi portabili: eventi della CPU che possono essere raccolti indipendentemente dal tipo di CPU  
  
-   Eventi piattaforma: eventi della CPU associati ad un particolare tipo di CPU  
  
 Gli eventi portabili includono eventi generali, ad esempio le istruzioni ritirate e i cicli non interrotti, eventi del buffer della CPU, eventi di creazione di un ramo ed eventi della cache L2.  I contatori degli eventi piattaforma sono determinati dal produttore del processore.  
  
 Le categorie di eventi possono essere condivise fra contatori portabili e di piattaforma.  Ad esempio, le categorie di dati riportate di seguito sono spesso comuni a entrambi i tipi:  
  
-   Eventi memoria  
  
-   Eventi front end  
  
-   Eventi creazione di un ramo  
  
 Nel profiler è possibile raccogliere i dati del contatore delle prestazioni in due modalità:  
  
-   Raccogliere i dati da uno o più contatori quando si esegue la profilatura tramite strumentazione.  
  
-   Specificare un evento di contatore come intervallo di campionamento quando si esegue la profilatura mediante campionamento.  Per ulteriori informazioni, vedere [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md).  
  
### Per raccogliere dati dei contatori delle prestazioni CPU quando si esegue la profilatura tramite strumentazione  
  
1.  In **Pagine delle proprietà** per la sessione di prestazioni fare clic su **Contatori CPU**.  
  
2.  Selezionare la casella di controllo **Raccogli contatori CPU**.  
  
3.  Espandere la struttura ad albero **Contatori di prestazioni disponibili** fino a individuare gli eventi di esempio che si desidera raccogliere.  
  
4.  Per ogni evento di cui si desidera raccogliere i dati, selezionare l'evento e fare clic sulla freccia DESTRA per aggiungere l'evento all'elenco **Contatori selezionati**.  
  
    > [!NOTE]
    >  L'opzione **Contatori di prestazioni disponibili** è abilitata solo se si seleziona la casella di controllo **Raccogli contatori CPU**.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)   
 [Contatori CPU e Windows](../profiling/cpu-and-windows-counters.md)   
 [Procedura: Scegliere eventi di campionamento](../profiling/how-to-choose-sampling-events.md)