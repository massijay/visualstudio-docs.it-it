---
title: "Tempo di annullamento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.preemption"
helpviewer_keywords: 
  - "Visualizzatore di concorrenze, Tempo di annullamento"
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Tempo di annullamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati alla durata del blocco suddivisa in categorie come annullamento.  Questa categoria implica che un thread viene disattivato per uno dei seguenti motivi:  
  
-   L'utilità di pianificazione lo ha sostituito tramite un thread prioritario superiore.  
  
-   Il quantum di esecuzione del thread è scaduto e altri thread erano pronti per essere eseguiti.  
  
 In questo periodo un thread è stato bloccato da un motivo di attesa del kernel che il visualizzatore di concorrenze calcola come annullamento.  I segmenti di annullamento iniziano nel momento in cui un thread viene estratto da un core logico e terminano quando il thread riprende l'esecuzione.  
  
 Le informazioni relative a un segmento annullato contengono il nome del processo o del thread che ha provocato l'annullamento.  Ciò non implica tuttavia che il processo o il thread in questione siano effettivamente stati eseguiti per tutto il periodo di annullamento.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)