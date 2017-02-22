---
title: "Grafico dell&#39;attivit&#224; GPU | Microsoft Docs"
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
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Grafico dell&#39;attivit&#224; GPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il grafico di attività della GPU nel Visualizzatore di concorrenza visualizza il livello di attività di DirectX nel sistema come misurato dal numero dei motori di DirectX che sono utilizzati nel tempo.  Il grafico non mostra quali specifici motori sono stati utilizzati.  Un motore viene considerato in uso se sta elaborando qualsiasi lavoro della GPU.  
  
## Colori del grafico di attività della GPU  
 Il verde indica l'utilizzo dei motori di DirectX dal processo corrente.  
  
 Grigio chiaro indica l'utilizzo dei motori di DirectX da altri processi nel sistema.  Per ridurre l'utilizzo dei motori di DirectX da altri processi, ridurre il numero di altri processi in esecuzione nel sistema.  
  
 Il bianco indica la disponibilità dei motori inutilizzati di DirectX nel sistema.  Tali motori sono disponibili per il processo se è possibile ottenere maggiori possibilità per sfruttarli.  Alcuni motori possono essere utilizzati solo per tipi specifici di attività.  
  
## Vedere anche  
 [Visualizzazione Uso](../profiling/utilization-view.md)