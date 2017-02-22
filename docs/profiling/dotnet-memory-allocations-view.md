---
title: "Visualizzazione Allocazioni per la memoria .NET | Microsoft Docs"
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
  - "vs.performance.view.allocation"
helpviewer_keywords: 
  - "Allocazioni (visualizzazione)"
  - "rapporti di prestazioni, visualizzazione allocazione"
  - "rapporti degli strumenti di profilatura, visualizzazione Allocazione"
  - "strumenti di profilatura, visualizzazione Allocazione"
ms.assetid: 01eb876e-c413-4516-977b-4f896929e8a6
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Allocazioni per la memoria .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Allocazioni sono elencati i tipi creati durante l'esecuzione della profilatura.  Ogni tipo è il nodo radice di una struttura ad albero delle chiamate in cui vengono visualizzati i percorsi di esecuzione delle funzioni restituiti nelle allocazioni del tipo.  
  
 I dati inclusi in una riga del tipo indicano il numero totale di oggetti del tipo creati durante l'esecuzione della profilatura e il numero totale di byte allocati per gli oggetti di tale tipo.  I valori inclusivi ed esclusivi per un tipo sono sempre gli stessi.  
  
-   I valori inclusivi sono relativi a oggetti creati nelle istanze della funzione e delle relative funzioni figlio chiamate dalla funzione padre nella struttura ad albero delle chiamate.  
  
-   I valori esclusivi sono relativi agli oggetti creati direttamente dalla funzione quando sono stati chiamati dalla funzione padre.  Non sono inclusi gli oggetti creati nelle funzioni figlio.  
  
 I dati per una funzione indicano il numero di oggetti creati e il numero di byte allocati per gli oggetti del tipo padre.  
  
## Evidenziazione del percorso critico di esecuzione  
 È possibile trovare il percorso di esecuzione della struttura ad albero delle chiamate che ha creato la maggior parte degli oggetti del tipo padre.  
  
-   Per visualizzare il percorso più attivo, fare clic con il pulsante destro del mouse sul tipo o la funzione, quindi scegliere **Espandi percorso critico**.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome**|Nome della funzione o del tipo allocato.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene il tipo o la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene il tipo o la funzione.|  
|**File di origine**|File di origine che contiene la definizione per il tipo o la funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio della definizione del tipo o della funzione nel file di origine.|  
|**Livello**|Indica se i dati sono relativi a un tipo o a una funzione.|  
|**Inclusive Allocations**|-   Per una funzione, numero totale di oggetti del tipo padre creati dalla funzione.  Tale numero include gli oggetti creati nelle funzioni figlio.<br />-   Per un tipo, numero totale di istanze del tipo create.|  
|**% allocazioni inclusive**|-   Per una funzione, percentuale di tutti gli oggetti creati durante l'esecuzione della profilatura che corrispondono ad allocazioni inclusive del tipo padre da parte della funzione.<br />-   Per un tipo, percentuale del numero totale di oggetti creati durante l'esecuzione della profilatura che corrispondono a istanze del tipo.|  
|**Exclusive Allocations**|-   Per una funzione, numero di oggetti creati durante l'esecuzione diretta della funzione nella parte superiore dello stack di chiamate.  Tale numero non include gli oggetti creati nelle funzioni figlio.<br />-   Per un tipo, numero totale di istanze del tipo create.|  
|**% allocazioni esclusive**|-   Per una funzione, percentuale di tutti gli oggetti creati durante l'esecuzione della profilatura che corrispondono ad allocazioni esclusive del tipo padre da parte della funzione.<br />-   Per un tipo, percentuale del numero totale di oggetti creati durante l'esecuzione della profilatura che corrispondono a istanze del tipo.|  
|**Byte inclusivi**|-   Per una funzione, numero di byte di memoria allocati dalla funzione per oggetti del tipo padre.  Questo numero include la memoria allocata dalle funzioni figlio.<br />-   Per un tipo, numero totale di byte allocati durante l'esecuzione della profilatura per le istanze di tale tipo.|  
|**% byte inclusivi**|-   Per una funzione, percentuale di tutta la memoria allocata durante l'esecuzione della profilatura che corrisponde ad allocazioni inclusive del tipo padre da parte della funzione.<br />-   Per un tipo, percentuale di tutta la memoria allocata durante l'esecuzione della profilatura per istanze del tipo.|  
|**Byte esclusivi**|-   Per una funzione, numero di byte di memoria allocati dalla funzione per oggetti del tipo padre.  Questo numero non include la memoria allocata dalle funzioni figlio.<br />-   Per un tipo, numero totale di byte allocati durante l'esecuzione della profilatura per le istanze del tipo.|  
|**% byte esclusivi**|-   Per una funzione, percentuale di tutta la memoria allocata durante l'esecuzione della profilatura che corrisponde ad allocazioni esclusive del tipo padre da parte della funzione.<br />-   Per un tipo, percentuale di tutta la memoria allocata durante l'esecuzione della profilatura per istanze del tipo.|