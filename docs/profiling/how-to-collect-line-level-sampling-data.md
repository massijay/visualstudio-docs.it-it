---
title: "Procedura: Raccogliere i dati di campionamento a livello di riga | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, campionamento a livello di riga"
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Raccogliere i dati di campionamento a livello di riga
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il campionamento a livello di riga è la capacità del profiler di determinare il punto del codice di una funzione che richiede un utilizzo intensivo del processore, ad esempio una funzione con esempi esclusivi elevati, in cui il processore impiega la maggior parte del tempo.  
  
## Panoramica  
 Nel campionamento a livello di riga, il profiler verifica il percorso chiamate nello stack di chiamate del programma a intervalli impostati e aggrega i risultati.  Tali risultati mostrano le istruzioni che il processore stava eseguendo quando i campioni sono stati prelevati.  I dati raccolti sui campioni esclusivi vengono analizzati per identificare le righe del codice e il puntatore all'istruzione \(IP\).  
  
 Il campionamento a livello di riga può essere utilizzato per il codice gestito così come per quello nativo.  I report di prestazioni che visualizzano questi dati includono la visualizzazione Righe e la visualizzazione Moduli.  
  
 Le informazioni inizio\/fine carattere non sono disponibili per il codice nativo.  Per le istruzioni su più righe, per il codice nativo non sono disponibili le informazioni di inizio riga, ma solo quelle di fine riga.  
  
### Dati disponibili  
 I dati del campionamento a livello di riga disponibili includono le seguenti informazioni:  
  
-   Nome funzione.  
  
-   Indirizzo funzione.  
  
-   Inizio riga \- numero di riga del codice di campionamento.  
  
-   Fine riga \- numero di riga di terminazione del codice sorgente.  Generalmente corrisponde al valore di "Inizio riga" ad eccezione di quando una singola istruzione del programma si estende in più righe del codice sorgente.  
  
-   Inizio carattere – colonna iniziale dell'esempio di aggregazione.  Generalmente questo valore è 0 ad eccezione di quando una singola riga contiene più istruzioni del programma.  
  
-   Fine carattere – colonna di terminazione dell'esempio di aggregazione.  
  
-   IP – indirizzo in cui è stato prelevato l'esempio di aggregazione \(solo visualizzazione IP\).  
  
 Nella visualizzazione **Moduli**, se una funzione presenta statistiche a livello di riga, le statistiche vengono annidate in ogni funzione.  Vengono inoltre visualizzate le statistiche a livello di IP annidate in ogni riga.  
  
### Disattivazione del campionamento a livello di riga per il codice gestito  
 Per impostazione predefinita, il campionamento a livello di riga è attivato.  È possibile disattivare la raccolta di dati a livello di riga per il codice gestito in uno dei seguenti modi:  
  
-   Prima di profilare, digitare VSPerfCLREnv \/samplelineoff  Questa operazione ha effetto sulle applicazioni e sui servizi.  
  
     oppure  
  
-   Quando si avvia un'applicazione, digitare SPerfCmd \/lineoff \<altri argomenti\>.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Analisi dei dati degli strumenti per la profilatura](../profiling/analyzing-performance-tools-data.md)