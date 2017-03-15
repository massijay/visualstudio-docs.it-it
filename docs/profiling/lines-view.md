---
title: "Visualizzazione Righe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.lines"
helpviewer_keywords: 
  - "Righe (visualizzazione)"
  - "rapporti degli strumenti di profilatura, visualizzazione Riga"
  - "strumenti di profilatura, visualizzazione Riga"
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Visualizzazione Righe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Righe è disponibile solo per i dati del profiler raccolti mediante il metodo di campionamento.  La visualizzazione non è disponibile per i dati raccolti utilizzando la strumentazione.  
  
 Per i dati del profilo di campionatura, la visualizzazione Righe identifica l'istruzione in una funzione in esecuzione diretta durante la raccolta del campione.  Per i dati di memoria .NET, la visualizzazione Righe identifica le istruzioni per l'allocazione di memoria.  
  
 Un'istruzione può occupare più righe in un file di origine e una singola riga può includere più istruzioni.  
  
 Un'istruzione viene identificata da quanto segue:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di codice sorgente in cui inizia l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale inizia l'istruzione.  
  
-   Riga di codice sorgente in cui termina l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale termina l'istruzione.  
  
## Vedere anche  
 [Visualizzazione Righe](../profiling/lines-view-sampling-data.md)   
 [Visualizzazione Righe \- Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Righe](../profiling/lines-view-contention-data.md)