---
title: "Creazione di rapporti di profilatura di base tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Creazione di rapporti di profilatura di base tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono illustrati i comandi VSPerfReport di base che generano rapporti con valori delimitati da virgole \(csv\) da un file dei dati di profilo con estensione vsp o vsps.  Per una descrizione di tutte le opzioni relative ai rapporti, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
## Comandi relativi ai rapporti  
 Utilizzare uno dei comandi seguenti per creare un rapporto per un file dei dati di profilo specificato.  
  
 **VSPerfReport** `VSPFile` **\/Summary:All**  
 Genera tutti i rapporti disponibili per il file vsp o vsps.  
  
 **VSPerfReport** `VSPFile` **\/Summary:**`ReportType`\[,`ReportType`...\]  
 Genera i tipi di rapporto specificati.  
  
 **VSPerfReport** `VSPFile` **\/CallTrace**  
 Genera un rapporto in cui sono elencati gli eventi di raccolta dei dati.  Solo il metodo di strumentazione.  
  
## parametri di tipo di rapporto  
 Nella tabella seguente vengono descritti i rapporti generati dall'opzione del tipo di rapporto specificata.  Le colonne di un rapporto dipendono dal metodo di profilo utilizzato per la raccolta dei dati.  
  
|Parametro|Descrizione del rapporto|Riferimento del rapporto|  
|---------------|------------------------------|------------------------------|  
|**CallerCallee**|Rappresenta le relazioni padre\/figlio tra le funzioni.|-   [Dati di campionamento](../profiling/caller-callee-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/caller-callee-view-contention-data.md)|  
|**Function**|Elenca i dati di profilo per funzione.|-   [Dati di campionamento](../profiling/functions-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/functions-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Rappresenta i percorsi di esecuzione e i dati di profilo di funzioni nell'esecuzione del profilo.|-   [Dati di strumentazione](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Dati di campionamento](../profiling/call-tree-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/call-tree-view-contention-data.md)|  
|**Counter**|Elenca i contrassegni di profilo e i valori del contatore delle prestazioni Windows raccolti durante l'esecuzione del profilo.|-   [Visualizzazione Contrassegni](../profiling/marks-view.md)|  
|**Ip**|Elenca i dati di profilo per istruzione.|-   [Dati di campionamento](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Dati su conflitti](../profiling/instruction-pointers-ips-view-contention-data.md)|  
|**Life**|Elenca la durata degli oggetti allocati.|-   [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md)|  
|**Line**|Elenca i dati di profilo per riga del codice sorgente.|-   [Dati di campionamento](../profiling/lines-view-sampling-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Dati su conflitti](../profiling/lines-view-contention-data.md)|  
|**Header**|Profilo delle informazioni di intestazione del file di dati.|Specifico del file.|  
|**Mark**|Profilo dei contrassegni raccolti nell'esecuzione del profilo.|-   [Visualizzazione Contrassegni](../profiling/marks-view.md)|  
|**Module**|Elenca i dati di profilo per i moduli.|-   [Dati di campionamento](../profiling/modules-view-sampling-data.md)<br />-   [Dati di strumentazione](../profiling/modules-view-instrumentation-data.md)<br />-   [Dati di campionamento di memoria .NET](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [Dati di strumentazione di memoria .NET](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Dati su conflitti](../profiling/modules-view-contention-data.md)|  
|**Process**|Elenca i dati di profilo per i processi.|-   [Visualizzazione Processo](../profiling/process-view.md)<br />-   [Dati su conflitti](../profiling/process-view-contention-data.md)|  
|**Thread**|Elenca i dati di profilo per i thread.|-   [Visualizzazione Processo](../profiling/process-view.md)|  
|**Type**|Elenca i dati di profilo di allocazione per tipo.|-   [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md)|  
|**Contention**|Conflitti di risorse.|-   [Conflitti di risorse](../profiling/resource-contentions-view-contention-data.md)|  
|**RuleWarnings**|Elenca i problemi relativi alle regole di prestazioni.|-   Elenca CheckId, descrizione e percorso del codice sorgente del problema di regola.|  
|**ETW**|Elenca tutti gli eventi Traccia eventi per Windows \(ETW\) raccolti durante l'esecuzione del profilo.|-   [Rapporto ETW](../profiling/event-tracing-for-windows-etw-report.md)|