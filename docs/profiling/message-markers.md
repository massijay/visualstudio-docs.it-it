---
title: "Marcatori di messaggi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.message"
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Marcatori di messaggi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un marcatore del messaggio rappresenta l'output del log.  Un messaggio è una stringa che viene pubblicata da una thread specifica in un momento specifico.  È possibile esportare i messaggi in un file di testo da utilizzare con altri strumenti.  È possibile portare il puntatore su un messaggio nel Visualizzatore della concorrenza per visualizzare la stringa del messaggio.  Ed è possibile visualizzare tutti i marcatori di messaggio nel [Rapporto marcatori](../profiling/markers-report.md).  Nella figura seguente viene illustrato un marcatore del messaggio.  
  
## Marcatori di aggregazione di messaggi  
 A volte più messaggi capitano così vicini nel Visualizzatore della concorrenza che non possono essere disegnati singolarmente.  In questo caso, viene visualizzato *un marcatore di aggregazione di messaggi* che rappresenta i messaggi sottostanti.  Quando si posiziona il puntatore su una di queste icone, una tooltip mostrerà il numero di messaggi sottostanti rappresentati.  Per visualizzare i messaggi, fare zoom avanti. Se viene fatto zoom avanti completamente e viene visualizzato ancora un marcatore di aggregazione, è possibile visualizzare i messaggi sottostanti in [Rapporto marcatori](../profiling/markers-report.md).  
  
## Vedere anche  
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)   
 [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)