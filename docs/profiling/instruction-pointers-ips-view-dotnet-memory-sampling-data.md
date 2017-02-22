---
title: "Visualizzazione dei puntatori all&#39;istruzione (IP, Instruction Pointer): dati di campionamento di memoria .NET del profiler | Microsoft Docs"
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
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione dei puntatori all&#39;istruzione (IP, Instruction Pointer): dati di campionamento di memoria .NET del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione IP dei dati di profilatura sull'allocazione di memoria .NET raccolti utilizzando il metodo di campionamento vengono elencate le istruzioni di assembly che hanno allocato la memoria durante l'esecuzione della profilatura.  Nelle colonne della visualizzazione vengono inoltre elencati la dimensione e il numero delle allocazioni.  
  
 Sono elencati solo i valori esclusivi.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene l'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Function Name**|Nome della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo iniziale della funzione.|  
|**Inizio della riga di codice sorgente**|Numero di riga iniziale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Fine della riga di codice sorgente**|Numero di riga finale nel file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Inizio origine del carattere**|Offset del carattere iniziale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Fine origine del carattere**|Offset del carattere finale nella riga del file di origine in corrispondenza del quale si è verificata l'allocazione.|  
|**Indirizzo dell'istruzione**|Indirizzo dell'istruzione.|  
|**Exclusive Allocations**|Numero totale di oggetti creati dall'istruzione.|  
|**% allocazioni esclusive**|Percentuale di tutti gli oggetti creati nell'esecuzione della profilatura che sono stati allocati dall'istruzione.|  
|**Byte esclusivi**|Numero di byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati dall'istruzione.|  
|**% byte esclusivi**|Percentuale di tutti i byte di memoria allocati nell'esecuzione della profilatura che sono stati allocati dall'istruzione.|  
  
## Vedere anche  
 [Visualizzazione Puntatori all'istruzione](../profiling/instruction-pointers-ips-view-sampling-data.md)