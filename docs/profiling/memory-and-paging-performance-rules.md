---
title: "Regole di prestazioni relative a memoria e paging | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Regole di prestazioni relative a memoria e paging
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le regole di prestazioni nella categoria memoria e paging identificano l'attività di paging in un'esecuzione di profilatura che può incidere sulle prestazioni e sulla reattività dell'applicazione.  
  
|||  
|-|-|  
|[DA0014: Frequenze molto elevate di paging di memoria attiva su disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Durante la profilatura si è verificata una frequenza estremamente elevata di paging di memoria attiva da e su disco.  Le frequenze di paging a questo livello avranno solitamente un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione.  Considerare la possibilità di ridurre le allocazioni di memoria rivedendo gli algoritmi.  Potrebbe inoltre essere necessario considerare i requisiti di memoria dell'applicazione,  Provare a ripetere l'esecuzione della profilatura su un computer con una maggiore quantità di memoria.  Questa regola viene attivata quando la quantità di attività di paging supera il valore soglia superiore della regola D0017.|  
|[DA0017: Frequenze elevate di paging di memoria attiva su disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Durante la profilatura si è verificata una frequenza relativamente elevata di paging di memoria attiva da e su disco.  Le frequenze di paging a questo livello avranno solitamente un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione.  Considerare la possibilità di ridurre le allocazioni di memoria rivedendo gli algoritmi.  Potrebbe inoltre essere necessario considerare i requisiti di memoria dell'applicazione,  Provare a ripetere l'esecuzione della profilatura su un computer con una maggiore quantità di memoria.|