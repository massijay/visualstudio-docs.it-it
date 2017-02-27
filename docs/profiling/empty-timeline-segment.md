---
title: "Segmento della cronologia vuoto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, segmento della sequenza temporale vuoto"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Segmento della cronologia vuoto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nel Visualizzatore della concorrenza, il motivo per cui una sezione della sequenza temporale è vuota \(sfondo bianco\) dipende dal tipo di canale.  
  
-   Per un canale di thread della CPU, significa che il thread non esisteva durante questa parte della sequenza temporale.  Se si vuole approfondire sui thread, è possibile trovare la sezione di esecuzione mediante il controllo zoom o mediante lo scorrimento orizzontale.  
  
-   Per un canale di I\/O, significa che nessun accesso al disco si è verificato in nome del processo di destinazione in quel momento.  
  
-   Per un canale di DirectX, significa che non è stato eseguito alcun lavoro da parte della GPU in nome del processo di destinazione durante questa parte della sequenza temporale.  
  
-   Per un canale marcatore, ciò significa che non è stato generato alcun marcatore.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)   
 [Controllo zoom \(visualizzazione Thread\)](../profiling/zoom-control-threads-view.md)