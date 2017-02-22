---
title: "Visualizzazione Righe: dati di campionamento del profiler | Microsoft Docs"
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
  - "Righe (visualizzazione)"
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Righe: dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Righe dei dati di campionamento sono elencati i dati di prestazioni per le istruzioni eseguite durante la raccolta dei campioni nell'esecuzione del profilo.  
  
> [!NOTE]
>  Le funzioni di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio.  Le applicazioni Windows Store richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In un file di origine un'istruzione può occupare più di una riga e una singola riga può includere più di un'istruzione.  Un'istruzione viene identificata da quanto segue:  
  
-   File di origine che contiene l'istruzione della funzione.  
  
-   Funzione che contiene l'istruzione.  
  
-   Riga di codice sorgente in cui inizia l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale inizia l'istruzione.  
  
-   Riga di codice sorgente in cui termina l'istruzione.  
  
-   Carattere nella riga di codice sorgente in corrispondenza del quale termina l'istruzione.  
  
 Nella colonna Nome riga viene fornita una concatenazione ordinabile dei dati dell'identificatore.  
  
 Per definizione, un'istruzione non chiama altre funzioni.  Di conseguenza, vengono elencati solo i valori esclusivi.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la riga di funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la riga di funzione.|  
|**File di origine**|File di origine che contiene la riga di funzione.|  
|**Function Name**|Nome della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo iniziale della funzione.|  
|**Inizio della riga di codice sorgente**|Numero di riga iniziale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Fine della riga di codice sorgente**|Numero di riga finale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Inizio origine del carattere**|Offset del carattere iniziale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Fine origine del carattere**|Offset del carattere finale nel file di origine in corrispondenza del quale viene raccolto questo esempio.|  
|**Nome riga**|Identificatore generato dal profiler della riga con la sintassi seguente:`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number End`**,**`Character End`**\]**|  
|**Exclusive Samples**|Numero totale dei campioni raccolti durante l'esecuzione della riga di funzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che sono stati raccolti durante l'esecuzione di questa riga di funzione.|  
  
## Vedere anche  
 [Visualizzazione Righe \- Campionamento](../profiling/lines-view-dotnet-memory-sampling-data.md)