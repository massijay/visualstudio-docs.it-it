---
title: Grafico di utilizzo della CPU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.cpu.graph
helpviewer_keywords: CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 852779620ec1d070da5aaabb0b5a9df8dafda359
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="cpu-utilization-graph"></a>Grafico Utilizzo CPU
Il grafico di utilizzo della CPU visualizza il livello di utilizzo in un'app nel tempo. L'asse X rappresenta la durata della traccia e l'asse Y rappresenta il numero di core logici nel sistema. Il grafico non indica quale core specifico è attivo in un momento determinato. Ad esempio, se due core sono in esecuzione al 50% per un determinato periodo di tempo, il grafico indica che viene utilizzato un solo core logico.  
  
## <a name="cpu-utilization-graph-colors"></a>Colori del grafico di utilizzo della CPU  
  
-   Il colore verde indica l'utilizzo dei core logici del sistema da parte del processo corrente.  
  
-   Il colore grigio chiaro indica l'utilizzo dei core logici da parte di altri processi nel sistema. Una percentuale elevata di colore grigio chiaro nel grafico della CPU indica che il sistema è eccessivamente caricato da altri processi e che il processo in corso potrebbe essere annullato dagli altri processi. Per ridurre l'uso dei core logici da parte di altri processi, ridurre il numero di tali processi eseguiti nel sistema.  
  
-   Il colore grigio scuro indica il consumo di core logici da parte del processo di sistema. Non è possibile controllare direttamente questa attività, ma è utile essere al corrente di questi eventi perché possono incidere sulla disponibilità di core logici per il processo.  
  
-   Il colore bianco indica la disponibilità di core logici non usati nel sistema. Tali core sono disponibili per il processo se è possibile trovare altre opportunità di parallelismo.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione Utilizzo](../profiling/utilization-view.md)   
 [Utilizzo medio della CPU](../profiling/average-cpu-utilization.md)