---
title: "Visualizzazione Struttura ad albero delle chiamate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "visualizzazione Struttura ad albero delle chiamate"
  - "rapporti di prestazioni, visualizzazione Struttura ad albero delle chiamate"
  - "rapporti degli strumenti di profilatura, visualizzazione Struttura ad albero delle chiamate"
  - "strumenti di profilatura, visualizzazione Struttura ad albero delle chiamate"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Visualizzazione Struttura ad albero delle chiamate
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La visualizzazione Albero delle chiamate contiene i percorsi di esecuzione della funzione utilizzati nell'applicazione profilata.  La radice della struttura ad albero è il punto di ingresso nell'applicazione o nel componente.  Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati delle prestazioni delle relative chiamate di funzione.  
  
 Nella visualizzazione Albero delle chiamate è possibile anche espandere ed evidenziare il percorso di esecuzione di una funzione che ha impiegato più tempo o che è stata campionata con più frequenza.  Per visualizzare il percorso che più influisce sulle prestazioni, fare clic con il pulsante destro del mouse sulla funzione, quindi scegliere **Espandi percorso critico**.  
  
 Ogni processo nell'esecuzione dell'analisi è visualizzato come un nodo radice.  È possibile impostare il nodo iniziale della visualizzazione Struttura ad albero delle chiamate facendo clic con il pulsante destro del mouse sul nodo che si desidera impostare come nodo iniziale e quindi selezionare **Imposta radice**.  
  
 Quando si imposta il nodo radice, si eliminano dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato.  È possibile reimpostare il nodo radice sul nodo precedentemente visualizzato.  Nella finestra visualizzazione Struttura ad albero delle chiamate, fare clic col pulsante destro del mouse e quindi selezionare **Reimposta radice**.  
  
 La visualizzazione Struttura ad albero delle chiamate può essere personalizzata per aggiungere o rimuovere colonne.  Fare clic col pulsante destro del mouse su **Barra del titolo nome colonna** quindi selezionare **Aggiungi\/Rimuovi colonne**.  
  
 La visualizzazione Struttura ad albero delle chiamate può essere configurata per la riduzione del rumore limitando la quantità di dati presentati.  Utilizzando la riduzione del rumore, i problemi di prestazioni sono più rilevanti nella visualizzazione.  Quando i problemi di prestazioni sono facili da distinguere, l'analisi è più semplice.  Per ulteriori informazioni, vedere [Procedura: Configurare la riduzione del rumore nelle visualizzazioni report](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Se la riduzione del rumore è configurata per visualizzare un avviso quando attivata, una barra informazioni verrà visualizzata nel report.  
  
 Per ulteriori informazioni sulle definizioni per le colonne nella visualizzazione Struttura ad albero delle chiamate, vedere quanto segue:  
  
 [Visualizzazione albero delle chiamate](../profiling/call-tree-view-sampling-data.md)  
  
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Visualizzazione Struttura ad albero delle chiamate \- Campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Visualizzazione Struttura ad albero delle chiamate](../profiling/call-tree-view-contention-data.md)  
  
## Vedere anche  
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)   
 [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)