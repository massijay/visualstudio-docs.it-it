---
title: "Visualizzazione Moduli: dati di strumentazione del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "visualizzazione Moduli"
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Visualizzazione Moduli: dati di strumentazione del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Moduli vengono visualizzati i dati di prestazioni raggruppati in base ai moduli presenti nei dati di profilo.  Le funzioni del modulo vengono elencate sotto il nodo del modulo.  
  
## Generale  
 Le colonne generali identificano la funzione in una riga di visualizzazione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione o del modulo.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Number of Calls**|Numero totale di chiamate effettuate alla funzione o al modulo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo in cui è in esecuzione il modulo o la funzione.|  
|**Time Exclusive Probe Overhead**|Sovraccarico temporale per questa funzione o modulo causato dalla strumentazione.|  
|**Time Inclusive Probe Overhead**|Sovraccarico temporale per questa funzione o modulo e relative funzioni figlio causato dalla strumentazione.|  
  
## Valori inclusivi trascorsi  
 I valori inclusivi trascorsi indicano il tempo trascorso da una funzione nello stack di chiamate.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Inclusive Time**|-   Per una funzione, il tempo trascorso nella funzione.  È incluso il tempo trascorso nelle funzioni figlio e nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per un modulo, il periodo di tempo in cui almeno una funzione del modulo si trovava nello stack di chiamate.|  
|**Elapsed Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo trascorso totale del modulo o funzione.|  
|**Tempo inclusivo trascorso medio**|-   Per una funzione, il tempo inclusivo trascorso medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo trascorso medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo trascorso massimo**|-   Per una funzione, il tempo inclusivo trascorso massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo trascorso massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo trascorso minimo**|-   Per una funzione, il tempo inclusivo trascorso minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo inclusivo trascorso minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Valori esclusivi trascorsi  
 I valori esclusivi trascorsi indicano il tempo di esecuzione diretta di una funzione nella parte alta dello stack di chiamate.  È incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma non è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Elapsed Exclusive Time**|-   Per una funzione, il tempo trascorso nel modulo o nella funzione.  È escluso il tempo trascorso nelle funzioni figlio, ma sono incluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per un modulo, somma dei tempi esclusivi trascorsi delle funzioni nel modulo.|  
|**Elapsed Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo trascorso totale di questo modulo o funzione.|  
|**Tempo esclusivo trascorso medio**|-   Per una funzione, il tempo esclusivo trascorso medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo trascorso medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo trascorso massimo**|-   Per una funzione, il tempo esclusivo trascorso massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo trascorso massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo trascorso minimo**|-   Per una funzione, il tempo esclusivo trascorso minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo esclusivo trascorso minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Valori inclusivi applicazione  
 I valori inclusivi applicazione indicano il tempo trascorso da una funzione nello stack di chiamate.  Non è incluso il tempo trascorso nelle chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output, ma è incluso il tempo trascorso nelle funzioni figlio.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Inclusive Time**|-   Per una funzione, il tempo trascorso per le chiamate alla funzione.  È incluso il tempo trascorso nelle funzioni figlio, ma sono escluse le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.<br />-   Per un modulo, il periodo di tempo in cui almeno una funzione del modulo si trovava nello stack di chiamate.  Non include il tempo trascorso nelle chiamate al sistema operativo.|  
|**Application Inclusive Time %**|Percentuale del tempo inclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo inclusivo applicazione di questo modulo o funzione.|  
|**Tempo inclusivo applicazione medio**|-   Per una funzione, il tempo inclusivo applicazione medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione massimo**|-   Per una funzione, il tempo inclusivo applicazione massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo inclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo inclusivo applicazione minimo**|-   Per una funzione, il tempo inclusivo applicazione minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo inclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Valori esclusivi applicazione  
 I valori esclusivi applicazione indicano il tempo trascorso nel modulo o nella funzione.  È escluso il tempo trascorso nelle funzioni figlio e le chiamate al sistema operativo, ad esempio cambi di contesto e operazioni di input\/output.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Application Exclusive Time**|Tempo esclusivo applicazione totale di tutte le chiamate al modulo o alla funzione.|  
|**Application Exclusive Time %**|Percentuale del tempo esclusivo trascorso totale dell'esecuzione del profilo trascorso nel tempo esclusivo applicazione di questo modulo o funzione.|  
|**Tempo esclusivo applicazione medio**|-   Per una funzione, il tempo esclusivo applicazione medio di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo applicazione medio di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione massimo**|-   Per una funzione, il tempo esclusivo applicazione massimo di una chiamata a questa funzione.<br />-   Per un modulo, il tempo esclusivo applicazione massimo di tutte le chiamate a funzioni nel modulo.|  
|**Tempo esclusivo applicazione minimo**|-   Per una funzione, il tempo esclusivo applicazione minimo di una chiamata al modulo o alla funzione.<br />-   Per un modulo, il tempo esclusivo applicazione minimo di tutte le chiamate a funzioni nel modulo.|  
  
## Vedere anche  
 [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)   
 [Visualizzazione Moduli \- Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli \- Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)