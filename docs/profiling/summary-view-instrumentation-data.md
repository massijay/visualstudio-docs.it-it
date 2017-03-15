---
title: "Visualizzazione Riepilogo: dati di strumentazione del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visualizzazione Riepilogo"
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Visualizzazione Riepilogo: dati di strumentazione del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Riepilogo vengono visualizzate informazioni sulle funzioni che influiscono maggiormente sulle prestazioni durante un'esecuzione del profilo.  Per ulteriori informazioni, inclusa una descrizione degli elenchi dei rapporti e dei collegamenti di notifica, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
## Grafico cronologia  
 Il grafico cronologia nella visualizzazione Riepilogo segnala l'utilizzo del processore \(CPU\) in base all'applicazione profilata durante il periodo di esecuzione del profilo.  È possibile utilizzare il grafico cronologia per filtrare la visualizzazione in base a un intervallo di tempo selezionato.  Per ulteriori informazioni, vedere [Procedura: filtrare le visualizzazioni rapporto dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Percorso ricorrente  
 In **Percorso critico** viene visualizzato il percorso di esecuzione che ha richiesto la quantità di tempo maggiore.  È possibile fare clic su una funzione per visualizzare la visualizzazione Dettagli funzione per la funzione.  Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione, quindi fare clic su una visualizzazione nell'elenco.  
  
 **Percorso critico** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo nei dati di profilo richiesto dalla funzione per l'esecuzione del codice nel corpo della funzione e nelle funzioni da essa chiamate.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo nei dati di profilo richiesto dalla funzione per l'esecuzione del codice nel corpo della funzione stessa.  Non è incluso il tempo trascorso nelle funzioni chiamate dalla funzione stessa.|  
  
## Funzioni con più lavoro individuale  
 Elenco delle funzioni che hanno richiesto la quantità di tempo maggiore per l'esecuzione del codice nel corpo della funzione e non nelle funzioni da essa chiamate.  
  
 **Funzioni con più lavoro individuale** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione.|  
|**Percentuale tempo esclusivo**|Percentuale del tempo nei dati di profilo richiesto dalla funzione per l'esecuzione del codice nel corpo della funzione stessa.  Non è incluso il tempo trascorso nelle funzioni chiamate dalla funzione stessa.|  
  
## Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-sampling-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-dotnet-memory-data.md)