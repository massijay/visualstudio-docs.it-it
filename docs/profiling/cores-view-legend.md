---
title: "Legenda della visualizzazione Core | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cores.legend"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, legenda della visualizzazione Core"
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Legenda della visualizzazione Core
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La legenda della visualizzazione Core consente di identificare ogni thread in base al colore e al nome.  Sono incluse colonne in cui sono mostrati i conteggi per cambi di contesto tra core diversi, numero totale di cambi di contesto e percentuale di cambi di contesto tra core diversi.  Le righe della legenda vengono ordinate sulla base del numero di cambi di contesto tra core diversi, in ordine decrescente.  
  
 È possibile selezionare le righe nella legenda per filtrare i thread visualizzati nella sequenza temporale.  Solo i thread selezionati vengono visualizzati nella sequenza temporale.  Se non viene selezionata alcuna riga, nella sequenza temporale vengono visualizzate tutte le righe.  
  
 I cambi di contesto tra core diversi costano maggiormente in termini di sovraccarico e prestazioni che le opzioni che rimangono nello stesso core logico.  Durante i cambi di contesto, i registri del processore vengono salvati e ripristinati, il codice kernel del sistema operativo viene eseguito, le voci del buffer lookaside di conversione ricaricate e la pipeline del processore viene scaricata.  I cambi di contesto tra core diversi possono essere ancora più costosi che altri cambi di contesto poiché i dati della cache non sono validi per il thread su un altro core.  Al contrario, se un thread subisce un cambio di contesto sul core nel quale era in esecuzione in precedenza, è probabile che i dati utili si trovino ancora nella cache.  Quando i cambi di contesto tra core diversi aumentano a causa di tentativi di gestire l'affinità di thread e le prestazioni peggiorano, si prenda in considerazione se risolvere o meno il problema.  Si inizi eliminando l'affinità di thread e osservando il comportamento risultante tra i diversi core.  
  
 Nella tabella riportata di seguito vengono descritti gli elementi della legenda.  
  
|Elemento|Definizione|  
|--------------|-----------------|  
|Nome thread|Consente di visualizzare il colore del thread nella sequenza temporale dei core precedente e il nome di tale thread.|  
|Scambi di contesto tra core diversi|Numero di scambi di contesto per un thread che è anche passato da un core logico a un altro.  Non viene fatta distinzione tra i cambi di contesto tra core diversi che passano da un die del processore ad un altro e quelli che rimangono nello stesso die.|  
|Scambi di contesto totali|Numero complessivo di scambi di contesto per un thread specificato durante il periodo di campionamento.  Ogni volta che un thread cambia contesto \(ad esempio, da esecuzione a sincronizzazione\) viene contato un cambio di contesto.|  
|Percentuale di scambi di contesto tra core diversi|Calcolati come percentuale dividendo il numero di scambi di contesto tra core diversi per il numero di scambi di contesto totali.  Più la percentuale è elevata, maggiori saranno gli effetti complessivi del sovraccarico degli scambi di contesto tra core diversi sulle prestazioni di questo thread particolare.|  
  
## Vedere anche  
 [Visualizzazione Core](../profiling/cores-view.md)