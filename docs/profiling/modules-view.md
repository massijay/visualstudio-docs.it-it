---
title: "Visualizzazione Moduli | Microsoft Docs"
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
  - "vs.performance.view.modules"
helpviewer_keywords: 
  - "visualizzazione Moduli"
  - "rapporti degli strumenti di profilatura, visualizzazione Moduli"
  - "strumenti di profilatura, visualizzazione Moduli"
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Visualizzazione Moduli
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Moduli contiene l'elenco dei moduli dei dati di profilatura.  Ogni modulo è il nodo radice di una struttura ad albero gerarchica.  Le funzioni profilate del modulo vengono elencate sotto il nodo del modulo.  Se i dati di profilatura sono stati raccolti tramite il metodo di campionamento, le informazioni sulle righe sono elencate al di sotto del nodo della funzione, mentre i dati del puntatore alle istruzioni sono elencati al di sotto del nodo della riga.  
  
 Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo.  
  
 Per aggiungere o rimuovere colonne, fare clic con il pulsante destro del mouse nella finestra del rapporto, quindi scegliere **Aggiungi\/Rimuovi colonne**.  Per ordinare i dati è possibile fare clic sul nome di una colonna.  Per ulteriori informazioni, vedere [Procedura: Personalizzare colonne della visualizzazione report](../profiling/how-to-customize-report-view-columns.md).  
  
 Le colonne disponibili nella visualizzazione Moduli dipendono dal metodo di profilatura \(campionamento o strumentazione\) utilizzato per raccogliere i dati e dalla raccolta o meno di dati di memoria .NET durante l'esecuzione della profilatura.  
  
## Vedere anche  
 [Visualizzazione Moduli](../profiling/modules-view-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-instrumentation-data.md)   
 [Visualizzazione Moduli \- Strumentazione](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Visualizzazione Moduli \- Campionamento](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Visualizzazione Moduli](../profiling/modules-view-contention-data.md)