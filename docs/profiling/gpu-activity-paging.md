---
title: "Attivit&#224; GPU (paging) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuactivity"
  - "vs.cv.threads.timeline.gpupaging"
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Attivit&#224; GPU (paging)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I segmenti **Attività GPU \(Paging\)** nella scheda dei thread rappresentano i casi in cui la GPU stava eseguendo le richieste di paging.  La lunghezza di un segmento rappresenta la durata di tempo in cui la GPU stava eseguendo un pacchetto di paging di accesso diretto alla memoria \(DMA\).  In genere, i pacchetti di paging vengono associati al trasferimento di memoria tra la CPU e la GPU.  
  
 Quando si seleziona un segmento di paging GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato.  Ciò include il tempo di attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto di DMA e il tempo necessario per l'elaborazione del pacchetto.  
  
## Vedere anche  
 [Visualizzazione Uso](../profiling/utilization-view.md)