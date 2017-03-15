---
title: "Visualizzazione Core | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, visualizzazione Core"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Visualizzazione Core
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La Cores View mostra come l'esecuzione del thread è stata mappata ai core logici del processore.  Se si sviluppano applicazioni server, questa visualizzazione agevola l'ottimizzazione delle prestazioni di cache mediante l'affinità di thread o la gestione di pool di thread.  Può inoltre consentire di visualizzare casi in cui l'affinità di thread può aver in realtà peggiorato il problema della migrazione tra core.  La Cores View dispone di due parti, un grafico e una legenda.  
  
 Il grafico superiore illustra i core logici sull'asse Y e il tempo sull'asse X.  Ogni thread nel grafico dispone di un colore univoco in modo da tenere traccia dello spostamento tra componenti principali nel tempo.  È possibile filtrare i thread in questo grafico nell'area della legenda.  
  
 L'area della legenda presenta una voce per ogni colore del grafico.  Sono riportati colore e nome del thread, numero di cambi di contesto tra core, numero totale di cambi di contesto e percentuale di cambi di contesto tra core diversi  La legenda viene ordinata in base al numero di cambi di contesto tra core, in ordine decrescente.  Vengono elencati solo i thread che hanno eseguito durante l'intervallo di tempo visualizzato.  L'elenco viene aggiornato si ingrandisce o si fa una panoramica.  
  
## Vedere anche  
 [Visualizzatore di concorrenze](../profiling/concurrency-visualizer.md)   
 [Visualizzazione Uso](../profiling/utilization-view.md)   
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)