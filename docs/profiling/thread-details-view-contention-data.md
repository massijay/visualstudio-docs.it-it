---
title: "Visualizzazione Dettagli thread: dati su conflitti del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threaddetails"
helpviewer_keywords: 
  - "Dettagli thread (visualizzazione)"
ms.assetid: 874c3b1c-88d8-479a-bb35-1291d9aa8e67
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Visualizzazione Dettagli thread: dati su conflitti del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nella visualizzazione Dettagli thread è presente un grafico della cronologia degli eventi di blocco nel thread selezionato di un'esecuzione del profilo causato da conflitti di risorse.  Si verifica un evento di blocco quando il thread viene indotto a sospendere l'esecuzione perché un altro thread ha bloccato l'accesso a una risorsa.  
  
 In questa visualizzazione la cronologia di esecuzione del thread è rappresentata come una barra orizzontale, mentre gli eventi di blocco sono rappresentati come una barra verticale su una cronologia orizzontale del thread.  Se necessario, è possibile ingrandire una sezione della cronologia per visualizzare i singoli eventi.  Per visualizzare il percorso di esecuzione delle funzioni che hanno condotto all'evento, fare clic sulla barra dell'evento.  Le funzioni verranno visualizzate nella finestra Stack di chiamate.  Quando è disponibile il codice sorgente per una funzione, è possibile fare clic sul nome della funzione per modificare il file di origine nell'IDE di Visual Studio.  
  
## Navigazione all'interno della cronologia  
  
#### Per applicare lo zoom avanti a un segmento della cronologia  
  
-   Fare clic e trascinare il puntatore del mouse per selezionare un'area della cronologia.  
  
     Quando si rilascia il mouse, il segmento temporale selezionato risulta ingrandito.  È possibile ripetere il processo per ingrandire ulteriormente il segmento.  La casella di scorrimento posta sulla barra di scorrimento del tempo rappresenta le dimensioni relative del segmento temporale visualizzato.  
  
#### Per applicare lo zoom indietro a una cronologia  
  
-   Scegliere **Zoom indietro** per tornare al livello di zoom precedente.  
  
-   Scegliere **Reimposta zoom** per mostrare l'intera cronologia nella visualizzazione.  
  
#### Per visualizzare lo stack di chiamate di un evento  
  
-   Nel grafico della cronologia fare clic sulla barra verticale che rappresenta l'evento.  
  
#### Per visualizzare o modificare il codice sorgente di una funzione nello stack di chiamate  
  
-   Nella finestra Stack di chiamate fare clic sul nome della funzione.  
  
 Il codice sorgente della funzione deve essere parte del progetto corrente.  
  
#### Per visualizzare gli eventi di conflitto di una risorsa in tutti i thread nell'esecuzione del profilo  
  
-   Nel grafico della cronologia fare clic sul nome o sull'ID della risorsa.  
  
     Verrà aperta la [Visualizzazione Dettagli risorsa](../profiling/resource-details-view-contention-data.md) per la risorsa selezionata.  
  
#### Per visualizzare i dati sui conflitti dei thread nella finestra Processi  
  
-   Nel grafico cronologia fare clic su **Totale**.  
  
     Verrà aperta la [Visualizzazione Processo](../profiling/process-view-contention-data.md) con il thread selezionato.