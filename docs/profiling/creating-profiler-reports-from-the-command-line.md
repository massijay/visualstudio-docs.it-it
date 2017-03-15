---
title: "Creazione di rapporti del profiler tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Creazione di rapporti del profiler tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento da riga di comando **VSPerfReport** consente di creare rapporti XML o con valori separati da virgole \(con estensione csv\) dai file dei dati di profilo \(con estensione vsp\).  I tipi di rapporto VSPerfReport corrispondono alle visualizzazioni basate su tabella dell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  È possibile filtrare il rapporto per visualizzare solo il proprio codice e un segmento del file di dati di profilatura.  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  
  
 È inoltre possibile semplificare la condivisione di file dei dati di profilo incorporando simboli nei file con estensione vsp e creando file di rapporto pre\-analizzati \(vsps\) più piccoli e più veloci da aprire.  
  
## Attività comuni  
  
|Task|Contenuto correlato|  
|----------|-------------------------|  
|**Creare un rapporto di base.** Creare tutti i tipi di rapporto VSPerfReport o un loro sottoinsieme.|-   [Creazione di rapporti di base](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Confrontare due file dei dati di profilo.** Creare un rapporto "diff" che confronta i dati di prestazioni in due file dei dati di profilo.|-   [Procedura: creare un rapporto di confronto del profiler da un prompt dei comandi](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Visualizzare i dati relativi alla traccia delle chiamate e a Traccia eventi per Windows \(ETW\).** Creare un rapporto di traccia delle chiamate contenente le informazioni di intervallo per ciascun punto di ingresso e di uscita delle funzioni dell'applicazione e ciascuna chiamata ad altre funzioni dalla funzione.  In alternativa creare un elenco dettagliato di tutti gli eventi ETW raccolti in un'esecuzione di profilo.|-   [Procedura: creare un rapporto calltrace](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrare un rapporto.** Limitare un rapporto alle sole funzioni nel codice o a un'ora specifica nel file dei dati di profilo.|-   [Procedura: filtrare rapporti tramite la riga di comando](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Creare file dei dati di profilo portabili.** Per semplificare la condivisione dei dati di profilo, è possibile incorporare i simboli per un'esecuzione del profilo nel file con estensione vsp.  È inoltre possibile creare un file dei dati di profilo preanalizzato con estensione vsps, più piccolo e più veloce da aprire.|-   [Creazione di file di dati di profilatura portabili](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|