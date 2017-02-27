---
title: "Tempo di gestione della memoria | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, periodo di paging"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Tempo di gestione della memoria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella cronologia sono associati a tempi di blocchi suddivisi in categorie come gestione della memoria.  Ciò implica che un thread è bloccato da un evento associato a un'operazione di gestione della memoria quale il paging.  In questo periodo un thread è stato bloccato in una API o in uno stato del kernel che il visualizzatore di concorrenze calcola come gestione della memoria.  Possono essere eventi come il paging e l'allocazione di memoria.  
  
 Esaminare gli stack di chiamate e i rapporti di profilo associati per comprendere meglio i motivi alla base della categorizzazione di blocchi come Gestione memoria.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)