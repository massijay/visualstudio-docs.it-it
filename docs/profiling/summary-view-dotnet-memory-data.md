---
title: "Visualizzazione Riepilogo: dati di memoria .NET del profiler | Microsoft Docs"
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
  - "Visualizzazione Riepilogo"
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Riepilogo: dati di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Riepilogo vengono visualizzate informazioni sui tipi e sulle funzioni .NET che hanno allocato la quantità di memoria maggiore e sui tipi che sono stati creati più frequentemente in un'esecuzione del profilo.  Per ulteriori informazioni, inclusa una descrizione degli elenchi dei rapporti e dei collegamenti di notifica, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
## Grafico cronologia  
 Il grafico cronologia nella visualizzazione Riepilogo segnala l'utilizzo del processore \(CPU\) in base all'applicazione profilata durante il periodo di esecuzione del profilo.  È possibile utilizzare il grafico cronologia per filtrare la visualizzazione in base a un intervallo di tempo selezionato.  Per ulteriori informazioni, vedere [Procedura: filtrare le visualizzazioni rapporto dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Funzioni che allocano molta memoria  
 Sono elencate le funzioni che hanno allocato il numero maggiore di byte di memoria nell'esecuzione del profilo.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione.|  
|**% byte**|Percentuale di tutti i byte allocati durante l'esecuzione della profilatura che sono stati allocati da questa funzione o da una funzione figlio chiamata da questa funzione.|  
  
## Tipi con molta memoria allocata  
 Sono elencati i tipi per i quali è stato allocato il numero maggiore di byte di memoria nell'esecuzione del profilo.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome del tipo.|  
|**% byte**|Percentuale di tutti i byte allocati nell'esecuzione del profilo che sono stati allocati per questo tipo.|  
  
## Tipi con molte istanze  
 Sono elencati i tipi creati più frequentemente durante l'esecuzione della profilatura.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome del tipo.|  
|**% istanze**|Percentuale del numero totale di oggetti .NET creati durante l'esecuzione del profilo che costituivano istanze di questo tipo.|  
  
## Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-sampling-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-instrumentation-data.md)