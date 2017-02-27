---
title: "Visualizzazione Riepilogo: dati di campionamento del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "profilatura del campionamento (metodo), Visualizzazione Riepilogo"
  - "Visualizzazione Riepilogo"
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Visualizzazione Riepilogo: dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Riepilogo vengono visualizzate informazioni sulle funzioni che influiscono maggiormente sulle prestazioni durante un'esecuzione del profilo.  Per ulteriori informazioni, inclusa una descrizione degli elenchi dei rapporti e dei collegamenti di notifica, vedere [Visualizzazione Riepilogo](../profiling/summary-view.md).  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Grafico cronologia  
 Il grafico cronologia nella visualizzazione Riepilogo rappresenta la percentuale di utilizzo del processore \(CPU\) dell'applicazione profilata durante il periodo di esecuzione del profilo.  È possibile utilizzare il grafico cronologia per filtrare la visualizzazione in base a un intervallo di tempo selezionato.  Per ulteriori informazioni, vedere [Procedura: filtrare le visualizzazioni rapporto dalla sequenza temporale di riepilogo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Percorso ricorrente  
 In **Percorso critico** viene visualizzato il percorso di esecuzione in cui viene raccolta la maggior parte dei campioni.  È possibile fare clic su una funzione per visualizzare la visualizzazione Dettagli funzione per la funzione.  Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione, quindi fare clic su una visualizzazione nell'elenco.  
  
 **Percorso critico** include i dati seguenti per ogni funzione:  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione.|  
|**% campioni inclusivi**|Percentuale di tutti i campioni che si sono verificati durante l'esecuzione di questa funzione o di una funzione chiamata da questa funzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni che si sono verificati durante l'esecuzione della funzione nel corpo della funzione.  Non sono inclusi i campioni raccolti nelle funzioni chiamate da questa funzione.|  
  
## Funzioni con più lavoro individuale  
 Nell'elenco **Funzioni con più lavoro individuale** vengono visualizzate le funzioni che presentano il numero di campioni esclusivi più elevato nell'esecuzione del profilo.  Un campione esclusivo viene assegnato a una funzione se il campione viene raccolto durante l'esecuzione del codice della funzione.  Un campione esclusivo non viene assegnato a una funzione se il campione viene raccolto quando la funzione chiama un'altra funzione.  Un numero di campioni esclusivi elevato indica che è trascorsa una quantità significativa di tempo nella funzione stessa.  
  
 È possibile fare clic su una funzione per visualizzare la visualizzazione Dettagli funzione per la funzione.  Per visualizzare altre visualizzazioni per la funzione, fare clic con il pulsante destro del mouse sulla funzione, quindi fare clic su una visualizzazione nell'elenco.  
  
 Per ogni funzione, **Funzioni con più lavoro individuale** include i dati seguenti:  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che sono stati raccolti durante l'esecuzione del codice nel corpo della funzione.  Sono esclusi i campioni che sono stati raccolti durante l'esecuzione delle funzioni chiamate da questa funzione.|  
  
## Vedere anche  
 [Visualizzazione Riepilogo](../profiling/summary-view-dotnet-memory-data.md)   
 [Visualizzazione Riepilogo](../profiling/summary-view-instrumentation-data.md)