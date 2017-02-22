---
title: "Grafico Utilizzo CPU | Microsoft Docs"
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
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, grafico Utilizzo CPU"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Grafico Utilizzo CPU
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il grafico di utilizzo della CPU mostra il livello di utilizzo della CPU in un'applicazione nel tempo.  Sull'asse X viene rappresentata la durata della traccia e sull'asse y il numero di core logici nel sistema.  Nel grafico non viene tuttavia indicato quale core specifico è attivo in un determinato momento.  Ad esempio, se due core sono ciascuno in esecuzione al 50 percento della capacità per un periodo di tempo specificato, in questa visualizzazione verrà indicato l'utilizzo di un solo core logico.  
  
## Colori del Grafico di Utilizzo della CPU  
  
-   Il verde indica l'utilizzo dei core logici nel sistema dal processo corrente.  
  
-   Il grigio chiaro indica l'utilizzo dei core logici da parte di altri processi nel sistema.  Una percentuale elevata di grigio chiaro nel grafico della CPU segnala un carico massimo sul sistema a causa di altri processi, per cui il processo dell'utente potrebbe essere annullato.  Per ridurre l'utilizzo di core logici da parte degli altri processi, limitare il numero dei processi stessi in esecuzione sul sistema.  
  
-   In grigio scuro viene indicato l'utilizzo dei core logici da parte del processo di sistema.  Sebbene non sia possibile controllarlo, è utile sapere quando viene eseguito perché può influire sulla disponibilità di core logici per il processo dell'utente.  
  
-   In bianco viene indicata la disponibilità di core logici inutilizzati nel sistema.  Tali core sono disponibili per il processo se è possibile trovare più opportunità di parallelismo.  
  
## Vedere anche  
 [Visualizzazione Uso](../profiling/utilization-view.md)   
 [Utilizzo CPU medio](../profiling/average-cpu-utilization.md)