---
title: "Visualizzazione Dettagli risorsa: dati su conflitti del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.resourcedetails"
helpviewer_keywords: 
  - "Dettagli risorsa (visualizzazione)"
ms.assetid: a4ecfe1c-abbc-4fb3-9ab2-34de50486901
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Visualizzazione Dettagli risorsa: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Dettagli risorsa è contenuto un grafico cronologia degli eventi di blocco causato da conflitti relativi a una risorsa selezionata.  Si verifica un evento di blocco quando un thread viene indotto a sospendere l'esecuzione perché un altro thread ha bloccato l'accesso alla risorsa.  
  
 In questa visualizzazione la cronologia di esecuzione di ciascun thread è rappresentata come una barra orizzontale, mentre ciascun evento di blocco è rappresentato come una barra verticale sulla cronologia del thread.  Se necessario, è possibile ingrandire una sezione della cronologia per visualizzare i singoli eventi.  Per visualizzare il percorso di esecuzione \(stack di chiamate\) delle funzioni che hanno condotto all'evento, fare clic sulla barra dell'evento.  Le funzioni verranno visualizzate nella finestra **Stack di chiamate**.  Quando è disponibile codice sorgente per una funzione, è possibile fare clic sul nome della funzione per modificare il file di origine nell'interfaccia per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Procedure  
  
#### Per ingrandire un segmento della cronologia  
  
-   Trascinare il puntatore del mouse su un'area della cronologia.  
  
     Quando si rilascia il pulsante del mouse, il segmento temporale selezionato risulta ingrandito.  È possibile ripetere il processo per ingrandire ulteriormente il segmento.  La casella di scorrimento posta sulla barra di scorrimento del tempo rappresenta le dimensioni relative del segmento di tempo visualizzato nella visualizzazione.  
  
#### Per applicare lo zoom indietro a una cronologia  
  
-   Effettuare uno dei passaggi riportati di seguito:  
  
    -   Scegliere **Zoom indietro** per tornare al livello di zoom precedente.  
  
    -   Scegliere **Reimposta zoom** per mostrare l'intera cronologia nella visualizzazione.  
  
#### Per visualizzare lo stack di chiamate di un evento  
  
-   Nel grafico cronologia, fare clic sulla barra dell'evento.  
  
#### Per visualizzare o modificare il codice sorgente di una funzione nello stack di chiamate  
  
-   Nella finestra **Stack di chiamate**, fare clic sul nome della funzione.  
  
 Il codice sorgente della funzione deve essere parte del progetto corrente.  
  
#### Per visualizzare la struttura ad albero delle chiamate di eventi di conflitto per la risorsa  
  
-   Nel grafico cronologia fare clic su **Totale**.  
  
     Viene visualizzata la visualizzazione Conflitti per la risorsa.  Per ulteriori informazioni, vedere [Visualizzazione relativa ai conflitti di risorse](../profiling/resource-contentions-view-contention-data.md).  
  
#### Per visualizzare tutti gli eventi di conflitto di un thread  
  
-   Nel grafico cronologia, fare clic sul nome o sull'ID del thread.  
  
     Viene visualizzata la visualizzazione Dettagli thread per il thread selezionato.  Per ulteriori informazioni, vedere [Visualizzazione Dettagli thread](../profiling/thread-details-view-contention-data.md).