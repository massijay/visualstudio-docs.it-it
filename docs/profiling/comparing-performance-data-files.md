---
title: "Confronto di file di dati degli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, confronto dei file di report"
  - "report degli strumenti per la profilatura, confronto"
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Confronto di file di dati degli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzionalità di confronto dei file di dati degli strumenti di profilatura consente di selezionare due file di rapporto \(con estensione vsp o vsps\) e di generare un rapporto indicante le differenze, le regressioni relative alle prestazioni e i miglioramenti riscontrati da una sessione di profilatura all'altra.  
  
 Un rapporto di confronto dei file di dati degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] confronta i risultati di un'analisi in un file di dati di profilatura con i risultati di un'analisi di base in un altro file di dati.  Entrambi file di dati devono essere stati generati tramite lo stesso metodo di profilatura.  Il report relativo all’analisi dei confronti viene salvato come file .vsps.  
  
 Nella visualizzazione del rapporto di confronto è inclusa una visualizzazione tabella dei dati modificati.  La tabella visualizza il delta o modifiche dalla linea di base.  Il delta viene calcolato determinando la differenza tra il valore precedente, il valore di base e il valore risultante dalla nuova analisi.  
  
 I confronti di dati del profiler possono essere basati sulle funzioni nel codice, moduli nell'applicazione, righe, puntatori all'istruzione \(IP\) e tipi.  
  
 I dati di analisi disponibili per il confronto contengono le informazioni visualizzate nelle colonne.  Per le definizioni di questi nomi delle colonne, vedere [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md).  
  
 È possibile impostare una soglia per ridurre il rumore ed escludere dalla visualizzazione tabella di confronto i dati delle righe non modificate in base a una quantità specificata.  
  
## In questa sezione  
 [Procedura: confrontare i file di dati del profiler](../profiling/how-to-compare-performance-data-files.md)