---
title: "Marcatori di span | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.markers.span"
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Marcatori di span
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un marcatore span rappresenta una parte significativa di un'applicazione.  Ad esempio, è possibile utilizzare uno span per rappresentare un periodo di tempo durante il quale un particolare elemento di lavoro viene elaborato.  La sua lunghezza rappresenta la durata della fase dell'applicazione corrispondente.  In questa illustrazione viene mostrato uno span nel Visualizzatore di concorrenze:  
  
 ![Marcatore espansione in Visualizzatore di concorrenza](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Marcatore span nel Visualizzatore di concorrenza  
  
## Categoria dello span  
 Un marcatore span viene mostrato in uno dei cinque colori diversi, a seconda della categoria.  I colori sono ripetuti se sono presenti più di cinque categorie.  La categoria può essere qualsiasi intero.  La figura mostra i cinque colori possibili:  
  
 ![Cinque espansioni in categorie diverse](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
I colori delle prime cinque categorie span  
  
## Marcatori di aggregazione span  
 Talvolta i marcatori span si verificano in modo cosi ravvicinato nel Visualizzatore della concorrenza che non possono essere disegnati singolarmente.  In questo caso, viene visualizzato un *marcatore di aggregazione span* grigio che rappresenta gli span sottostanti.  Quando si posiziona il puntatore su una di queste icone, un tooltip mostrerà il numero di span sottostanti che sono rappresentati.  Per visualizzare gli span, ingrandire.  Se facendo lo zoom viene visualizzato ancora un marcatore di aggregazione di span, è possibile visualizzare i marcatori di span sottostanti nel [Rapporto marcatori](../profiling/markers-report.md).  In questa illustrazione viene mostrato un marcatore di aggregazione span:  
  
 ![Marcatore espansione aggregato in Visualizzatore di concorrenza](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Un marcatore di aggregazione span  
  
## Vedere anche  
 [Marcatori del visualizzatore di concorrenza](../profiling/concurrency-visualizer-markers.md)   
 [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md)