---
title: "DA0017: Frequenze elevate di paging di memoria attiva su disco | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.17"
  - "vs.performance.rules.DA0017"
  - "vs.performance.DA0017"
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# DA0017: Frequenze elevate di paging di memoria attiva su disco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0017|  
|Category|Memoria e paging|  
|Metodo di profilatura|Tutte|  
|Messaggio|È stata rilevata una frequenza elevata di paging di memoria attiva su disco.  L'applicazione potrebbe essere associata alla memoria.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## Causa  
 I dati relativi alle prestazioni di sistema raccolti nell'esecuzione della profilatura indicano che si è verificata una frequenza elevata di paging di memoria attiva da e su disco durante la profilatura.  Le frequenze di paging a questo livello avranno normalmente un impatto sulle prestazioni e sulla velocità di risposta dell'applicazione.  Considerare la possibilità di ridurre le allocazioni di memoria rivedendo gli algoritmi.  Potrebbe inoltre essere necessario considerare i requisiti di memoria dell'applicazione,  
  
## Descrizione della regola  
  
> [!NOTE]
>  Questa regola informativa viene attivata quando i livelli di paging di memoria attiva raggiungono una quantità significativa.  Quando si verifica un livello di paging estremamente elevato, viene attivata invece la regola di avviso [DA0014: Frequenze molto elevate di paging di memoria attiva su disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md).  
  
 Un'attività di paging su disco eccessiva può essere causata da memoria fisica insufficiente.  Se le operazioni di paging utilizzano in modo dominante il disco fisico su cui risiede il file di paging, possono rallentare le altre operazioni del disco orientate all'applicazione sullo stesso disco.  
  
 Le pagine vengono spesso lette dal disco o scritte sul disco nelle operazioni di paging di massa.  Il numero di pagine generate al secondo è spesso molto maggiore del numero di pagine scritte al secondo, ad esempio,  perché il numero di pagine generate al secondo include anche le pagine di dati modificate dalla cache dei file di sistema.  Tuttavia, non è sempre facile determinare quale processo è direttamente responsabile del paging o perché.  
  
## Come correggere le violazioni  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md).  Individuare la colonna **Memoria\\Pagine\/sec**.  Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'attività I\/O di paging è più elevata rispetto ad altre.  
  
 Se si raccolgono dati del profilo per un'applicazione ASP.NET in un scenario del test di carico, provare a eseguire nuovamente il test di carico su un computer configurato con memoria fisica \(o RAM\) aggiuntiva.  
  
 Considerare la possibilità di ridurre le allocazioni di memoria rivedendo gli algoritmi ed evitando API che utilizzano molta memoria, ad esempio String.Concat e String.Substring.