---
title: "Durata della sospensione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "Visualizzatore di concorrenze, Durata della sospensione"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Durata della sospensione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati alla durata del blocco suddivisa in categorie come sospensione.  La categoria della sospensione implica che un thread ha abbandonato volontariamente il core logico e non è in funzione.  In questo periodo un thread è stato bloccato in una API che il visualizzatore di concorrenze calcola come sospensione.  Rientrano in questo gruppo le interfacce API `Sleep()` e `SwitchToThread()`.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)