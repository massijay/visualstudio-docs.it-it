---
title: "Visualizzazione Riepilogo: visualizzazione dei conflitti tra le risorse del profiler | Microsoft Docs"
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
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Visualizzazione Riepilogo: visualizzazione dei conflitti tra le risorse del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Riepilogo vengono visualizzate informazioni sugli eventi dell'applicazione in cui un thread o un processo in attesa di accedere a una risorsa è stato sospeso.  
  
 Per ulteriori informazioni, inclusa una descrizione degli elenchi dei rapporti e dei collegamenti di notifica, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
## Grafico cronologia  
 Nel grafico cronologia della visualizzazione Riepilogo è riportato il numero di eventi di conflitto dell'applicazione profilata che si sono verificati nel corso del profilo.  È possibile utilizzare il grafico cronologia per filtrare la visualizzazione in base a un intervallo di tempo selezionato.  Per ulteriori informazioni, vedere [Procedura: filtrare le visualizzazioni rapporto dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Risorse con più conflitti  
 In **Risorse con più conflitti** sono elencate le risorse dell'applicazione che hanno causato la maggior parte degli eventi di conflitto.  È possibile fare clic sul nome di una risorsa per visualizzare la visualizzazione Conflitti.  Nella visualizzazione Conflitti viene fornita una cronologia temporale dettagliata dei conflitti di risorse in base al thread.  
  
 Per ogni risorsa **Risorse con più conflitti** include i dati seguenti.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Il nome della risorsa.|  
|**% conflitti**|Percentuale di tutti gli eventi di conflitto nei dati di profilo che costituivano conflitti con questa risorsa.|  
  
## Thread con più conflitti  
 In **Thread con più conflitti** sono elencati i thread dell'applicazione su cui si è verificata la maggior parte degli eventi di conflitto.  È possibile fare clic sul nome del thread per aprire la visualizzazione Conflitti contenente una cronologia temporale dettagliata dei conflitti di risorse in base al thread.  
  
 Per ogni thread **Thread con più conflitti** include i dati seguenti.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID**|Identificatore del thread.|  
|**Nome**|Nome del processo proprietario del thread.|  
|**% conflitti**|Percentuale di tutti gli eventi di conflitto nei dati di profilo che costituivano conflitti con questa risorsa.|