---
title: "Tabella di riferimento delle regole di prestazioni degli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Tabella di riferimento delle regole di prestazioni degli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le regole delle prestazioni degli strumenti di profilatura forniscono informazioni e avvisi aggiuntivi sulle prestazioni dell'applicazione.  Le regole delle prestazioni analizzano i dati di un'esecuzione di profilatura raccolti da origini quali i contatori delle prestazioni del processore e di Windows.  I messaggi delle regole vengono visualizzate nella finestra Output errore dell'ambiente di sviluppo integrato di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  I messaggi vengono elencati con uno dei livelli di regole seguenti:  
  
|||  
|-|-|  
|**delle modifiche a..."**|Poche regole generano messaggi di errore poiché la maggior parte dei problemi di prestazioni non sono effettivamente errori.  Un messaggio di errore può indicare un errore nella raccolta dei dati di profilatura.|  
|**Avviso**|Gli avvisi indicano un'area dell'applicazione che può potenzialmente dare origine a problemi di prestazioni o che può essere ottimizzata.|  
|**Informazioni**|I messaggi di informazioni indicano che l'analisi di una condizione della regola non ha raggiunto la soglia per generare un messaggio di errore o che le informazioni nel messaggio sono utili, ma non riflettono un problema di prestazioni.|  
  
## In questa sezione  
 [Regole di prestazioni in base all'ID](../profiling/performance-rules-by-id.md)  
  
 Le regole di prestazioni degli strumenti di profilatura sono organizzate in quattro categorie:  
  
|||  
|-|-|  
|[Regole di prestazioni per l'utilizzo di .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Regole che permettono di utilizzare .NET Framework in modo efficiente.|  
|[Regole di prestazioni relative a memoria e paging](../profiling/memory-and-paging-performance-rules.md)|Regole che analizzano la memoria gestita e il comportamento di paging dell'applicazione.|  
|[Regole di utilizzo degli strumenti di profilatura](../profiling/profiling-tools-usage-rules.md)|Regole che permettono di utilizzare gli strumenti di profilatura in modo efficiente.|  
|[Regole di prestazioni relative al monitoraggio delle risorse](../profiling/resource-monitoring-performance-rules.md)|Messaggi di informazioni sull'utilizzo del processore e della memoria in un'esecuzione di profilatura.|