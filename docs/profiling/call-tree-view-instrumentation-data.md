---
title: "Visualizzazione struttura ad albero delle chiamate: dati di strumentazione del profiler | Microsoft Docs"
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
  - "visualizzazione Struttura ad albero delle chiamate"
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione struttura ad albero delle chiamate: dati di strumentazione del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I valori per una funzione nella struttura ad albero delle chiamate indicano il periodo di tempo in cui le istanze della funzione sono state chiamate dalla funzione padre nella struttura ad albero delle chiamate.  I valori percentuale vengono calcolati confrontando il valore delle istanze della funzione rispetto al tempo inclusivo trascorso totale di tutte le funzioni nell'esecuzione del profilo.  
  
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
|**Nome di processo**|Il nome assegnato al processo.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi esclusivi.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Livello**|Profondità della funzione nella struttura ad albero delle chiamate.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo nello stack di chiamate di queste istanze della funzione che sono state chiamate dalla funzione padre nella struttura ad albero delle chiamate.  È incluso il tempo trascorso nelle funzioni figlio chiamate dalla funzione e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|Tempo inclusivo trascorso totale di tutte le chiamate a questa funzione in questo contesto.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo in cui le istanze di una funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate hanno eseguito il codice nel corpo della funzione, ovvero quando la funzione si trovava nella parte alta dello stack di chiamate.  È incluso il tempo delle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  Tuttavia, non è incluso il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|Tempo esclusivo trascorso totale di tutte le chiamate a questa funzione in questo contesto.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo in cui le istanze di una funzione che sono state chiamate dalla funzione padre nella struttura ad albero delle chiamate si trovavano nello stack di chiamate.  Non include il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma include il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|Tempo inclusivo applicazione totale di tutte le chiamate a questa funzione in questo contesto.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo in cui le istanze di una funzione chiamate dalla funzione padre nella struttura ad albero delle chiamate hanno eseguito direttamente il codice nel corpo della funzione, ovvero quando la funzione si trovava nella parte alta dello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  Inoltre, non è incluso il tempo trascorso nelle funzioni figlio chiamate dalla funzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|Tempo esclusivo applicazione totale di tutte le chiamate a questa funzione in questo contesto.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione albero delle chiamate](../profiling/call-tree-view-sampling-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate \- Strumentazione](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Struttura ad albero delle chiamate \- Campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)