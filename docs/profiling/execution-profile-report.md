---
title: "Report del profilo di esecuzione | Microsoft Docs"
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
  - "vs.cv.threads.report.execution"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, report del profilo di esecuzione"
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Report del profilo di esecuzione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il rapporto del profilo di esecuzione rappresenta un profilo di campionamento convenzionale.  I campioni vengono acquisiti ogni millisecondo durante i periodi in cui un thread è in esecuzione su un core logico e lo strumento di visualizzazione della concorrenza compila una struttura ad albero delle chiamate tipica confrontando il set accumulato di stack di campionamento.  I dati in questa tabella possono essere influenzati dall'intervallo di tempo corrente, dai thread nascosti e dai filtri eventualmente applicati:  
  
-   Se è selezionato Just My Code, vengono presentati solo gli stack frame che dispongono di codice utente, oltre a un livello al di sotto del codice utente.  
  
-   Se viene impostato il valore di Riduzione rumore, gli stack confrontati la cui frequenza è inferiore a quella specificata vengono esclusi dal rapporto.  
  
 Nella tabella seguente sono illustrate le colonne nel rapporto.  
  
|Colonna|Descrizione|  
|-------------|-----------------|  
|Nome|Il nome della funzione per ogni livello dello stack di chiamate.|  
|Campioni inclusivi|Numero totale di campioni raccolti per tutti gli stack accumulati nel livello della struttura ad albero dello stack di chiamate stesso.  Il numero inclusivo è la somma dei campioni esclusivi relativi alla funzione e dei contatori inclusivi relativi a tutti i nodi figlio.|  
|Exclusive Samples|Numero totale di campioni confrontati per i quali la funzione si trova al livello più basso dello stack di chiamate.|  
|% inclusivi|La percentuale di campioni totali mostrata nella colonna dei campioni inclusivi.  Le percentuali sono arrotondate a due posizioni decimali.|  
|% esclusivi|La percentuale di campioni totali mostrata nella colonna dei campioni esclusivi.  Le percentuali sono arrotondate a due posizioni decimali.|  
|Dettagli|Nome completo della funzione.  Include il conteggio di righe, se disponibile.|  
  
 È possibile visualizzare questa tabella del rapporto nella visualizzazione [Tempo di esecuzione \(Visualizzazione thread\)](../profiling/execution-time-threads-view.md).  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)