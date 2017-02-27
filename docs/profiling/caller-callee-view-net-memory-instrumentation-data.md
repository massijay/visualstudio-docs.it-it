---
title: "Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET del profiler | Microsoft Docs"
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
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Visualizzazione Chiamante/chiamato: dati di strumentazione di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Chiamante\/chiamato dei dati di profilo di memoria .NET raccolti con il metodo di strumentazione contiene dati di allocazione e intervallo per una funzione selezionata e per le funzioni padre e figlio della funzione selezionata.  Nella visualizzazione Chiamante\/chiamato sono presenti tre griglie.  
  
 Nella griglia centrale **Funzione corrente** contiene le informazioni di profilo di memoria per la funzione selezionata.  I valori includono tutte le chiamate campionate alla funzione.  
  
 Nella griglia superiore **Funzioni che hanno chiamato la funzione corrente** contiene il valore della funzione selezionata \(corrente\) generato dalle chiamate provenienti dalla funzione computer chiamante \(padre\).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** contiene i dati di profilo di memoria per le funzioni computer chiamato \(figlio\) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
 Fare doppio clic su una riga di funzione computer chiamante o chiamato per rendere quella riga la funzione corrente.  
  
## Generale  
  
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
|**Type**|Contesto della funzione:<br /><br /> **0** \- funzione corrente<br /><br /> **1**: funzione che chiama la funzione corrente<br /><br /> **2**: funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Nome funzione radice**|Nome della funzione corrente.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
  
## Valori di allocazione memoria .NET  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Exclusive Allocations**|-   Per la funzione corrente, il numero di oggetti creati durante l'esecuzione di codice nel corpo della funzione \(ovvero quando la funzione si trovava nella parte alta dello stack di chiamate\).  Non sono inclusi gli oggetti creati in funzioni chiamate da questa funzione.<br />-   Per una funzione computer chiamante, il numero delle allocazioni esclusive della funzione corrente generate da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, numero di oggetti creati dalle istanze di questa funzione chiamate dalla funzione corrente.  Non sono inclusi gli oggetti creati da funzioni chiamate dalla funzione computer chiamato.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che costituivano allocazioni esclusive di questa funzione.|  
|**Inclusive Allocations**|-   Per la funzione corrente, il numero di oggetti allocati dalla funzione nell'esecuzione del profilo.  Il numero include gli oggetti creati nelle funzioni computer chiamato chiamati dalla funzione.<br />-   Per una funzione computer chiamante, il numero delle allocazioni inclusive della funzione corrente generate da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il numero di oggetti allocati dalle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  Il numero include le allocazioni effettuate da funzioni chiamate da questa funzione computer chiamato.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Byte esclusivi**|-   Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione del profilo.  Non è inclusa la memoria allocata nelle funzioni computer chiamato chiamate dalla funzione.<br />-   Per una funzione computer chiamante, il numero di byte esclusivi della funzione corrente generati da chiamate effettuate da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il numero di byte allocati dalle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  Non sono inclusi i byte allocati da funzioni chiamate dalla funzione computer chiamato.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano allocazioni esclusive di questa funzione.|  
|**Byte inclusivi**|-   Per la funzione corrente, il numero di byte in memoria allocati dalla funzione nell'esecuzione del profilo.  Il numero include la memoria allocata nelle funzioni computer chiamato chiamate dalla funzione.<br />-   Per una funzione computer chiamante, il numero dei byte inclusivi delle istanze della funzione corrente generate da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il numero di byte allocati dalle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  Il numero include i byte allocati da funzioni chiamate da questa funzione computer chiamato.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|-   Per la funzione corrente, il tempo trascorso nella funzione.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità del tempo inclusivo trascorso della funzione corrente generata da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il tempo trascorso in questa funzione generata da chiamate provenienti dalla funzione corrente.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso di questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso medio**|Tempo inclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso massimo**|Tempo inclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo trascorso minimo**|Tempo inclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  È incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma non è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|-   Per la funzione corrente, il tempo trascorso nell'esecuzione del corpo della funzione.  È escluso il tempo trascorso nelle funzioni figlio, ma sono incluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità di tempo esclusivo trascorso della funzione corrente generata da chiamate provenienti da questa funzione computer chiamante.<br />-   Per una funzione computer chiamato, il tempo trascorso in questa funzione generata da chiamate provenienti dalla funzione corrente.  È escluso il tempo trascorso nelle funzioni figlio della funzione computer chiamato, ma sono incluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso medio**|Tempo esclusivo trascorso medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso massimo**|Tempo esclusivo trascorso massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo trascorso minimo**|Tempo esclusivo trascorso minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|-   Per la funzione corrente, il tempo trascorso nella funzione e nelle relative funzioni figlio.  È escluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità del tempo inclusivo applicazione della funzione corrente generata da chiamate provenienti da questa funzione computer chiamato.<br />-   Per una funzione computer chiamato, il tempo trascorso in questa funzione e nelle relative funzioni figlio generate da chiamate provenienti dalla funzione corrente.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione medio**|Tempo inclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione massimo**|Tempo inclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo inclusivo applicazione minimo**|Tempo inclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo trascorso nella funzione, escluso il tempo trascorso nelle funzioni figlio.  Inoltre, non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|-   Per la funzione corrente, il tempo trascorso nell'esecuzione del corpo della funzione.  Non sono inclusi il tempo trascorso nelle funzioni figlio e le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per una funzione computer chiamante, la quantità del tempo esclusivo applicazione della funzione corrente generata da chiamate provenienti da questa funzione computer chiamato.<br />-   Per una funzione computer chiamato, il tempo trascorso in questa funzione generata da chiamate provenienti dalla funzione corrente.  Non sono inclusi il tempo trascorso nelle funzioni figlio della funzione computer chiamato e le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione totale di questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione medio**|Tempo esclusivo applicazione medio di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione massimo**|Tempo esclusivo applicazione massimo di una chiamata a questa funzione in questo contesto.|  
|**Tempo esclusivo applicazione minimo**|Tempo esclusivo applicazione minimo di una chiamata a questa funzione in questo contesto.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante\/chiamato \- Campionamento](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-instrumentation-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-sampling-data.md)