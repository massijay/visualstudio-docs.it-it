---
title: "DA0022: Frequenza elevata di Garbage Collection di generazione 2 | Microsoft Docs"
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
  - "vs.performance.DA0022"
  - "vs.performance.rules.DA0022"
  - "vs.performance.22"
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0022: Frequenza elevata di Garbage Collection di generazione 2
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0022|  
|Categoria|Utilizzo di .NET Framework|  
|Metodo di profilatura|Tutto|  
|Messaggio|È stata rilevata una frequenza elevata di Garbage Collection di generazione 2.  In genere, ciò avviene se la maggior parte delle strutture dati del programma sono allocate e rese persistenti per molto tempo per progettazione.  Tuttavia, se tale comportamento è imprevisto, l'applicazione potrebbe bloccare gli oggetti.  Per ulteriori dettagli, è possibile raccogliere dati sull'allocazione di memoria .NET e informazioni sulla durata degli oggetti per comprendere il criterio di allocazione della memoria utilizzata dall'applicazione.|  
|Tipo regola|Avviso|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Causa  
 I dati relativi alle prestazioni di sistema raccolti durante la profilatura indicano che una percentuale significativa della memoria per oggetti .NET Framework è stata recuperata nell'operazione di Garbage Collection di generazione 2 rispetto alle operazioni di Garbage Collection di generazione 0 e generazione 1.  
  
## Descrizione della regola  
 Microsoft .NET Common Language Runtime \(CLR\) fornisce un meccanismo di gestione automatica della memoria che utilizza un Garbage Collector per recuperare memoria da oggetti che non vengono più utilizzati dall'applicazione.  Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata.  Le variabili locali, ad esempio, dovrebbero essere di breve durata.  Gli oggetti appena creati vengono avviati in generazione 0 \(gen 0\), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora utilizzati dall'applicazione.  
  
 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace.  Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace.  Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore.  La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.  
  
 Questa regola viene attivata quando si verificano proporzionalmente troppe operazioni di Garbage Collection di generazione 2.  Le applicazioni per .NET Framework ben progettate disporranno di un numero di operazioni di Garbage Collection di generazione 1 5 volte maggiori rispetto alle raccolte di generazione 2. \(Un fattore 10x è probabilmente è ideale\).  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [Visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura.  Individuare le colonne **Memoria CLR .NET\\Raccolte di generazione 0** e **Memoria CLR .NET\\Raccolte di generazione 1**.  Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'operazione di Garbage Collection si verifica più frequentemente.  Confrontare questi valori con la colonna **Percentuale tempo in GC** per verificare se il modello di allocazioni della memoria gestita sta provocando un eccessivo sovraccarico della gestione della memoria.  
  
 Una percentuale elevata di Garbage Collection di generazione di 2 non è sempre un problema.  Potrebbe essere stato definito in fase di progettazione.  È possibile che questa regola venga attivata da un'applicazione che alloca strutture dei dati di grandi dimensioni che devono rimanere attive per i lunghi periodi durante l'esecuzione.  Quando tale applicazione è in condizioni di pressione della memoria, è possibile che venga imposta l'esecuzione di operazioni di Garbage Collection frequenti.  Se le operazioni di Garbage Collection di generazione 0 e generazione 1 meno costose possono recuperare solo una piccola quantità memoria gestita, verranno pianificate operazioni più frequenti di Garbage Collection di generazione 2.  
  
 Nella visualizzazione Contrassegni sono presenti altre colonne Memoria CLR .NET che possono facilitare l'identificazione dei problemi di Garbage Collection.  La colonna **Percentuale tempo in GC** consente di ottenere informazioni sull'incidenza dell'attuale sovraccarico di gestione della memoria.  Se l'applicazione utilizza in genere un numero abbastanza limitato di oggetti grandi ma persistenti, le raccolte frequenti di generazione 2 non dovranno utilizzare quantità eccessive di tempo CPU.  Se l'applicazione è in condizioni di pressione della memoria perché è richiesta una maggiore quantità di memoria fisica \(RAM\), è possibile che vengano attivate anche regole correlate per la valutazione dei valori della colonna **Memoria\\Pagine\/sec**.  
  
 Per comprendere il modello di utilizzo della memoria gestita dell'applicazione, eseguire di nuovo la profilatura con un profilo di allocazione della memoria .NET e selezionare l'opzione di profilatura della durata degli oggetti.  
  
 Per informazioni su come migliorare le prestazioni di Garbage Collection, vedere [Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni](http://go.microsoft.com/fwlink/?LinkId=148226) sul sito Web Microsoft \(la pagina potrebbe essere in inglese\).  Per informazioni sul sovraccarico della procedura di Garbage Collection automatica, vedere [Heap di grandi oggetti](http://go.microsoft.com/fwlink/?LinkId=177836).