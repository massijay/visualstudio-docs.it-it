---
title: "Visualizzazione Moduli: dati di campionamento di memoria .NET del profiler | Microsoft Docs"
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
  - "visualizzazione Moduli"
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Moduli: dati di campionamento di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Moduli dei dati di allocazione di memoria .NET raccolti con il metodo di campionamento raggruppa i dati di memoria in base ai moduli eseguiti nell'esecuzione della profilatura.  Ogni modulo è la radice di una struttura ad albero gerarchica.  Le funzioni del modulo vengono elencate sotto il nodo del modulo.  
  
 I numeri di riga dei file di origine delle istruzioni per l'allocazione di memoria vengono elencati sotto il nodo della funzione e gli indirizzi delle istruzioni che eseguono l'allocazione vengono elencati sotto il nodo della riga.  I valori inclusivi ed esclusivi sono sempre gli stessi sia per i dati di riga che per i dati di istruzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome del modulo, della funzione, del numero di riga o dell'indirizzo dell'istruzione.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Inclusive Allocations**|-   Per una funzione, numero totale di oggetti creati dalla funzione.  Il numero include gli oggetti creati nelle funzioni computer chiamato chiamati da questa funzione.<br />-   Per un modulo, il numero di oggetti in un'esecuzione del profilo che sono stati allocati mentre era in esecuzione almeno una funzione del modulo.  Sono inclusi gli oggetti creati nelle funzioni chiamate dalle funzioni del modulo.<br />-   Per una riga o un'istruzione, numero totale di oggetti allocati dalla riga o dall'istruzione.|  
|**% allocazioni inclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che costituivano allocazioni inclusive del modulo, della funzione, della riga o dell'istruzione.|  
|**Exclusive Allocations**|-   Per la funzione corrente, il numero di oggetti creati durante l'esecuzione di codice del corpo della funzione \(ovvero quando la funzione si trovava nella parte alta dello stack di chiamate\).  Non sono inclusi gli oggetti creati in funzioni chiamate da questa funzione.<br />-   Per un modulo, somma delle allocazioni esclusive delle funzioni nel modulo.<br />-   Per una riga o un'istruzione, numero totale di oggetti creati da questa riga o dall'istruzione.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti allocati nell'esecuzione della profilatura che costituivano allocazioni esclusive del modulo, della funzione, della riga o dell'istruzione.|  
|**Byte inclusivi**|-   Per una funzione, il numero di byte allocati dalla funzione.  Sono inclusi i byte allocati nelle funzioni chiamate da questa funzione.<br />-   Per un modulo, il numero di byte allocati in un'esecuzione del profilo che sono stati allocati mentre era in esecuzione almeno una funzione del modulo.  Sono inclusi gli oggetti creati in tutte le funzioni chiamate dalle funzioni del modulo.<br />-   Per una riga o un'istruzione, numero totale di oggetti creati dalla riga o dall'istruzione.|  
|**% byte inclusivi**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che rappresentavano byte inclusivi del modulo, della funzione, della riga o dell'istruzione.|  
|**Byte esclusivi**|-   Per una funzione, il numero totale di byte allocati dalla funzione.  Non sono inclusi i byte allocati nelle funzioni chiamate da questa funzione.<br />-   Per un modulo, somma dei byte esclusivi allocati dalle funzioni nel modulo.<br />-   Per una riga o un'istruzione, numero totale di oggetti allocati da questa riga o dall'istruzione.|  
|**% byte esclusivi**|Percentuale di tutti i byte allocati nell'esecuzione della profilatura che rappresentavano byte esclusivi del modulo, della funzione, della riga o dell'istruzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Moduli \- Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)