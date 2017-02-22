---
title: "Visualizzazione Processo | Microsoft Docs"
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
  - "vs.performance.view.process"
helpviewer_keywords: 
  - "strumenti di prestazioni (rapporti), visualizzazione processo"
  - "strumenti di prestazioni, visualizzazione processo"
  - "Processo (visualizzazione)"
  - "strumenti di profilatura, rapporto dei processi"
  - "strumenti di profilatura, visualizzazione processo"
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Processo vengono presentati i dati di profilatura per i processi e i thread eseguiti durante la profilatura.  
  
 I processi vengono elencati per nome.  I thread vengono elencati come nodi figlio del processo che li ha creati.  I thread vengono specificati in base alla funzione che li ha avviati o all'etichetta **\[ntdll.dll\]** se non è disponibile alcun simbolo.  
  
 Per aggiungere o rimuovere colonne, fare clic con il pulsante destro del mouse nella visualizzazione, quindi scegliere **Aggiungi\/Rimuovi colonne**.  È inoltre possibile ordinare i dati facendo clic sui nomi delle colonne.  Per ulteriori informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).  
  
 Le colonne della visualizzazione Processo sono le stesse per i dati generati con i metodi di campionamento e di strumentazione e per quelli che includono dati di memoria .NET.  I valori della colonna sono descritti nella tabella seguente.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**Unique ID**|Identificatore generato dal profiler univoco per il processo o il thread.|  
|**ID**|Identificatore generato dal sistema per il processo o il thread.|  
|**Nome**|Nome del processo o del thread.|  
|**Ora di inizio**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura all'avvio del processo o del thread.|  
|**Ora di fine**|Numero di millisecondi o di cicli del processore dall'inizio della profilatura alla fine del processo o del thread.|  
  
## Vedere anche  
 [Visualizzazioni dei dati del metodo di campionamento](../profiling/profiler-sampling-method-data-views.md)   
 [Visualizzazioni dei dati del metodo di strumentazione](../profiling/instrumentation-method-data-views.md)   
 [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md)