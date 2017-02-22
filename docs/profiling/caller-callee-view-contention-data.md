---
title: "Visualizzazione Chiamante/chiamato: dati su conflitti del profiler | Microsoft Docs"
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
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Chiamante/chiamato: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Chiamante\/chiamato consente di visualizzare informazioni relative ai conflitti per una funzione selezionata e per le relative funzioni figlio.  Nella visualizzazione Chiamante\/chiamato sono presenti tre griglie.  
  
 **Funzione corrente** viene visualizzato nella griglia al centro e include le informazioni sui conflitti per la funzione selezionata.  I valori includono tutti i conflitti del blocco per la funzione.  
  
 **Funzioni che hanno chiamato la funzione corrente** viene visualizzato nella griglia superiore e include i singoli contributi delle funzioni computer chiamante \(padre\) ai valori della funzione selezionata \(corrente\).  
  
 **Funzioni che sono state chiamate dalla funzione corrente** viene visualizzato nella griglia inferiore e include le informazioni sui conflitti per le funzioni chiamate \(figlio\) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Type**|Contesto della funzione:<br /><br /> -   **0** \- funzione corrente<br />-   **1**: funzione che chiama la funzione corrente<br />-   **2**: funzione chiamata dalla funzione corrente<br /><br /> Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Tempo blocco esclusivo**|-   Per la funzione corrente, tempo durante il quale è stata impedita l'esecuzione del codice nel corpo della funzione.  Non è incluso il tempo blocco nelle funzioni chiamate dalla funzione.<br />-   Per una funzione computer chiamante, quantità di tempo di blocco esclusivo della funzione corrente trascorsa quando questa funzione ha chiamato la funzione corrente.<br />-   Per una funzione computer chiamato, tempo durante il quale è stata impedita l'esecuzione del codice da parte di questa funzione quando la funzione è stata chiamata dalla funzione corrente.  Non è incluso il tempo blocco nelle funzioni figlio chiamate dalla funzione computer chiamato.|  
|**% tempo blocco esclusivo**|Percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco esclusivo per questa funzione in questo contesto.|  
|**Conflitti esclusivi**|-   Per la funzione corrente, numero di volte in cui è stata impedita l'esecuzione del codice nel corpo della funzione.  Non sono inclusi i conflitti che si sono verificati nelle funzioni chiamate dalla funzione.<br />-   Per una funzione computer chiamante, numero di conflitti esclusivi della funzione corrente verificatisi quando questa funzione ha chiamato la funzione corrente.<br />-   Per una funzione computer chiamato, numero di volte in cui è stata impedita l'esecuzione del codice da parte di questa funzione nel corpo della funzione quando la funzione è stata chiamata dalla funzione corrente.  Non sono inclusi i conflitti che si sono verificati nelle funzioni chiamate dalla funzione computer chiamante.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano conflitti esclusivi per la funzione in questo contesto.|  
|**Function Address**|Indirizzo o token della funzione.|  
|**Function Name**|Nome completo della funzione.|  
|**Tempo blocco inclusivo**|-   Per la funzione corrente, tempo durante il quale è stata impedita l'esecuzione di questa funzione o di una delle funzioni chiamate da questa funzione.  Non è incluso il tempo blocco nelle funzioni chiamate dalla funzione corrente.<br />-   Per una funzione computer chiamante, quantità di tempo di blocco inclusivo della funzione corrente trascorsa quando questa funzione ha chiamato la funzione corrente.<br />-   Per una funzione computer chiamato, tempo durante il quale è stata impedita l'esecuzione di questa funzione o di una delle funzioni chiamate dalla funzione quando quest'ultima è stata chiamata dalla funzione corrente.  Non è incluso il tempo blocco nelle funzioni chiamate dalla funzione computer chiamato.|  
|**% tempo blocco inclusivo**|Percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco inclusivo per questa funzione in questo contesto.|  
|**Conflitti inclusivi**|-   Per la funzione corrente, numero di volte in cui è stata impedita l'esecuzione di questa funzione o di una delle funzioni chiamate dalla funzione.  Sono inclusi i conflitti che si sono verificati nelle funzioni chiamate dalla funzione.<br />-   Per una funzione computer chiamante, numero di conflitti inclusivi della funzione corrente verificatisi quando questa funzione ha chiamato la funzione corrente.<br />-   Per una funzione computer chiamato, numero di volte in cui è stata impedita l'esecuzione di questa funzione o di una delle funzioni chiamate dalla funzione quando quest'ultima è stata chiamata dalla funzione corrente.  Sono inclusi i conflitti che si sono verificati nelle funzioni chiamate dalla funzione computer chiamante.|  
|**% conflitti inclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano conflitti esclusivi per la funzione in questo contesto.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID del processo in cui si sono verificati i conflitti.|  
|**Nome di processo**|Nome del processo.|  
|**Nome funzione radice**|Nome della funzione corrente.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Strumentazione](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Campionamento](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-instrumentation-data.md)