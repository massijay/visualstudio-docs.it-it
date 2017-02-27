---
title: "Visualizzazione Moduli: dati di campionamento del profiler | Microsoft Docs"
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
  - "profilatura del campionamento (metodo), visualizzazione Moduli"
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Visualizzazione Moduli: dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Moduli dei dati di campionamento vengono visualizzati i dati di prestazioni raggruppati in base ai moduli campionati nei dati di profilo.  Ogni modulo è la radice di una struttura ad albero gerarchica.  Le funzioni campionate del modulo vengono elencate nel nodo del modulo.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Se era in corso l'esecuzione della funzione quando sono stati raccolti i campioni, ovvero la funzione si trovava nella parte alta dello stack di chiamate, le righe di codice sorgente e gli indirizzi delle istruzioni in esecuzione vengono elencati nel nodo della funzione.  Poiché i dati vengono raccolti per una riga di codice sorgente o per un puntatore all'istruzione durante l'esecuzione della riga o dell'istruzione, i valori inclusivi ed esclusivi sono sempre gli stessi sia per i dati di riga che per i dati di istruzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome del modulo, della funzione, del numero di riga o dell'indirizzo del puntatore all'istruzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la funzione, la riga o il puntatore all'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene il modulo, la funzione, la riga o il puntatore all'istruzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Inclusive Samples**|-   Per una funzione, numero di campioni in cui era in corso l'esecuzione di questa funzione o di una funzione chiamata da questa funzione, ovvero numero di campioni dello stack di chiamate che contenevano questa funzione.<br />-   Per un modulo, numero di campioni in cui almeno una funzione del modulo era in esecuzione.<br />-   Per una riga o un'istruzione, numero di campioni in cui era in esecuzione questa riga o questa istruzione.|  
|**% campioni inclusivi**|-   Per una funzione o un modulo, percentuale di tutti i campioni nell'esecuzione del profilo che costituivano campioni inclusivi di questa funzione o di questo modulo.<br />-   Per una riga o un'istruzione, percentuale di tutti i campioni nell'esecuzione del profilo in cui era in esecuzione questa riga o questa istruzione.|  
|**Exclusive Samples**|-   Per una funzione, numero di campioni dello stack di chiamate in cui era in corso l'esecuzione diretta di questa funzione, ovvero numero di campioni in cui questa funzione si trovava nello stack di chiamate.<br />-   Per un modulo, somma dei campioni esclusivi delle funzioni nel modulo.<br />-   Per una riga o un'istruzione, numero di campioni in cui era in esecuzione questa riga o questa istruzione.|  
|**% campioni esclusivi**|-   Per una funzione o un modulo, percentuale di tutti i campioni nell'esecuzione del profilo che costituivano campioni esclusivi di questa funzione o di questo modulo.<br />-   Per una riga o un'istruzione, percentuale di tutti i campioni nell'esecuzione del profilo in cui era in esecuzione questa riga o questa istruzione.|  
  
## Vedere anche  
 [Visualizzazione Moduli \- Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli \- Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)