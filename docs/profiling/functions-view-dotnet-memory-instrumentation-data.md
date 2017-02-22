---
title: "Visualizzazione Funzioni: dati di strumentazione di memoria .NET del profiler | Microsoft Docs"
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
  - "visualizzazione Funzioni"
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Funzioni: dati di strumentazione di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Funzioni dei dati di profilo dell'allocazione di memoria .NET raccolti con il metodo di strumentazione sono elencate le funzioni che hanno allocato memoria durante l'esecuzione della profilatura.  Nella riga di una funzione sono indicate le dimensioni e il numero di allocazioni e i dati di intervallo per la funzione.  
  
## Generale  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Function Name**|Nome della funzione.|  
|**Function Address**|Indirizzo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Number of Calls**|Numero totale di chiamate effettuate a questa funzione.|  
|**File di origine**|File di origine che contiene la definizione di questa funzione.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi esclusivi.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
  
## Valori di memoria .NET  
 I valori di memoria .NET inclusivi di una funzione indicano il numero \(allocazioni\) e le dimensioni \(byte\) di oggetti creati dalla funzione e dalle relative funzioni figlio.  
  
 I valori di memoria esclusivi indicano il numero e le dimensioni di oggetti creati dalla funzione, ma non dalle relative funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Inclusive Allocations**|Numero totale di oggetti creati in questa funzione e nelle funzioni chiamate da questa funzione.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Exclusive Allocations**|Numero totale di oggetti creati durante l'esecuzione del codice nel corpo della funzione.  Non sono inclusi gli oggetti creati nelle funzioni chiamate da questa funzione.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che costituivano allocazioni esclusive di questa funzione.|  
|**Byte inclusivi**|Numero di byte di memoria allocati in questa funzione e nelle funzioni chiamate da questa funzione.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano byte inclusivi di questa funzione.|  
|**Byte esclusivi**|Numero di byte di memoria allocati da questa funzione, ma non dalle funzioni chiamate da questa funzione.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano byte esclusivi di questa funzione.|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso di questa funzione.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  È incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma non è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questa funzione.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione totale di questa funzione.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, né il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione totale di questa funzione.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Funzioni \- Campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)