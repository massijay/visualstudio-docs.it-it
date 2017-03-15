---
title: "Canali (visualizzazione Thread) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.channelnames"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, canali (visualizzazione Thread)"
ms.assetid: 2f798c17-2363-42a4-be94-a5751d208eac
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Canali (visualizzazione Thread)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il visualizzatore di concorrenza mostra quattro tipi di canali: canali dei thread, canali dei dischi, canali del marcatore e canali della GPU.  
  
## Canali di thread  
 Un canale di thread mostra lo stato del thread, in base al colore, per un solo thread.  Se ci si posiziona sul nome del canale, viene visualizzata la funzione di avvio per il thread specificato.  Il visualizzatore della concorrenza rileva diversi tipi di thread.  Nella tabella seguente sono riportati i tipi più comuni.  
  
|||  
|-|-|  
|Thread principale|Il thread che ha avviato l'app.|  
|Thread processo di lavoro|Un thread creato dal thread principale dell'applicazione.|  
|Thread processo di lavoro CLR|Un thread di lavoro creato dal Common Language Runtime \(CLR\).|  
|Thread di supporto del debugger|Un thread di lavoro creato dal debugger di Visual Studio.|  
|Thread ConcRT|Un thread creato dal runtime di concorrenza Microsoft.|  
|Thread GDI|Un thread creato da GDIPlus.|  
|Thread OLE\/RPC|Un thread creato come thread di lavoro RPC.|  
|Thread RPC|Un thread creato come thread RPC.|  
|Thread Winsock|Un thread creato come thread Winsock.|  
|Pool di thread|Un thread creato dal pool di thread CLR.|  
  
## Canali di dischi  
 I canali dei dischi corrispondono alle unità fisiche nel computer.  Poiché esistono canali separati per operazioni di lettura e scrittura per ogni unità fisica sul sistema, ogni unità dispone di due canali.  I numeri dei dischi corrispondono ai nomi dei dispositivi del kernel.  Un canale del disco viene visualizzato solo se c'era attività sul disco.  
  
## Canali del marcatore  
 I canali del marcatore corrispondono agli eventi generati dall'applicazione e dalle librerie che essa utilizza.  Ad esempio, Task Parallel Library, Parallel Patterns Library, e AMP C\+\+ generano eventi che vengono visualizzati come marcatori.  Ogni canale del marcatore viene associato a un ID del thread, visualizzato accanto alla descrizione del canale.  L'id identifica il thread che ha generato l'evento.  La descrizione del canale include il nome del provider ETW \(Event Tracing for Windows\) che ha generato l'evento.  Se il canale visualizza eventi da [SDK del visualizzatore di concorrenza](../profiling/concurrency-visualizer-sdk.md), il nome della serie viene visualizzato.  
  
## Canali della GPU  
 I canali della GPU visualizzano informazioni sull'attività DirectX 11 nel sistema.  Ogni motore DirectX associato alla scheda grafica possiede un canale separato.  I segmenti singoli rappresentano il tempo impiegato per l'elaborazione di un pacchetto DMA.  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)