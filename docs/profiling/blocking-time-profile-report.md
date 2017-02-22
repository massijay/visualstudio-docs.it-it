---
title: "Report del profilo di durata del blocco | Microsoft Docs"
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
  - "vs.cv.threads.report.blocking"
helpviewer_keywords: 
  - "Visualizzatore di concorrenza, report del profilo di durata del blocco"
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Report del profilo di durata del blocco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I rapporti di profilo forniscono dati relativi al tempo di blocco di aggregazione per gli stack di chiamate specifici di ogni categoria di blocco \(ad esempio "I\/O" o "Sincronizzazione"\).  Il rapporto di precedenza elenca i processi che hanno avuto precedenza al processo corrente assieme al numero di istanze di precedenza.  Per compilare il rapporto del profilo di blocco, lo strumento raccoglie chiamate API di blocco e le accumula in una struttura ad albero di stack di chiamate.  I dati visualizzati in questi rapporti variano in base all'intervallo di tempo corrente, ai thread nascosti e ai due filtri seguenti che è possibile applicare:  
  
-   Se viene selezionato Just My Code, vengono presentati solo gli stack frame che dispongono di un codice utente, oltre a un livello al di sotto del codice utente.  
  
-   Se viene impostato il valore Riduzione rumore, vengono ignorati gli stack fascicolati con una frequenza minore rispetto a quella specificata.  
  
 Espandere qualsiasi voce della struttura ad albero delle chiamate per individuare la riga di codice in cui viene impiegato il tempo di blocco.  Per individuare la riga di codice sorgente per una voce, nel menu di scelta rapida, scegliere **Visualizza Sorgente**.  Per identificare la riga di codice che ha chiamato quella corrente, nel menu di scelta rapida, scegliere **Visualizza siti di chiamata**.  Se è disponibile un solo sito di chiamata, il comando si connetterà direttamente sulla riga di codice evidenziata per il sito di chiamata.  Se sono disponibili più siti di chiamata, il comando apre una finestra di dialogo in cui è possibile selezionare una voce e quindi scegliere il pulsante **Vai all'origine** per individuare il sito di chiamata evidenziato.  È spesso molto utile visualizzare il codice sorgente per il sito di chiamata con il maggior numero di istanze, i tempi più lunghi o entrambi.  
  
## Colonne del rapporto del tempo di blocco  
 Nella tabella seguente sono illustrate le colonne di ogni rapporto del tempo di blocco.  
  
|Nome colonna|Descrizione|  
|------------------|-----------------|  
|Nome|Il nome della funzione per ogni livello dello stack di chiamate.|  
|Istanze|Il numero di istanze della chiamata di blocco per il periodo di tempo visibile.|  
|Durata blocco inclusiva|Tempo di blocco totale impiegato per tutti gli stack che riportano a questo livello della struttura ad albero dello stack di chiamate.  Il numero inclusivo è la somma della durata di blocco esclusiva per questa funzione e della durata di blocco esclusiva per tutti i relativi nodi figlio.|  
|Durata blocco esclusiva|La durata totale del blocco durante la quale questa funzione si trova al livello inferiore dello stack di chiamate.  Una voce univoca dello stack di chiamate con un elevato tempo esclusivo di blocco può essere una funzione di interesse.|  
|Categoria API\/attesa|Visualizzata solo per le funzioni al livello inferiore dello stack di chiamate.  Laddove venga riconosciuta la firma della chiamata di blocco, viene fornito il nome dell'API di blocco.  Se la firma non viene riconosciuta, vengono fornite le informazioni riportate dal kernel.|  
|Dettagli|Nome completo della funzione.  Include il conteggio di righe, se disponibile.|  
  
### Sincronizzazione  
 Il rapporto di sincronizzazione mostra le chiamate responsabili di segmenti che bloccano la sincronizzazione, oltre ai tempi di blocco di aggregazione di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di sincronizzazione](../profiling/synchronization-time.md).  
  
### Sleep  
 Il rapporto di sospensione mostra le chiamate responsabili del tempo di blocco attribuito al tempo impiegato per la sospensione, oltre ai tempi di blocco di aggregazione di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Durata della sospensione](../profiling/sleep-time.md).  
  
### I\/O  
 Il rapporto di I\/O mostra le chiamate responsabili di segmenti che bloccano le operazioni di I\/O, oltre ai tempi di blocco di aggregazione di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di I\/O \(visualizzazione Thread\)](../profiling/i-o-time-threads-view.md).  
  
### Gestione della memoria  
 Il rapporto di gestione della memoria mostra le chiamate responsabili dei segmenti che bloccano le operazioni di gestione della memoria, oltre ai tempi di blocco di aggregazione di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di gestione della memoria](../profiling/memory-management-time.md).  
  
### Priorità  
 Il rapporto di precedenza elenca i processi che hanno avuto precedenza al processo corrente assieme al numero di istanze.  È possibile espandere ciascun processo per visualizzare i thread specifici che hanno sostituito i thread nel processo corrente e visualizzare la suddivisione delle istanze di precedenza per thread.  Questo rapporto di blocco è meno utilizzabile di altri perché la precedenza viene in genere imposta al processo dal sistema operativo, non da un problema nel codice.  Per ulteriori informazioni, vedere [Tempo di annullamento](../profiling/preemption-time.md).  
  
### Elaborazione interfaccia utente  
 Il rapporto di elaborazione interfaccia utente mostra le chiamate responsabili dei segmenti che bloccano i blocchi di elaborazione interfaccia utente e i tempi di blocco aggregati di ogni stack di chiamate.  Per ulteriori informazioni, vedere [Tempo di elaborazione dell'interfaccia utente](../profiling/ui-processing-time.md).  
  
## Vedere anche  
 [Visualizzazione Thread](../profiling/threads-view-parallel-performance.md)