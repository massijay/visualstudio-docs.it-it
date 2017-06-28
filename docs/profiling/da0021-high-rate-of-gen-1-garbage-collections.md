---
title: "DA0021: Frequenza elevata di Garbage Collection di generazione 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.21"
  - "vs.performance.DA0021"
  - "vs.performance.rules.DA0021"
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0021: Frequenza elevata di Garbage Collection di generazione 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0021|  
|Categoria|Utilizzo di .NET Framework|  
|Metodi di profilatura|Tutto|  
|Messaggio|È stata rilevata una frequenza elevata di Garbage Collection di generazione 2.  In genere, ciò avviene se la maggior parte delle strutture dati del programma sono allocate e rese persistenti per molto tempo per progettazione.  Tuttavia, se tale comportamento è imprevisto, l'applicazione potrebbe bloccare gli oggetti.  Per ulteriori dettagli, è possibile raccogliere dati sull'allocazione di memoria .NET e informazioni sulla durata degli oggetti per comprendere il criterio di allocazione della memoria utilizzata dall'applicazione.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Causa  
 I dati relativi alle prestazioni di sistema raccolti durante la profilatura indicano che una percentuale significativa della memoria per oggetti .NET Framework è stata recuperata nell'operazione di Garbage Collection di generazione 1 rispetto alla raccolta dei dati di generazione 0.  
  
## Descrizione della regola  
 Microsoft .NET Common Language Runtime \(CLR\) fornisce un meccanismo di gestione automatica della memoria che utilizza un Garbage Collector per recuperare memoria da oggetti che non vengono più utilizzati dall'applicazione.  Il Garbage Collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durata.  Le variabili locali, ad esempio, dovrebbero essere di breve durata.  Gli oggetti appena creati vengono avviati in generazione 0 \(gen 0\), quindi avanzano a generazione 1 se vengono conservati dopo l'esecuzione di un'operazione di Garbage Collection e infine passano a generazione 2 se sono ancora utilizzati dall'applicazione.  
  
 Gli oggetti in generazione 0 vengono raccolti frequentemente e in genere in modo molto efficace.  Gli oggetti in generazione 1 vengono raccolti meno frequentemente e in modo meno efficace.  Infine, gli oggetti di lunga durata in generazione 2 dovrebbero essere raccolti con una frequenza ancora inferiore.  La raccolta in generazione 2, che è l'esecuzione di un'operazione di Garbage Collection completa, è anche l'operazione più costosa.  
  
 Questa regola viene attivata quando si sono verificate proporzionalmente troppe operazioni di Garbage Collection di generazione 1.  Se troppi oggetti di durata relativamente breve vengono conservati dopo una raccolta di generazione 0, ma possono essere raccolti in una generazione 1, il costo di gestione della memoria può diventare eccessivo.  Per ulteriori informazioni, vedere [Crisi di mezza età](http://go.microsoft.com/fwlink/?LinkId=177835) il post sulle prestazioni Tidbits di Rico Mariani sul sito Web MSDN.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [Visualizzazione Contrassegni](../profiling/marks-view.md) dei dati di profilatura.  Individuare le colonne **Memoria CLR .NET\\Raccolte di generazione 0** e **Memoria CLR .NET\\Raccolte di generazione 1**.  Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'operazione di Garbage Collection si verifica più frequentemente.  Confrontare questi valori con la colonna **Percentuale tempo in GC** per verificare se il modello di allocazioni della memoria gestita sta provocando un eccessivo sovraccarico della gestione della memoria.  
  
 Per comprendere il modello di utilizzo della memoria gestita dell'applicazione, eseguire di nuovo la profilatura con un profilo di allocazione della memoria .NET e richiedere misurazioni della durata degli oggetti.  
  
 Per informazioni su come migliorare le prestazioni di Garbage Collection, vedere [Nozioni fondamentali su Garbage Collection e suggerimenti sulle prestazioni](http://go.microsoft.com/fwlink/?LinkId=148226) sul sito Web Microsoft \(la pagina potrebbe essere in inglese\).  Per informazioni sul sovraccarico della procedura di Garbage Collection automatica, vedere [Heap di grandi oggetti](http://go.microsoft.com/fwlink/?LinkId=177836).