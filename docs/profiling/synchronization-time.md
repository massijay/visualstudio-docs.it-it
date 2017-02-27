---
title: "Tempo di sincronizzazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "Visualizzatore di concorrenze, Tempo di sincronizzazione"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Tempo di sincronizzazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella cronologia sono associati a durate di blocchi suddivise in categorie come sincronizzazione.  Quando un thread è contrassegnato come bloccato su sincronizzazione, ne consegue una delle condizioni seguenti:  
  
-   L'esecuzione del thread potrebbe aver prodotto una chiamata a un'API di sincronizzazione dei thread nota, ad esempio `EnterCriticalSection()` o `WaitForSingleObject()`.  
  
-   L'algoritmo di corrispondenza delle API non può essere totalmente completo e pertanto alcune API che potrebbero essere mappate ad altre categorie possono risultare ugualmente in sincronizzazione poiché il frame nello stack di chiamate ha raggiunto un primitive di blocco del kernel sottostante mappato a questa categoria.  
  
 Per comprendere l'effettiva causa di un evento di blocco del thread, esaminare con attenzione i rapporti di profilatura e gli stack di chiamate di blocco.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)