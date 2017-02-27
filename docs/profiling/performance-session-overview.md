---
title: "Panoramica delle sessioni di prestazioni degli strumenti per la profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Strumenti per la profilatura, sessione di prestazioni"
  - "sessioni di prestazioni"
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Panoramica delle sessioni di prestazioni degli strumenti per la profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono spiegate le nozioni di base della profilatura.  Gli sviluppatori non esperti di prestazioni potranno notare come gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] possano contribuire ad accrescere rapidamente la produttività e le prestazioni del codice.  Gli sviluppatori esperti di profilatura possono trovare informazioni su specifici processi e funzionalità degli strumenti di profilatura.  
  
 Gli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contribuiscono a identificare i problemi di prestazioni nel codice sorgente e a confrontare le prestazioni di possibili soluzioni.  Le procedure guidate e le impostazioni predefinite degli strumenti di profilatura consentono di ottenere immediatamente informazioni dettagliate su vari problemi relativi alle prestazioni.  Le funzionalità e le opzioni degli strumenti di profilatura consentono il controllo completo del processo di profilatura.  Questo controllo include la destinazione precisa delle sezioni di codice, la raccolta delle informazioni sui tempi a livello di blocco e l'inclusione nei dati di ulteriori valori delle prestazioni del sistema e del processore.  
  
 I passaggi seguenti costituiscono il processo di base per l'utilizzo di Strumenti di profilatura:  
  
1.  Configurare la sessione di prestazioni specificando il metodo di raccolta e i dati che si desidera raccogliere.  
  
2.  Raccogliere i dati di profilatura eseguendo l'applicazione nella sessione di prestazioni.  
  
3.  Analizzare i dati per identificare il problema di prestazioni.  
  
4.  Modificare il codice nell'ambiente di sviluppo integrato \(IDE\) di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per migliorare le prestazioni del codice per l'applicazione  
  
5.  Raccogliere i dati di profilatura sul codice modificato e confrontare i dati di profilatura originali e modificati.  
  
6.  Generare un report che documenta l'aumento nelle prestazioni.  
  
 Per utilizzare le informazioni fornite dalla profilatura, è necessario disporre delle informazioni sui simboli disponibili per i binari da profilare e per i binari del sistema operativo Windows.  
  
## Configurazione della sessione di prestazioni  
 Per configurare una sessione di prestazioni, selezionare il metodo di profilatura che si desidera usare e i dati che si desidera raccogliere.  La **Creazione guidata sessione di prestazioni** degli strumenti di profilatura guida l'utente durante la configurazione di base e le pagine delle proprietà Sessione prestazioni possono essere utilizzate per aggiungere altre opzioni:  
  
-   I metodi di profilatura includono il campionamento, la traccia e l'allocazione della memoria.  
  
-   I valori dei dati includono l'ora, i contatori delle prestazioni del sistema operativo e del processore e gli eventi dell'applicazione, ad esempio gli errori di pagina e le transizioni del kernel.  
  
 È possibile configurare una sessione di prestazioni in un progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nella soluzione del progetto o profilare i binari arbitrari tramite l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  È possibile specificare le proprietà della sessione nelle pagine delle proprietà Sessione prestazioni o utilizzare la procedura guidata di profilatura.  
  
## Raccolta dei dati di profilatura  
 Si inizia la raccolta dei dati di profilatura in **Esplora prestazioni**.  È possibile sospendere e riprendere la profilatura per limitare la quantità di dati raccolti.  È possibile anche collegarsi a un processo già in esecuzione.  
  
 All'avvio dell'applicazione, viene visualizzata la finestra **Controllo raccolta dati** nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Dalla finestra **Controllo raccolta dati**, è possibile profilare parti specifiche dell'applicazione sospendendo e riprendendo il processo di raccolta.  È possibile utilizzare anche la finestra **Controllo raccolta dati** per inserire contrassegni nei dati raccolti.  I contrassegni sono punti di dati definiti dall'utente visibili nelle visualizzazioni del profilo che possono essere utilizzati per filtrare i dati di profilatura.  
  
 Quando l'applicazione di destinazione viene chiusa, gli strumenti di profilatura generano un file di dati di profilatura \(\*.vsp\) e un rapporto di riepilogo che viene visualizzato nell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Analisi dei dati e identificazione dei problemi di prestazioni  
 Quando si termina l'esecuzione di una profilatura, i dati vengono analizzati e viene visualizzato un riepilogo nelle finestre della visualizzazione **Rapporto di prestazioni** degli strumenti di profilatura.  I dati di profilatura sono raccolti per lo stack di chiamate e le singole funzioni dell'applicazione di destinazione.  Le visualizzazioni del report contengono l'analisi delle prestazioni per gli intervalli di dati dei processi, dei thread, dei moduli, delle funzioni e delle righe del codice sorgente dell'applicazione.  I valori dei dati di profilatura per una funzione includono gli elementi seguenti:  
  
-   Il tempo totale impiegato nella funzione e nelle funzioni figlio chiamate dalla funzione \(valori inclusivi\).  
  
-   Il tempo impiegato per eseguire solo il codice nella funzione \(valori esclusivi\).  
  
 Più di dodici visualizzazioni diverse consentono di analizzare i dati di profilatura nella modalità più efficiente.  Le personalizzazioni della visualizzazione consentono di filtrare e ordinare i dati per trovare le funzioni che potrebbero essere la causa di problemi di prestazioni.  Il filtro del percorso ricorrente fornisce un'evidenziazione immediata dei percorsi più attivi nelle visualizzazioni Albero delle chiamate e Modulo.  
  
## Modifica del codice dell'applicazione  
 Una volta isolati i problemi di prestazioni rilevanti, è possibile modificare il codice tramite l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e raccogliere i dati di profilatura per le modifiche.  
  
## Nuova raccolta dei dati di profilatura e confronto dei dati tra le esecuzioni della profilatura  
 Nella visualizzazione del report di confronto degli strumenti di profilatura viene indicata la differenza delle prestazioni del modulo, della funzione o della riga tra due file di dati di profilatura selezionati.  È possibile specificare i valori dei dati di profilatura da confrontare e passare dalla visualizzazione del confronto e alle visualizzazioni dei singoli file e viceversa.  
  
## Generazione di un report dei risultati  
 È possibile incollare le righe di una visualizzazione del report delle prestazioni in messaggi di posta elettronica e fogli di calcolo e generare report contenenti i dati di una o più visualizzazioni.  
  
## Vedere anche  
 [Cenni preliminari](../profiling/overviews-performance-tools.md)   
 [Procedura dettagliata: Profilatura di applicazioni](../profiling/walkthrough-identifying-performance-problems.md)