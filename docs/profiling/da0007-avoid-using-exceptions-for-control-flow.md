---
title: "DA0007: Evitare di utilizzare eccezioni per il flusso di controllo | Microsoft Docs"
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
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0007: Evitare di utilizzare eccezioni per il flusso di controllo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0007|  
|Categoria|Utilizzo di .NET Framework|  
|Metodi di profilatura|Tutto|  
|Messaggio|Rilevato un elevato numero costante di eccezioni.  Provare a ridurre l'utilizzo di eccezioni nella logica di programma.|  
|Tipo messaggio|Avviso|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 25 campioni per attivare questa regola.  
  
## Causa  
 Nei dati di profilatura sono stati chiamati gestori di eccezioni .NET Framework con una frequenza elevata.  Considerare l'utilizzo di un'altra logica del flusso di controllo per ridurre il numero di eccezioni generate.  
  
## Descrizione della regola  
 Benché utilizzare gestori di eccezioni per rilevare gli errori e gli altri eventi che compromettono l'esecuzione del programma sia una procedura consigliata, l'utilizzo di un gestore di eccezioni come parte della normale logica di esecuzione del programma può essere costoso e deve essere evitato.  Nella maggior parte dei casi, le eccezioni devono essere utilizzate solo in circostanze eccezionali e impreviste.  Le eccezioni non devono essere utilizzate per restituire valori come parte del flusso di programma normale.  In molti casi per evitare la generazione di eccezioni è possibile convalidare i valori e utilizzare logica condizionale per arrestare l'esecuzione delle istruzioni che provocano il problema.  
  
 Per ulteriori informazioni vedere la sezione [Gestione delle eccezioni](http://go.microsoft.com/fwlink/?LinkID=177825) del **Chapter 5 — Improving Managed Code Performance** nel volume di **Improving .NET Application Performance and Scalability** della libreria di **Microsoft Patterns and Practices** su MSDN.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione Contrassegni.  Trovare la colonna che contiene le misure **Eccezioni CLR .NET \(@ ProcessInstance\) \\ Eccezioni\/sec**.  Determinare se esistono fasi specifiche dell'esecuzione del programma dove la gestione delle eccezioni risulta più frequente rispetto alle altre fasi.  Utilizzando un profilo di campionamento, provare a identificare le istruzioni throw e i blocchi try\/catch che generano eccezioni frequenti.  Se necessario, aggiungere logica ai blocchi catch per individuare le eccezioni che vengono gestite più spesso.  Dove possibile, sostituire le istruzioni throw o i blocchi catch eseguiti frequentemente con una logica di controllo di flusso o un codice di convalida a bassa complessità.  
  
 Ad esempio, se si rileva che l'applicazione sta gestendo eccezioni DivideByZeroException frequenti, per migliorare le prestazioni dell'applicazione è possibile aggiungere logica al programma per verificare la presenza di denominatori con valori zero.