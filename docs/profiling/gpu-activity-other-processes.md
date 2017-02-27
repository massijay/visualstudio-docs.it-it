---
title: "Attivit&#224; GPU (altri processi) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Attivit&#224; GPU (altri processi)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I segmenti **Attività GPU \(altri processi\)** nella vista Threads del Visualizzatore di concorrenza, rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto di altri processi nel sistema.  Queste richieste vengono inviate alla GPU come pacchetti ad accesso diretto alla memoria \(DMA\).  La lunghezza di un segmento rappresenta la durata di tempo che il pacchetto viene elaborato dalla GPU.  
  
 Quando si seleziona questo tipo di segmento, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto che è stato elaborato.  Le informazioni includono la quantità di tempo che il pacchetto resta in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto.