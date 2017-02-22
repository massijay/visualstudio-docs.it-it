---
title: "Visualizzazione Processo: dati su conflitti del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processo (visualizzazione)"
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Processo: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Processo vengono visualizzati i dati di conflitto per i processi e i thread eseguiti durante l'esecuzione del profilo.  
  
 Quando sono disponibili i simboli, i processi vengono elencati in base al nome.  Quando non sono disponibili simboli, i processi vengono elencati in base all'indirizzo di memoria in formato esadecimale.  I thread vengono elencati come figli del processo che li creati.  
  
 Nella tabella seguente vengono descritti i valori delle colonne nella tabella della visualizzazione Processo.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|  
|**Tempo blocco**|Tempo totale durante il quale è stata impedita l'esecuzione di funzioni del processo o del thread.|  
|**% tempo blocco**|Percentuale della durata del processo o del thread in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|  
|**Conflitti**|Numero di volte in cui è stata impedita l'esecuzione delle funzioni del processo o del thread.|  
|**% conflitti**|Percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano conflitti del processo o del thread.|  
|**Ora di fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|  
|**ID**|Identificatore generato dal sistema per il processo o il thread.|  
|**Durata**|Numero di millisecondi o di cicli del processore dall'inizio del processo o del thread alla fine del processo o del thread o alla fine del profilo.|  
|**Type**|Tipo di riga, ovvero processo o thread.<br /><br /> Solo nei rapporti della riga di comando di **VSReport**.  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome**|Nome del processo o del thread.|  
|**Unique ID**|Identificatore generato dal profiler univoco per il processo o il thread.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Processo](../profiling/process-view.md)