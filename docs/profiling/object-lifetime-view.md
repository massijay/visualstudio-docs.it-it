---
title: "Visualizzazione Durata oggetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.objectlifetime"
helpviewer_keywords: 
  - "durata, oggetti"
  - "Durata oggetti (visualizzazione)"
  - "rapporti di prestazioni, Durata oggetti (visualizzazione)"
  - "rapporti degli strumenti di profilatura, visualizzazione Durata oggetti"
  - "strumenti di profilatura, visualizzazione Durata oggetti"
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Durata oggetti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Durata oggetti è disponibile quando è selezionata l'opzione **Raccogliere anche le informazioni sulla durata dell'oggetto .NET** nelle pagine delle proprietà Sessione prestazioni.  
  
 Il Garbage Collector di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] gestisce l'allocazione e il rilascio di memoria per l'applicazione.  Per ottimizzare le prestazioni del Garbage Collector, l'heap gestito è diviso in tre generazioni: 0, 1 e 2.  Il Garbage Collector del runtime archivia i nuovi oggetti nella generazione 0.  Gli oggetti non raccolti vengono promossi e archiviati nelle generazioni 1 e 2.  
  
 Il Garbage Collector recupera memoria deallocando un'intera generazione di oggetti.  Per gli oggetti creati dall'applicazione profilata, nella visualizzazione Durata oggetti vengono visualizzati il numero e le dimensioni degli oggetti e la generazione durante la quale vengono recuperati.  
  
## Generale  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Nome classe**|Nome della classe del tipo allocato.|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
  
## Dati relativi alle istanze  
 I dati relativi alle istanze indicano il numero di oggetti del tipo creati durante l'esecuzione della profilatura e la generazione in cui gli oggetti sono stati deallocati dal Garbage Collector.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Istanze**|Numero di allocazioni di oggetti del tipo.|  
|**% istanze totali**|Percentuale del numero totale di allocazioni eseguite durante l'esecuzione della profilatura.|  
|**Istanze di generazione 0 raccolte**|Numero di istanze del tipo deallocate nella generazione 0 dell'algoritmo del Garbage Collector.|  
|**Istanze di generazione 1 raccolte**|Numero di istanze del tipo deallocate nella generazione 1 dell'algoritmo del Garbage Collector.|  
|**Istanze di generazione 2 raccolte**|Numero di istanze del tipo deallocate nella generazione 2 dell'algoritmo del Garbage Collector.|  
|**Istanze attive alla fine**|Numero di istanze del tipo non deallocate fino alla fine dell'esecuzione della profilatura.|  
  
## Dati relativi alle dimensioni \(byte\)  
 I dati relativi alle dimensioni \(byte\) indicano le dimensioni degli oggetti del tipo creati durante l'esecuzione della profilatura e la quantità di memoria recuperata in ogni generazione in cui è avvenuta la deallocazione degli oggetti.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Totale byte allocati**|Numero totale di byte per tutte le istanze del tipo.|  
|**% byte totali**|Percentuale del numero totale di byte allocati durante l'esecuzione della profilatura per le istanze del tipo.|  
|**Byte di generazione 0 raccolti**|Dimensioni delle istanze del tipo deallocate nella generazione 0 dell'algoritmo del Garbage Collector.|  
|**Byte di generazione 1 raccolti**|Dimensioni delle istanze del tipo deallocate nella generazione 1 dell'algoritmo del Garbage Collector.|  
|**Byte di generazione 2 raccolti**|Dimensioni delle istanze del tipo deallocate nella generazione 2 dell'algoritmo del Garbage Collector.|  
  
## Dati relativi all'heap degli oggetti grandi  
 L'allocatore di memoria .NET gestisce oggetti molto grandi in una posizione distinta dall'heap gestito standard.  I dati relativi all'heap degli oggetti grandi indicano il numero e le dimensioni degli oggetti del tipo gestiti in questa posizione.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Istanze di heap oggetti grandi raccolte**|Numero di istanze del tipo individuate nell'heap degli oggetti grandi e raccolte durante l'esecuzione della profilatura.|  
|**Byte di heap oggetti grandi raccolti**|Dimensioni, in byte, delle istanze di questo tipo individuate nell'heap degli oggetti grandi e raccolte durante l'esecuzione della profilatura.|  
  
## Vedere anche  
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)