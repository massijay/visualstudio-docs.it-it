---
title: "Visualizzazione Funzioni: dati di campionamento del profiler | Microsoft Docs"
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
  - "profilatura del campionamento (metodo), visualizzazione Funzioni"
  - "Funzioni (visualizzazione)"
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Funzioni: dati di campionamento del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione rapporto Funzioni per il metodo di profilo campione sono elencate le funzioni che sono state campionate durante l'esecuzione del profilo.  
  
> [!NOTE]
>  Le funzionalità di sicurezza avanzate in Windows 8 e Windows Server 2012 necessarie modifiche significative in modo che il profiler di Visual Studio consente di raccogliere dati su queste piattaforme.  Le applicazioni di archivio di Windows richiedono nuove tecniche di raccolta.  Vedere [Profilatura delle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|**ID processo**|ID di processo dell'esecuzione della profilatura.|  
|**Nome di processo**|Nome del processo.|  
|**Module Name**|Nome del modulo che contiene la funzione.|  
|**Percorso modulo**|Percorso del modulo che contiene la funzione.|  
|**File di origine**|File di origine che contiene la definizione per questa funzione.|  
|**Function Name**|Nome completo della funzione.|  
|**Numero riga funzione**|Numero di riga dell'inizio di questa funzione nel file di origine.|  
|**Function Address**|Indirizzo della funzione.|  
|**Inclusive Samples**|Numero totale di campioni raccolti durante l'esecuzione di questa funzione, ovvero il numero di campioni raccolti quando questa funzione si trovava nello stack di chiamate.  Sono inclusi i campioni raccolti durante l'esecuzione delle funzioni chiamate da questa funzione.|  
|**% campioni inclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che costituivano campioni inclusivi di questa funzione.|  
|**Exclusive Samples**|Numero totale di campioni raccolti durante l'esecuzione del codice nel corpo di questa funzione, ovvero quando questa funzione si trovava nella parte alta dello stack di chiamate.  Non sono inclusi i campioni raccolti nelle funzioni chiamate da questa funzione.|  
|**% campioni esclusivi**|Percentuale di tutti i campioni nell'esecuzione del profilo che costituivano campioni esclusivi di questa funzione.|  
  
## Vedere anche  
 [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md)   
 [Visualizzazione Funzioni \- Strumentazione](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Funzioni \- Campionamento](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Funzioni](../profiling/functions-view-instrumentation-data.md)