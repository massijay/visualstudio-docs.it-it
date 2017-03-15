---
title: "Visualizzazione Funzioni: dati di strumentazione del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Funzione (visualizzazione)"
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Visualizzazione Funzioni: dati di strumentazione del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione rapporto Funzioni sono elencati i dati di profilo in base al nome della funzione.  
  
## Generale  
 Le colonne generali identificano la funzione in una riga di visualizzazione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Function Name**|Nome della funzione.|  
|**Function Address**|Indirizzo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Number of Calls**|Numero totale di chiamate effettuate a questa funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione causato dalla strumentazione.  Non è incluso il sovraccarico nelle funzioni chiamate dalla funzione.  Il sovraccarico per probe è stato sottratto da tutti i tempi esclusivi.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione.  È incluso il sovraccarico nelle funzioni chiamate dalla funzione.  Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  Sono inclusi il tempo trascorso nelle funzioni chiamate dalla funzione e il tempo trascorso in chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso di questa funzione.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo durante il quale veniva eseguito codice nel corpo della funzione, ovvero quando la funzione si trovava nella parte alta dello stack di chiamate.  È incluso il tempo trascorso in chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma non è incluso il tempo trascorso nelle funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questa funzione.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma è incluso il tempo trascorso nelle funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione totale di questa funzione.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output né il tempo trascorso nelle funzioni chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione totale di questa funzione.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)   
 [Visualizzazione Funzioni \- Campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Funzioni \- Strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)