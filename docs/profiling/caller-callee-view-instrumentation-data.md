---
title: "Visualizzazione Chiamante/chiamato: dati di strumentazione del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione Chiamante/Chiamato"
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Visualizzazione Chiamante/chiamato: dati di strumentazione del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Chiamante\/chiamato vengono visualizzate informazioni di profilo relative a una funzione selezionata e alle funzioni padre e figlio ad essa associate nella struttura ad albero delle chiamate.  Nella visualizzazione Chiamante\/chiamato sono presenti tre griglie.  
  
 Nella griglia centrale, **Funzione corrente** contiene le informazioni di profilo sulla funzione selezionata.  Sono incluse tutte le chiamate alla funzione.  
  
 Nella griglia superiore, **Funzioni che hanno chiamato la funzione corrente** contiene le informazioni di profilo sulle funzioni computer chiamato \(padre\) della funzione selezionata.  I valori indicano la quantità del valore della funzione corrente generata da chiamate provenienti da questa funzione computer chiamante.  
  
 Nella griglia inferiore, **Funzioni che sono state chiamate dalla funzione corrente** contiene le informazioni di profilo sulle istanze delle funzioni computer chiamato \(figlio\) della funzione selezionata.  Il valore indica unicamente il tempo trascorso nella funzione figlio quando è stata chiamata dalla funzione corrente.  
  
## Generale  
 Le colonne generali identificano la funzione in una riga di visualizzazione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Function Name**|Nome della funzione.|  
|**Function Address**|Indirizzo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Number of Calls**|Numero totale di chiamate a questa funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi esclusivi.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione e per le relative funzioni figlio causato dalla strumentazione.  Il sovraccarico per probe è stato sottratto da tutti i tempi inclusivi.|  
|**Type**|Contesto della funzione:<br /><br /> **0** \- funzione corrente<br /><br /> **1**: funzione che chiama la funzione corrente<br /><br /> **2**: funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome funzione radice**|Nome della funzione corrente.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  Sono inclusi il tempo trascorso nelle funzioni figlio e il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|-   Per la funzione corrente, il tempo trascorso nella funzione.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità del tempo inclusivo trascorso della funzione corrente generata da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il tempo trascorso nelle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  È incluso il tempo trascorso nelle funzioni figlio del computer chiamato e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso di questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  È incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma non è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|-   Per la funzione corrente, il tempo trascorso nell'esecuzione diretta della funzione.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità di tempo esclusivo trascorso della funzione corrente generata da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il tempo trascorso nelle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  È escluso il tempo trascorso nelle funzioni figlio della funzione computer chiamato, ma sono incluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|-   Per la funzione corrente, il tempo trascorso nella funzione e nelle relative funzioni figlio.  È escluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità del tempo inclusivo applicazione della funzione corrente generata da chiamate provenienti da questa funzione computer chiamato.<br />-   Per una funzione computer chiamato, il tempo trascorso nelle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  È incluso il tempo trascorso nelle funzioni figlio della funzione computer chiamato, ma non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo trascorso nella funzione.  È escluso il tempo trascorso nelle funzioni figlio e le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|-   Per la funzione corrente, il tempo trascorso nell'esecuzione diretta della funzione.  Non sono inclusi il tempo trascorso nelle funzioni figlio e le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità del tempo esclusivo applicazione della funzione corrente generata da chiamate provenienti da questa funzione computer chiamato.<br />-   Per una funzione computer chiamato, il tempo trascorso nelle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  Non sono inclusi il tempo trascorso nelle funzioni figlio della funzione computer chiamato e le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Campionamento](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Strumentazione](../profiling/caller-callee-view-net-memory-instrumentation-data.md)