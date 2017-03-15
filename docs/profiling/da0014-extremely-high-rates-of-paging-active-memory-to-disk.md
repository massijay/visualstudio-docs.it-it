---
title: "DA0014: Frequenze molto elevate di paging di memoria attiva su disco | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAMemoryBound"
  - "vs.performance.DA0014"
  - "vs.performance.14"
  - "vs.performance.rules.DA0014"
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0014: Frequenze molto elevate di paging di memoria attiva su disco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0014|  
|Categoria|Memoria e paging|  
|Metodo di profilatura|Tutto|  
|Messaggio|È stata rilevata una frequenza molto elevata di paging di memoria attiva su disco.  L'applicazione potrebbe essere associata alla memoria.|  
|Tipo regola|Avviso|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 25 campioni per attivare questa regola.  
  
## Causa  
 I dati relativi alle prestazioni di sistema raccolti nell'esecuzione della profilatura indicano che si è verificata una frequenza estremamente elevata di paging di memoria attiva da e su disco durante la profilatura.  In genere le frequenze di paging a questo livello hanno un impatto sulle prestazioni e sulla capacità di risposta dell'applicazione.  Considerare la possibilità di ridurre le allocazioni di memoria rivedendo gli algoritmi.  Potrebbe inoltre essere necessario considerare i requisiti di memoria dell'applicazione. Eseguire di nuovo la profilatura su un computer con una maggiore quantità di memoria.  
  
## Descrizione della regola  
 Un'attività di paging su disco eccessiva può essere causata da memoria fisica insufficiente.  Se le operazioni di paging utilizzano in modo dominante il disco fisico su cui risiede il file di paging, possono rallentare le altre operazioni del disco orientate all'applicazione sullo stesso disco.  
  
 Molto spesso le pagine vengono lette dal disco o scritte nel disco mediante operazioni di paging di massa.  Molto spesso il numero di output di pagina al secondo è assai maggiore del numero di scritture di pagina al secondo, ad esempio.  perché il numero di pagine generate al secondo include anche le pagine di dati modificate dalla cache dei file di sistema.  Tuttavia, non è sempre facile determinare quale processo è direttamente responsabile del paging o perché.  
  
> [!NOTE]
>  Questa regola viene attivata quando i livelli di paging della memoria attiva raggiungono una frequenza molto elevata.  Quando il livello di paging è significativo, ma non estremo, viene invece attivata la regola informativa [DA0017: Frequenze elevate di paging di memoria attiva su disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md).  
  
## Come correggere le violazioni  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md).  Individuare la colonna **Memoria\\Pagine\/sec**.  Determinare se sono presenti fasi specifiche di esecuzione del programma in cui l'attività I\/O di paging è più elevata rispetto ad altre.  
  
 Se si raccolgono dati del profilo per un'applicazione ASP.NET in un scenario del test di carico, provare a eseguire nuovamente il test di carico su un computer configurato con memoria fisica \(o RAM\) aggiuntiva.  
  
 Considerare la possibilità di ridurre le allocazioni di memoria rivedendo gli algoritmi ed evitando API che utilizzano molta memoria, ad esempio String.Concat e String.Substring.