---
title: "Attivit&#224; GPU (questo processo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Attivit&#224; GPU (questo processo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I segmenti di **Attività GPU \(questo processo\)** nella visualizzazione Thread nel Visualizzatore di concorrenze rappresentano i casi in cui la GPU stava eseguendo le richieste da parte del processo corrente.  Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria \(DMA\).  La lunghezza di un segmento rappresenta il tempo in cui la GPU stava eseguendo un pacchetto DMA per conto del processo corrente.  
  
 Quando si seleziona il segmento di attività di GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato.  Le informazioni includono la quantità di tempo che il pacchetto resta in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto.  Un processo diverso dal processo corrente può inviare fisicamente il pacchetto di DMA alla GPU.  Il Visualizzatore della concorrenza può rilevare quando un altro processo invia lavoro alla GPU per conto del processo corrente.