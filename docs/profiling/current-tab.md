---
title: "Scheda Corrente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.reportnav.current"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, stack di chiamate al punto di selezione"
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Scheda Corrente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cliccando sulla scheda **Corrente**, è possibile visualizzare lo stack di chiamate \(se disponibile\) più vicino al punto di selezione corrente nella sequenza temporale se un segmento di thread della CPU è selezionato.  In questo caso, il punto di selezione è indicato da una freccia nera o un punto di inserimento, al di sopra della sequenza temporale.  Se viene selezionato un segmento di blocco, il punto di inserimento non è visualizzato poiché non si è verificata alcuna esecuzione.  Tuttavia, il segmento è ancora evidenziato e uno stack di chiamate viene visualizzato.  
  
 La scheda **Corrente** visualizza inoltre le informazioni sui segmenti di attività DirectX, i marcatori e l'accesso I\/O.  Per i segmenti di attività DirectX, vengono visualizzate le informazioni sulla modalità con cui i pacchetti DMA vengono processati dalla coda hardware.  Per i marcatori, vengono visualizzate le informazioni sulla descrizione e il tipo del marcatore.  Per l'accesso I\/O, vengono visualizzate le informazioni sul file e il numero di byte letti o scritti.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)