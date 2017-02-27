---
title: "Visualizzazione Chiamante/chiamato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "strumenti per la profilatura, visualizzazione Chiamante/Chiamato (report)"
  - "strumenti per la profilatura, visualizzazione Chiamante/chiamato"
  - "report di prestazioni, visualizzazione Chiamante/Chiamato"
  - "visualizzazione Chiamante/Chiamato"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Visualizzazione Chiamante/chiamato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Chiamante\/chiamato consente di visualizzare informazioni relative alla profilatura per una funzione selezionata e per le relative funzioni figlio.  La visualizzazione Chiamante\/chiamato contiene tre griglie:  
  
 **Funzione corrente** viene visualizzato nella griglia al centro e include le informazioni di profilatura per la funzione selezionata.  I valori includono tutte le chiamate alla funzione raccolte durante l'esecuzione della profilatura.  
  
 **Funzioni che hanno chiamato la funzione corrente** viene visualizzato nella griglia superiore e include il numero dei valori della funzione selezionata \(corrente\) generati dalle chiamate dalla funzione chiamante \(padre\).  
  
 **Funzioni che sono state chiamate dalla funzione corrente** viene visualizzato nella griglia inferiore e include le informazioni di profilatura per le funzioni chiamate \(figlio\) della funzione selezionata quando la funzione figlio è stata chiamata dalla funzione corrente.  
  
 Le colonne disponibili nella visualizzazione Chiamante\/chiamato dipendono dal metodo di profilatura \(campionamento o strumentazione\) utilizzato per raccogliere i dati e dalla raccolta o meno di dati di memoria .NET durante l'esecuzione della profilatura.  
  
 È possibile selezionare una funzione diversa come Funzione corrente nella parte centrale della visualizzazione Rapporto facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione.  La visualizzazione Rapporto verrà aggiornata automaticamente in base alle modifiche.  
  
 Per ordinare i dati, è possibile fare clic sui nomi delle colonne.  È possibile aggiungere altre colonne alla visualizzazione Chiamante\/chiamato.  Per ulteriori informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).  
  
## Vedere anche  
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-instrumentation-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Strumentazione](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Visualizzazione Chiamante\/chiamato \- Campionamento](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Chiamante\/chiamato](../profiling/caller-callee-view-contention-data.md)