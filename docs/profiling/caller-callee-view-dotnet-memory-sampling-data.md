---
title: "Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET del profiler | Microsoft Docs"
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
  - "visualizzazione Chiamante/Chiamato"
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Chiamante/chiamato: dati di campionamento di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Chiamante\/chiamato vengono visualizzati i dati di profilo di memoria .NET per una funzione selezionata e per le relative funzioni padre e figlio.  Nella visualizzazione Chiamante\/chiamato sono presenti tre griglie.  
  
 Nella griglia centrale **Funzione corrente** contiene le informazioni di profilo di memoria per la funzione selezionata.  I valori includono tutte le chiamate campionate alla funzione.  
  
 Nella griglia superiore **Funzioni che hanno chiamato la funzione corrente** contiene il valore della funzione selezionata \(corrente\) generato dalle chiamate provenienti dalla funzione computer chiamante \(padre\).  
  
 Nella griglia inferiore **Funzioni che sono state chiamate dalla funzione corrente** contiene i dati di profilo di memoria per le funzioni computer chiamato \(figlio\) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
 Fare doppio clic su una riga di funzione computer chiamante o chiamato per rendere quella riga la funzione corrente.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Function Name**|Nome completo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo della funzione.|  
|**Type**|Contesto della funzione:<br /><br /> **0** \- funzione corrente<br /><br /> **1**: funzione che chiama la funzione corrente<br /><br /> **2**: funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Livello**|Profondità della funzione nella struttura ad albero delle chiamate.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Inclusive Allocations**|-   Per la funzione corrente, il numero di oggetti allocati dalla funzione nell'esecuzione del profilo.  Questo numero include gli oggetti creati nelle funzioni computer chiamato.<br />-   Per una funzione computer chiamante, numero delle allocazioni inclusive della funzione corrente generate da chiamate provenienti da questa funzione.<br />-   Per una funzione computer chiamato, numero di oggetti allocati dalle istanze di questa funzione che sono state chiamate dalla funzione corrente.  Il numero include le allocazioni effettuate da funzioni chiamate dalla funzione computer chiamato.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Exclusive Allocations**|-   Per la funzione corrente, il numero di oggetti creati durante l'esecuzione di codice del corpo della funzione \(ovvero quando la funzione si trovava nella parte alta dello stack di chiamate\).  Non sono inclusi gli oggetti creati in funzioni chiamate dalla funzione.<br />-   Per una funzione computer chiamante, numero delle allocazioni esclusive della funzione corrente generate da chiamate provenienti da questa funzione.<br />-   Per una funzione computer chiamato, numero di oggetti creati dalle istanze di questa funzione chiamate dalla funzione corrente.  Non sono inclusi gli oggetti creati da funzioni chiamate dalla funzione computer chiamato.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Byte inclusivi**|-   Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione del profilo.  È inclusa la memoria allocata nelle funzioni chiamate da questa funzione.<br />-   Per una funzione computer chiamante, numero dei byte inclusivi della funzione corrente generate da chiamate provenienti dalla funzione computer chiamante.<br />-   Per una funzione computer chiamato, il numero di byte allocati dalle istanze di questa funzione generate da chiamate provenienti dalla funzione corrente.  Il numero include i byte allocati da funzioni chiamate da questa funzione computer chiamato.|  
|**% byte inclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano allocazioni inclusive di questa funzione.|  
|**Byte esclusivi**|-   Per la funzione corrente, il numero di byte di memoria allocati dalla funzione nell'esecuzione del profilo.  Non è inclusa la memoria allocata dalle funzioni chiamate dalla funzione corrente.<br />-   Per una funzione computer chiamato, numero dei byte esclusivi della funzione corrente generate da chiamate provenienti dalla funzione computer chiamante.<br />-   Per una funzione computer chiamato, il numero di byte allocati dalle istanze della funzione generate da chiamate provenienti dalla funzione corrente.  Non sono inclusi i byte allocati da funzioni chiamate dalla funzione computer chiamato.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che costituivano allocazioni esclusive di questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante\/chiamato \- Strumentazione](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-instrumentation-data.md)