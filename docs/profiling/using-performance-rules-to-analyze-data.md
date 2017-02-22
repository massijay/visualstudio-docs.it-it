---
title: "Utilizzo delle regole di prestazioni per analizzare i dati di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Utilizzo delle regole di prestazioni per analizzare i dati di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di prestazioni degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] segnalano i problemi che possono rallentare l'esecuzione di un'applicazione profilata.  Gli avvisi possono anche indicare la necessità di modificare i metodi di raccolta per raccogliere dati più utili.  Gli avvisi di prestazioni vengono generati automaticamente in una sessione di profilo.  Gli avvisi vengono visualizzati nella finestra **Elenco errori** quando viene aperto un file di dati di profilo in Visual Studio.  Nella finestra **Elenco errori** è possibile individuare il codice sorgente del problema e visualizzare informazioni dettagliate sull'errore, ad esempio informazioni sulla risoluzione del problema.  È inoltre possibile disabilitare gli avvisi a cui non si è interessati.  
  
> [!NOTE]
>  Gli avvisi di prestazioni del profiler sono generati dall'analisi dinamica dell'esecuzione del programma e sono indipendenti dagli avvisi dell'analisi codice.  L'analisi codice può anche generare avvisi di prestazioni per codice gestito in base all'analisi statica del codice sorgente.  Per ulteriori informazioni, vedere [Analisi della qualità del codice gestito](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) e [Avvisi di prestazioni](../code-quality/performance-warnings.md).  
  
## In questa sezione  
 [Procedura: visualizzare gli avvisi di prestazioni](../profiling/how-to-view-performance-warnings.md)  
 Vengono fornite informazioni sull'apertura della finestra **Elenco errori** per visualizzare gli avvisi di prestazioni del profiler.  
  
 [Procedura: abilitare e disabilitare le regole di prestazioni](../profiling/how-to-configure-performance-rules.md)  
 Vengono fornite informazioni sull'attivazione o sulla disattivazione di singoli avvisi di prestazioni.  
  
 [Tabella di riferimento delle regole di prestazioni](../profiling/performance-rules-reference.md)  
 Vengono fornite informazioni dettagliate sugli avvisi di prestazioni del profiler.