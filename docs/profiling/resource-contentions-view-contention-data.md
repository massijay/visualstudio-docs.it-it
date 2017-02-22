---
title: "Visualizzazione Conflitto di risorse: dati su conflitti del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcecontention"
helpviewer_keywords: 
  - "Conflitti tra risorse (visualizzazione)"
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Conflitto di risorse: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Conflitto di risorse sono elencati i dati sui conflitti relativi alle risorse che hanno causato gli eventi di conflitto.  Si verifica un evento di conflitto quando una funzione in un thread deve attendere l'accesso alla risorsa perché una funzione in un altro thread ne ha acquisito l'accesso esclusivo.  Ogni risorsa è il nodo radice di una struttura ad albero delle chiamate in cui vengono visualizzati i percorsi di esecuzione delle funzioni che hanno generato gli eventi di conflitto.  
  
## Valori dati  
  
### Valori della risorsa  
 I dati contenuti in una riga di risorsa indicano il tempo totale durante il quale l'accesso alla risorsa è rimasto bloccato nei dati di profilo e il numero totale di eventi di conflitto che si sono verificati a causa del conflitto di accesso a questa risorsa.  I valori inclusivi ed esclusivi per una risorsa sono sempre gli stessi.  
  
### Valori della funzione  
 I valori della funzione sono basati sulle istanze della funzione che si sono verificate nel percorso di esecuzione rappresentato nella struttura ad albero delle chiamate.  
  
-   I valori esclusivi sono basati sugli eventi che si sono verificati durante l'esecuzione delle istruzioni da parte della funzione nel corpo di quest'ultima.  Gli eventi che si sono verificati nelle funzioni chiamate dalla funzione non sono inclusi nei valori esclusivi.  
  
-   I valori inclusivi sono basati sugli eventi che si sono verificati durante l'esecuzione della funzione o di una funzione chiamata dalla stessa.  
  
### Valori percentuali  
 I valori percentuali sono basati sul tempo totale o sugli eventi di conflitto nei dati di profilo.  Se si filtra il rapporto o la visualizzazione dell'esecuzione del profilo, verranno utilizzati come valore totale solo i conflitti e i tempi di blocco nei dati filtrati.  
  
## Navigazione nella visualizzazione Assegnazione risorse  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della risorsa o della funzione.|  
|**Tempo blocco esclusivo**|-   Per una risorsa, tempo totale durante il quale l'accesso alla risorsa è rimasto bloccato ponendo il thread in uno stato di attesa.<br />-   Per una funzione, tempo durante il quale queste istanze della funzione non hanno potuto accedere alla risorsa padre durante l'esecuzione del codice nel corpo della funzione.  Non è incluso il tempo blocco nelle funzioni chiamate dalla funzione.|  
|**% tempo blocco esclusivo**|-   Per una risorsa, percentuale del tempo blocco nei dati di profilo che costituiva il tempo blocco di questa risorsa<br />-   Per una funzione, percentuale del tempo blocco nei dati di profilo che costituiva il tempo blocco esclusivo di queste istanze della funzione.|  
|**Conflitti esclusivi**|-   Per una risorsa, numero totale di volte in cui l'accesso alla risorsa è risultato bloccato ponendo un thread in uno stato di attesa.<br />-   Per una funzione, numero di volte in cui queste istanze della funzione non hanno potuto accedere alla risorsa padre durante l'esecuzione del codice nel corpo della funzione.  Non sono inclusi gli eventi di blocco nelle funzioni chiamate dalla funzione.|  
|**% conflitti esclusivi**|-   Per una risorsa, percentuale di tutti gli eventi di conflitto nei dati di profilo che costituivano eventi di conflitto per l'accesso a questa risorsa.<br />-   Per una risorsa, percentuale di tutti gli eventi di conflitto nei dati di profilo che costituivano eventi di conflitto esclusivi di queste istanze della funzione per la risorsa padre.|  
|**Tempo blocco inclusivo**|-   Per una risorsa, tempo totale durante il quale l'accesso alla risorsa è rimasto bloccato ponendo il thread in uno stato di attesa.<br />-   Per una funzione, tempo durante il quale queste istanze della funzione o qualsiasi funzione chiamata dalle istanze non hanno potuto accedere alla risorsa padre durante l'esecuzione del codice nel corpo della funzione.|  
|**% tempo blocco inclusivo**|-   Per una risorsa, percentuale del tempo blocco nei dati di profilo che costituiva il tempo blocco di questa risorsa<br />-   Per una funzione, percentuale del tempo blocco nell'esecuzione del profilo che costituiva il tempo blocco inclusivo di queste istanze della funzione.|  
|**Conflitti inclusivi**|-   Per una risorsa, numero totale di volte in cui l'accesso alla risorsa è risultato bloccato ponendo un thread in uno stato di attesa.<br />-   Per una risorsa, percentuale di tutti gli eventi di conflitto nell'esecuzione del profilo che costituivano eventi di conflitto inclusivi di queste istanze della funzione per la risorsa padre.|  
|**% conflitti inclusivi**|-   Per una risorsa, percentuale di tutti gli eventi di conflitto nell'esecuzione del profilo che costituivano eventi di conflitto per l'accesso a questa risorsa.<br />-   Per una funzione, numero di volte in cui queste istanze della funzione non hanno potuto accedere alla risorsa padre durante l'esecuzione del codice nel corpo della funzione.  Non sono inclusi gli eventi di blocco nelle funzioni chiamate dalla funzione.|  
|**Livello**|Profondità di questa funzione nella struttura ad albero delle chiamate.  Solo nei rapporti della riga di comando di [VSPerfReport](../profiling/vsperfreport.md).|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**ID processo**|ID del processo in cui è in esecuzione la funzione.|  
|**Nome di processo**|Nome del processo.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|