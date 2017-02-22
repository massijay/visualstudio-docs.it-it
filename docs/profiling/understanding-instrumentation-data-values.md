---
title: "Informazioni sui valori dei dati di strumentazione negli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per la profilatura, strumentazione"
  - "metodo di profilatura strumentazione"
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Informazioni sui valori dei dati di strumentazione negli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il metodo di profilatura della *strumentazione* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registra dettagliate informazioni di intervallo per le chiamate di funzioni, le righe e le istruzioni nell'applicazione profilata  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Il metodo di strumentazione inserisce il codice all'inizio e alla fine delle funzioni di destinazione nel file binario profilato e prima e dopo ogni chiamata di tali funzioni ad altre funzioni.  Il codice inserito registra quanto segue:  
  
-   L'intervallo tra questo evento di raccolta e il precedente.  
  
-   L'eventuale esecuzione di un'operazione del sistema operativo durante l'intervallo.  Ad esempio, il sistema operativo potrebbe leggere o scrivere sul disco oppure passare dal thread di destinazione a un altro thread di un altro processo.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Per ogni intervallo, l'analisi del profiler ricostruisce lo stack di chiamate presente alla fine dell'intervallo.  Uno stack di chiamate è l'elenco delle funzioni attive in un processore in un determinato momento.  Solo una funzione \(la funzione corrente\) esegue il codice. Le altre funzioni costituiscono la catena delle chiamate di funzione che hanno causato la chiamata alla funzione corrente \(lo stack di chiamate\).  
  
 Per ogni funzione nello stack di chiamate quando l'intervallo è stato registrato, l'analisi del profiler aggiunge l'intervallo a uno o più dei quattro valori di dati per la funzione.  L'analisi aggiunge l'intervallo a un valore di dati per una funzione sulla base di due criteri:  
  
-   Se l'intervallo si è verificato nel codice della funzione o in una *funzione figlio* \(una funzione chiamata dalla funzione\).  
  
-   Se un evento del sistema operativo si è verificato nell'intervallo.  
  
 I valori di dati per un intervallo di una funzione o un intervallo di dati sono denominati *Inclusivo trascorso*, *Esclusivo trascorso*, *Inclusivo applicazione* ed *Esclusivo applicazione*.  
  
-   Tutti gli intervalli di una funzione vengono aggiunti al valore di dati Inclusivo trascorso.  
  
-   Se l'intervallo si è verificato nel codice della funzione e non in una funzione figlio, l'intervallo viene aggiunto al valore di dati Esclusivo trascorso della funzione.  
  
-   Se un evento del sistema operativo non si è verificato nell'intervallo, l'intervallo viene aggiunto al valore di dati Inclusivo applicazione.  
  
-   Se un evento del sistema operativo non si è verificato nell'intervallo e l'intervallo si è verificato nell'esecuzione diretta del codice della funzione \(ovvero non in una funzione figlio\), l'intervallo viene aggiunto al valore di dati Esclusivo applicazione.  
  
 I rapporti sulla profilatura della strumentazione aggregano i valori totali delle funzioni nella sessione di profilatura stessa e dei processi, thread e binari della sessione.  
  
## Valori Inclusivo trascorso  
 Tempo totale impiegato per eseguire una funzione e le relative funzioni figlio.  
  
 I valori Inclusivo trascorso includono gli intervalli impiegati per eseguire direttamente il codice della funzione e gli intervalli impiegati per eseguire le funzioni figlio della funzione di destinazione.  Nei valori Inclusivo trascorso sono inclusi anche gli intervalli della funzione o delle funzioni figlio che comprendono l'attesa del sistema operativo.  
  
## Valori Esclusivo trascorso  
 Tempo totale impiegato per eseguire una funzione, senza il tempo speso per le funzioni figlio.  
  
 I valori Esclusivo trascorso includono gli intervalli impiegati per eseguire direttamente il codice della funzione, indipendentemente dal verificarsi o meno di un evento del sistema operativo nell'intervallo.  Tutti gli intervalli spesi nelle funzioni figlio chiamate dalla funzione di destinazione non sono inclusi nei valori Esclusivo trascorso.  
  
## Valori Inclusivo applicazione  
 Tempo impiegato per eseguire una funzione e le relative funzioni figlio, senza il tempo speso per gli eventi del sistema operativo.  
  
 I valori Inclusivo applicazione non includono gli intervalli contenenti eventi del sistema operativo.  I valori Inclusivo applicazione includono tutti gli altri intervalli impiegati per eseguire una funzione, senza considerare se l'intervallo è stato impiegato per eseguire direttamente il codice della funzione o per le funzioni figlio della funzione di destinazione.  
  
## Valori Esclusivo applicazione  
 Tempo impiegato per eseguire una funzione, senza il tempo impiegato per le funzioni figlio e per gli eventi del sistema operativo.  
  
 I valori Esclusivo applicazione non includono gli intervalli contenenti gli eventi del sistema operativo o gli intervalli impiegati per l'esecuzione delle funzioni chiamate dalla funzione.  I valori Esclusivo applicazione includono solo gli intervalli impiegati per eseguire direttamente il codice della funzione e che non contengono eventi del sistema operativo.  
  
## Percentuale Inclusivo trascorso  
 Percentuale dei valori totali Inclusivo trascorso della sessione di profilatura che costituiscono i valori Inclusivo trascorso della funzione, del modulo, del thread o del processo.  
  
 100 \* Inclusivo trascorso funzione \/ Inclusivo trascorso sessione  
  
## Percentuale Esclusivo trascorso  
 Percentuale dei valori totali Inclusivo trascorso della sessione di profilatura che costituiscono i valori Esclusivo trascorso della funzione, del modulo, del thread o del processo.  
  
 100 \* Funzione Esclusivo trascorso \/ Sessione Inclusivo trascorso  
  
## Percentuale Inclusivo applicazione  
 Percentuale dei valori totali Inclusivo applicazione della sessione di profilatura che costituiscono i valori Inclusivo applicazione della funzione, del modulo, del thread o del processo.  
  
 100 \* Funzione Inclusivo applicazione \/ Sessione Inclusivo applicazione  
  
## Percentuale Esclusivo applicazione  
 Percentuale dei valori totali Inclusivo applicazione della sessione di profilatura che costituiscono i valori Esclusivo applicazione della funzione, del modulo, del thread o del processo.  
  
 100 \* Funzione Esclusivo applicazione \/ Sessione Inclusivo applicazione  
  
## Vedere anche  
 [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md)   
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)