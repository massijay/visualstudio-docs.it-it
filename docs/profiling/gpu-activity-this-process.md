---
title: "Attività GPU (questo processo) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 255a1ff62d4f9c444169e1330dcd11eb8e1030ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-this-process"></a>Attività GPU (questo processo)
I segmenti **Attività GPU (questo processo)** nella visualizzazione Thread nel visualizzatore di concorrenza rappresentano i casi in cui la GPU stava eseguendo l'elaborazione delle richieste per conto del processo corrente. Queste richieste vengono inviate alla GPU come pacchetti di accesso diretto alla memoria (DMA). La lunghezza di un segmento rappresenta l'intervallo di tempo per cui la GPU ha elaborato un pacchetto DMA per conto del processo corrente.  
  
 Quando si seleziona il segmento di attività GPU, il rapporto nella scheda **Corrente** visualizza le informazioni sul pacchetto DMA che è stato elaborato. Queste informazioni includono la quantità di tempo per cui il pacchetto è rimasto in attesa nella coda hardware associata al motore di DirectX, il processo che ha inviato il pacchetto e il tempo richiesto per elaborare il pacchetto. Un processo diverso dal processo corrente può avere inviato fisicamente il pacchetto DMA alla GPU. Il visualizzatore di concorrenza è in grado di rilevare quando un altro processo ha inviato operazioni alla GPU per conto del processo corrente.