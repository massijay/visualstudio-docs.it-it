---
title: "DA0018: Applicazione a 32 bit in esecuzione al limite di memoria gestito dal processo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.18"
  - "vs.performance.DA0018"
  - "vs.performance.rules.DA0018"
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0018: Applicazione a 32 bit in esecuzione al limite di memoria gestito dal processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0018|  
|Categoria|Utilizzo di strumenti di profilatura|  
|Metodo di profilatura|Campionamento|  
|Messaggio|Le allocazioni di memoria gestita hanno quasi raggiunto il limite predefinito per un processo a 32 bit.  L'applicazione potrebbe essere associata alla memoria.|  
|Tipo regola|Avviso|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Causa  
 I dati di sistema raccolti durante l'esecuzione della profilatura indicano che gli heap di memoria di .NET Framework hanno quasi raggiunto la dimensione massima consentita per gli heap gestiti in un processo a 32 bit.  Questa dimensione massima è un valore predefinito.  Si basa sulla quantità totale di spazio degli indirizzi del processo che può essere allocata per i byte privati.  Il valore indicato è il massimo valore degli heap osservato durante l'attività del processo profilato.  Considerare la possibilità di eseguire di nuovo la profilatura utilizzando il metodo di profilatura della memoria di .NET e ottimizzare l'utilizzo delle risorse gestite dall'applicazione.  
  
 Quando la dimensione degli heap gestiti si avvicina al limite predefinito, potrebbe essere necessario richiamare più frequentemente il processo di Garbage Collection automatico.  In questo modo viene aumentato il sovraccarico di gestione della memoria.  
  
 La regola viene attivata solo per applicazioni a 32 bit in esecuzione su computer a 32 bit.  
  
## Descrizione della regola  
 Microsoft .NET Common Language Runtime \(CLR\) fornisce un meccanismo di gestione automatica della memoria che utilizza un Garbage Collector per recuperare memoria da oggetti che non vengono più utilizzati dall'applicazione.  Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata.  Le variabili locali, ad esempio, dovrebbero essere di breve durata.  Gli oggetti appena creati vengono avviati in generazione 0 \(gen 0\), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora utilizzati dall'applicazione.  
  
 Oggetti gestiti maggiori di 85 KB vengono allocati nell'heap degli oggetti, in cui sono soggetti a Garbage Collection e a compressione meno frequenti che oggetti più piccoli. Gli oggetti grandi vengono gestiti separatamente perché si presuppone che siano più persistenti e perché la combinazione di oggetti grandi e persistenti con oggetti più piccoli allocati frequentemente potrebbe produrre un'indesiderata frammentazione dell'heap.  
  
 Quando la dimensione totale degli heap gestiti si avvicina al limite predefinito, il sovraccarico di gestione della memoria aumenta di solito a un punto tale che potrebbe iniziare ad avere un impatto sulla capacità di risposta e sulla scalabilità dell'applicazione.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md).  Individuare le colonne **Memoria CLR .NET\\Byte in tutti gli heap** e **Totale byte di cui è stato eseguito il commit**.  Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'allocazione di memoria gestita è maggiore rispetto ad altre fasi.  Confrontare i valori della colonna **Byte in tutti gli heap** con la frequenza di Garbage Collection indicata nelle colonne **Memoria CLR .NET\\Raccolte di generazione 0**, **Memoria CLR .NET\\Raccolte di generazione 1** e **Memoria CLR .NET\\Raccolte di generazione 2** per determinare se il modello di allocazioni di memoria gestita incide sulla frequenza di Garbage Collection.  
  
 In un'applicazione per .NET Framework, Common Language Runtime limita la dimensione totale degli heap gestiti a un valore leggermente inferiore a metà della dimensione massima della parte di area privata di uno spazio degli indirizzi del processo.  Per i processi a 32 bit in esecuzione su un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB.  Quando la dimensione totale degli heap gestiti si avvicina al limite predefinito, il sovraccarico di gestione della memoria può aumentare e le prestazioni dell'applicazione possono diminuire.  
  
 Se l'eccessivo sovraccarico della memoria gestita costituisce un problema, considerare una delle seguenti opzioni:  
  
-   ottimizzazione dell'utilizzo delle risorse di memoria gestita da parte dell'applicazione  
  
     \- oppure \-  
  
-   esecuzione di procedure per limitare i vincoli architettonici alla dimensione massima della memoria virtuale per un processo a 32 bit  
  
 Per ottimizzare l'utilizzo delle risorse di memoria gestita da parte dell'applicazione, raccogliere i dati di allocazione della memoria gestita con un'esecuzione della profilatura dell'allocazione di memoria di .NET.  Rivedere i rapporti [Visualizzazioni dei dati di memoria .NET](../profiling/dotnet-memory-data-views.md) per comprendere il modello di allocazione di memoria dell'applicazione.  
  
 Utilizzare [Visualizzazione Durata oggetti](../profiling/object-lifetime-view.md) per determinare quali oggetti dati del programma vengono conservati nella generazione e e ne verranno quindi recuperati.  
  
 Utilizzare [Visualizzazione Allocazioni](../profiling/dotnet-memory-allocations-view.md) per determinare il percorso di esecuzione che ha comportato queste allocazioni.  
  
 Per ulteriori informazioni su come migliorare le prestazioni di Garbage Collection, vedere l'articolo tecnico su .NET Framework, [Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni](http://go.microsoft.com/fwlink/?LinkId=177946) sul sito web MSDN \(la pagina potrebbe essere in inglese\).  
  
 Per limitare i vincoli della memoria virtuale sull'architettura alla dimensione della parte privata di uno spazio degli indirizzi del processo, provare a eseguire questo processo a 32 bit su un computer a 64 bit.  Un processo a 32 bit su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.  
  
 Un processo a 64 bit eseguito su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.  Considerare la possibilità di compilare di nuovo l'applicazione in modo che venga eseguita come un'applicazione di 64 bit nativa.  Questa regola è solo a scopo informativo e potrebbe non richiedere azione correttiva.