---
title: "Visualizzazione dei puntatori all&#39;istruzione (IP, Instruction Pointer): dati di campionamento del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Puntatori all'istruzione (visualizzazione)"
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Visualizzazione dei puntatori all&#39;istruzione (IP, Instruction Pointer): dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione IP dei dati di campionamento sono elencati i dati sulle prestazioni per le istruzioni dell'assembly eseguite direttamente durante la raccolta dei campioni nell'esecuzione del profilo.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene l'istruzione.|  
|**Percorso modulo**|Percorso del modulo che contiene l'istruzione.|  
|**File di origine**|File di origine che contiene l'istruzione.|  
|**Function Name**|Nome della funzione che contiene l'istruzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo di memoria iniziale della funzione nel binario caricato.|  
|**Inizio della riga di codice sorgente**|Numero di riga iniziale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Fine della riga di codice sorgente**|Numero di riga finale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Inizio origine del carattere**|Offset del carattere iniziale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Fine origine del carattere**|Offset del carattere finale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Indirizzo dell'istruzione**|Indirizzo dell'istruzione nel binario caricato.|  
|**Exclusive Samples**|Numero totale dei campioni raccolti durante l'esecuzione dell'istruzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che sono stati raccolti durante l'esecuzione di questa istruzione.|  
  
## Vedere anche  
 [Visualizzazione Puntatori all'istruzione \- Campionamento](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)