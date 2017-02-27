---
title: "Strumento di spostamento di utilizzo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.performance.utilizationnavigator"
ms.assetid: 522a981a-37ef-4cdd-a04c-f1e7525a2aab
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Strumento di spostamento di utilizzo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare l'Utilization Navigator nel Visualizzatore di concorrenza per selezionare un intervallo di tempo in una traccia.  Il Visualizzatore di concorrenza illustra l'utilizzo dei core della CPU da un processo di destinazione nel tempo.  Ciò rende più semplice analizzare i modelli di utilizzo della CPU e consente inoltre il confronto tra l'utilizzo dei dati e dei dati in altre visualizzazioni.  L'Utilization Navigator viene visualizzato nella parte superiore di ogni visualizzazione nel Visualizzatore di concorrenza.  Nella figura seguente viene illustrato l'Utilization Navigator.  
  
 ![Utilization Navigator con intervallo di tempo selezionato](../profiling/media/cvutilizationnavigator.png "CVUtilizationNavigator")  
Utilization Navigator e intervallo di tempo selezionato  
  
 Nell'illustrazione, l'intervallo selezionato viene indicato da un rettangolo rosso, noto come *cursore*.  
  
 Di seguito viene illustrato come utilizzare l'Utilization Navigator per modificare l'intervallo di tempo visualizzato:  
  
-   È possibile visualizzare una panoramica di lavoro trascinando il cursore a sinistra o a destra. \(Tastiera: Spostare il puntatore sul cursore e premere il tasto freccia sinistra o freccia destra\).  
  
-   È possibile modificare l'estensione dell'intervallo trascinando uno degli handle. \(Tastiera: Spostare il puntatore su un handle e quindi premere il tasto freccia destra o freccia sinistra\).  
  
 Se si modifica l'intervallo mediante un controllo zoom differente del Visualizzatore di concorrenza, l'Utilization Navigator viene aggiornato per riflettere la modifica.