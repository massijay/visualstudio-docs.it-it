---
title: "Report delle operazioni su disco (visualizzazione Thread) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.diskoperations"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, report delle operazioni su file (visualizzazione Thread)"
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Report delle operazioni su disco (visualizzazione Thread)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le operazioni del disco segnalano le operazioni di I\/O del disco nei canali del disco.  
  
 Queste sono le informazioni riportate Per ogni accesso al disco che si verifica per conto del processo che sta subendo il profiling nell'intervallo di tempo attualmente visibile:  
  
-   Il nome e il PID del processo che ha eseguito l'accesso al disco  
  
-   ID del thread che ha effettuato l'accesso al disco  
  
-   Il nome del file che ha subito un l'accesso  
  
-   Numero di operazioni di lettura per ogni file  
  
-   Numero di byte letti.  
  
-   Latenza di lettura in millisecondi  
  
-   Numero di operazioni di scrittura  
  
-   Numero dei byte scritti.  
  
-   Latenza di scrittura in millisecondi  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)