---
title: "Visualizzazione Moduli: dati su conflitti del profiler | Microsoft Docs"
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
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Visualizzazione Moduli: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Moduli dei dati su conflitti vengono visualizzati i dati di concorrenza raggruppati in base ai moduli campionati nei dati di profilo.  Ogni modulo è la radice di una struttura ad albero gerarchica.  Le funzioni del modulo in cui si sono verificati eventi di conflitto sono elencate nel nodo del modulo.  
  
 Se quando si è verificato un evento di conflitto era in esecuzione il codice della funzione, ovvero la funzione si trovava nella parte alta dello stack di chiamate, le righe di codice sorgente e gli indirizzi delle istruzioni in esecuzione sono elencati nel nodo della funzione.  Poiché i dati vengono raccolti per una riga di codice sorgente o per un puntatore all'istruzione durante l'esecuzione della riga o dell'istruzione, i valori inclusivi ed esclusivi sono sempre gli stessi sia per i dati di riga che per i dati di istruzione.  
  
 Nella tabella seguente vengono descritti i valori delle colonne nella visualizzazione Moduli dei dati di conflitto.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Tempo blocco esclusivo**|-   Per una funzione, tempo durante il quale è stata impedita l'esecuzione del codice nel corpo della funzione.  Non è incluso il tempo blocco nelle funzioni chiamate dalla funzione.<br />-   Per un modulo, somma dei tempi blocco esclusivi delle funzioni nel modulo.<br />-   Per una riga o un'istruzione, tempo durante il quale è stata impedita l'esecuzione di questa riga o istruzione.|  
|**% tempo blocco esclusivo**|-   Per una funzione o un modulo, percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco esclusivo di questa funzione o modulo.<br />-   Per una riga o un'istruzione, percentuale del tempo blocco nell'esecuzione del profilo in cui è stata impedita l'esecuzione di questa riga o istruzione.|  
|**Conflitti esclusivi**|-   Per una funzione, numero di volte in cui è stata impedita l'esecuzione del codice nel corpo della funzione.  Non sono inclusi i conflitti nelle funzioni chiamate dalla funzione.<br />-   Per un modulo, somma dei conflitti esclusivi delle funzioni nel modulo.<br />-   Per una riga o un'istruzione, numero di volte in cui è stata impedita l'esecuzione di questa riga o istruzione.|  
|**% conflitti esclusivi**|-   Per una funzione o modulo, percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano i conflitti esclusivi di questa funzione o modulo.<br />-   Per una riga o istruzione, percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano i conflitti che hanno impedito l'esecuzione di questa riga o istruzione.|  
|**Tempo blocco inclusivo**|-   Per una funzione, tempo durante il quale è stata impedita l'esecuzione di questa funzione o di una funzione chiamata da questa funzione.<br />-   Per un modulo, somma del tempo blocco in cui almeno una funzione di questo modulo si trovava nello stack.<br />-   Per una riga o un'istruzione, tempo durante il quale è stata impedita l'esecuzione di questa riga o istruzione.|  
|**% tempo blocco inclusivo**|-   Per una funzione o un modulo, percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco inclusivo di questa funzione o modulo.<br />-   Per una riga o un'istruzione, percentuale del tempo blocco nell'esecuzione del profilo in cui era in corso l'esecuzione di questa riga o istruzione.|  
|**Conflitti inclusivi**|-   Per una funzione, numero di volte in cui è stata impedita l'esecuzione di questa funzione o di una funzione chiamata da questa funzione.<br />-   Per un modulo, numero dei conflitti in cui almeno una funzione di questo modulo si trovava nello stack.<br />-   Per una riga o un'istruzione, numero di volte in cui è stata impedita l'esecuzione di questa riga o istruzione.|  
|**% conflitti inclusivi**|-   Per una funzione o un modulo, percentuale di tutti i conflitti nell'esecuzione del profilo che costituivano i conflitti inclusivi di questa funzione o modulo.<br />-   Per una riga o un'istruzione, percentuale del tempo blocco nell'esecuzione del profilo in cui era in corso l'esecuzione di questa riga o istruzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene la funzione, la riga o il puntatore all'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene il modulo, la funzione, la riga o il puntatore all'istruzione.|  
|**Nome**|Nome della funzione o del modulo.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Moduli](../profiling/modules-view.md)   
 [Visualizzazione Moduli \- Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli \- Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)