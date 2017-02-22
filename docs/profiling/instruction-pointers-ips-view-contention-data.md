---
title: "Visualizzazione dei puntatori all&#39;istruzione (IP, Instruction Pointer): dati su conflitti del profiler | Microsoft Docs"
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
  - "Puntatori all'istruzione (visualizzazione)"
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione dei puntatori all&#39;istruzione (IP, Instruction Pointer): dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione IP dei dati di conflitto sono elencati i dati per le istruzioni dell'assembly di cui è stata impedita l'esecuzione durante l'esecuzione del profilo.  
  
 Nella tabella seguente vengono illustrati i valori delle colonne nella visualizzazione dei puntatori all'istruzione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Tempo blocco esclusivo**|Tempo blocco in questa funzione.|  
|**% tempo blocco esclusivo**|Percentuale di tempo blocco durante l'esecuzione dell'istruzione.|  
|**Conflitti esclusivi**|Numero di conflitti che si sono verificati durante l'esecuzione dell'istruzione.|  
|**% conflitti esclusivi**|Percentuale di tutti i conflitti nell'esecuzione del profilo che si sono verificati durante l'esecuzione dell'istruzione.|  
|**Function Address**|Indirizzo di memoria iniziale della funzione nel binario caricato.|  
|**Function Name**|Nome della funzione che contiene l'istruzione.|  
|**Indirizzo dell'istruzione**|Indirizzo di memoria dell'istruzione nel binario caricato.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Module Name**|Nome del modulo che contiene l'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|  
|**ID processo**|ID del processo profilato.|  
|**Nome di processo**|Nome del processo.|  
|**Inizio origine del carattere**|Offset del carattere nella riga del file di origine dove inizia questa istruzione.|  
|**Fine origine del carattere**|Offset del carattere nella riga del file di origine dove termina questa istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Inizio della riga di codice sorgente**|Numero di riga del file di origine dove inizia questa istruzione.|  
|**Fine della riga di codice sorgente**|Numero di riga del file di origine dove termina questa istruzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Puntatori all'istruzione](../profiling/instruction-pointers-ips-view.md)   
 [Visualizzazione Puntatori all'istruzione \- Campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Puntatori all'istruzione](../profiling/instruction-pointers-ips-view-sampling-data.md)