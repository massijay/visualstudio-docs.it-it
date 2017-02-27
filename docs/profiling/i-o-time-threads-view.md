---
title: "Tempo di I/O (visualizzazione Thread) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.io"
helpviewer_keywords: 
  - "Visualizzatore di concorrenze, Tempo di I/O (visualizzazione thread)"
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Tempo di I/O (visualizzazione Thread)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questi segmenti nella sequenza temporale sono associati a tempi di blocco suddivisi in categorie come I\/O.  Ciò significa che un thread è in attesa del completamento di un'operazione di I\/O.  È possibile che il thread sia stato bloccato in una API o da un'attesa del kernel correlata a I\/O che il visualizzatore di concorrenze calcola come I\/O.  Rientrano in questo gruppo le interfacce API `CreateFile()`, `ReadFile()` e `WSARecv()`.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)