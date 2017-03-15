---
title: "DA0005: Raccolte GC2 frequenti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0005"
  - "vs.performance.rules.DAManyGC2Collections"
  - "vs.performance.5"
  - "vs.performance.rules.DA0005"
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0005: Raccolte GC2 frequenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|RuleId|DA0005|  
|Categoria|Utilizzo di .NET Framework|  
|Metodo di profilatura|Memoria .NET|  
|Messaggio|Molti oggetti vengono raccolti tramite Garbage Collection di generazione 2.|  
|Tipo messaggio|Avviso|  
  
## Causa  
 Un numero elevato di oggetti di memoria .NET viene recuperato in un'operazione di Garbage Collection di generazione 2.  
  
## Descrizione della regola  
 Microsoft .NET Common Language Runtime \(CLR\) fornisce un meccanismo di gestione automatica della memoria che utilizza un Garbage Collector per recuperare memoria da oggetti che l'applicazione non utilizza più.  Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata.  Le variabili locali, ad esempio, dovrebbero essere di breve durata.  Gli oggetti appena creati vengono avviati in generazione 0 \(gen 0\), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora utilizzati dall'applicazione.  
  
 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace.  Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace.  Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore.  La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.  
  
 Questa regola viene attivata quando si sono verificate proporzionalmente troppe operazioni di Garbage Collection di generazione 2.  Se un numero eccessivo di oggetti di durata relativamente breve sopravvive alla Garbage Collection generazione 1 e tuttavia può essere successivamente raccolto in una Garbage Collection generazione 2 completa, spesso il costo di gestione della memoria può diventare eccessivo.  Per ulteriori informazioni, vedere [Crisi di mezza età](http://go.microsoft.com/fwlink/?LinkId=177835) il post sulle prestazioni Tidbits di Rico Mariani sul sito Web MSDN.  
  
## Come esaminare un avviso  
 Rivedere i rapporti [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md) per comprendere il modello di allocazione di memoria dell'applicazione.  Utilizzare [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md) per determinare quali oggetti dati del programma sopravvivono fino alla generazione 2 e quindi ne vengono recuperati.  Utilizzare [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md) per determinare il percorso di esecuzione che ha comportato queste allocazioni.  
  
 Per informazioni su come migliorare le prestazioni di Garbage Collection, vedere [Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni](http://go.microsoft.com/fwlink/?LinkId=148226) sul sito Web Microsoft \(la pagina potrebbe essere in inglese\).  Per informazioni sul sovraccarico della procedura di Garbage Collection automatica, vedere [Heap di grandi oggetti](http://go.microsoft.com/fwlink/?LinkId=177836).