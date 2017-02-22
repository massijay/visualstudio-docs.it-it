---
title: "Visualizzazione Funzioni: dati su conflitti del profiler | Microsoft Docs"
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
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Funzioni: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione rapporto Funzioni dei dati su conflitti sono elencate le funzioni di cui è stata impedita l'esecuzione durante l'esecuzione del profilo.  
  
 Nella tabella seguente vengono descritti i valori visualizzati nella visualizzazione Funzioni di un file dei dati di profilo che sono stati raccolti tramite il metodo di concorrenza.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Tempo blocco esclusivo**|Quantità di tempo durante la quale è stata impedita l'esecuzione del codice nel corpo di questa funzione.  Non è incluso il tempo blocco nelle funzioni chiamate dalla funzione.|  
|**% tempo blocco esclusivo**|Percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco esclusivo di questa funzione.|  
|**Conflitti esclusivi**|Numero di volte in cui è stata impedita l'esecuzione del codice nel corpo di questa funzione.  Non sono inclusi i conflitti nelle funzioni chiamate dalla funzione.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano conflitti esclusivi di questa funzione.|  
|**Function Address**|Indirizzo della funzione.|  
|**Function Name**|Nome completo della funzione.|  
|**Tempo blocco inclusivo**|Tempo durante il quale è stata impedita l'esecuzione di questa funzione o di una funzione chiamata da questa funzione.|  
|**% tempo blocco inclusivo**|Percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco inclusivo di questa funzione o modulo.|  
|**Conflitti inclusivi**|Numero di volte in cui è stata impedita l'esecuzione di questa funzione o di una funzione chiamata da questa funzione.|  
|**% conflitti inclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano conflitti inclusivi di questa funzione o modulo.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID del processo in cui è in esecuzione la funzione.|  
|**Nome di processo**|Nome del processo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Funzioni](../profiling/functions-view.md)   
 [Visualizzazione Funzioni \- Strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Funzioni \- Campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-sampling-data.md)