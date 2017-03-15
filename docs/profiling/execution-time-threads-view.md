---
title: "Tempo di esecuzione (visualizzazione Thread) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.execution"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, tempo di esecuzione (visualizzazione Thread)"
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Tempo di esecuzione (visualizzazione Thread)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale della visualizzazione Thread rappresentano il tempo di esecuzione, quando il thread è in esecuzione su un core logico nel sistema.  
  
 Le modifiche nello stato del thread vengono rilevate tramite eventi di cambio di contesto del kernel.  Event Trace for Windows \(ETW\) acquisisce esempi di stack ogni millisecondo.  In un segmento verde molto corto è possibile che non venga acquisito alcun esempio.  Pertanto, alcuni segmenti di breve esecuzione potrebbero non mostrare stack di chiamate.  
  
 Quando si fa clic su un segmento di esecuzione, il Visualizzatore di concorrenze mostra lo stack di esempio più vicino alla posizione del click.  Il percorso dello stack di esempio è indicato da una freccia nera o da un punto di inserimento al di sopra della sequenza temporale e lo stack di esempio viene visualizzato nella scheda **Corrente**.  
  
 Per visualizzare un profilo di campionamento tradizionale per tutti i segmenti di esecuzione nella visualizzazione corrente, fare clic su **Esecuzione** nel Profilo cronologia visibile.  
  
## Vedere anche  
 [Report del profilo di esecuzione](../profiling/execution-profile-report.md)   
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)