---
title: "DA0003: Numero elevato di campioni del kernel | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DA0003"
  - "vs.performance.DA0003"
  - "vs.performance.3"
  - "vs.performance.rules.DAManyKernelSamples"
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# DA0003: Numero elevato di campioni del kernel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0003|  
|Categoria|Utilizzo di strumenti di profilatura|  
|Metodi di profilatura|Campionamento|  
|Messaggio|È presente un numero elevato di campioni in modalità kernel.  Questa circostanza potrebbe indicare un volume elevato di attività I\/O oppure un rapporto elevato di cambi di contesto.  Si consiglia di profilare nuovamente l'applicazione utilizzando la modalità strumentazione.|  
|Tipo regola|Informazioni|  
  
## Causa  
 Una proporzione significativa dei campioni dello stack di chiamate raccolti per l'applicazione erano in esecuzione in modalità kernel.  Considerare l'esecuzione del profilo dell'applicazione utilizzando un metodo di profilo diverso.  
  
## Descrizione della regola  
 In Windows, è possibile eseguire il codice sia in modalità kernel che in modalità utente. La modalità kernel è anche nota come modalità privilegiata. Solo un codice di sistema di basso livello, ad esempio un driver di dispositivo, viene eseguito in modalità kernel.  Un'applicazione in modalità utente può passare in modalità kernel per eseguire operazioni di I\/O, attendere primitive di sincronizzazione di processo o thread oppure per effettuare chiamate di sistema.  
  
 Il campionamento è molto più efficace quando si profilano applicazioni che per la maggior parte del tempo eseguono operazioni in modalità utente.  Il numero di campioni raccolti quando l'applicazione era in esecuzione in modalità kernel può indicare operazioni di I\/O frequenti o il verificarsi di cambi di contesto.  Nessuna di queste operazioni può essere esaminata utilizzando il metodo di campionamento.  Se viene acquisito un numero eccessivo di campioni in modalità kernel è possibile che i dati di campionamento non siano statisticamente significativi in quanto non contengono abbastanza campioni in modalità utente.  
  
## Come correggere le violazioni  
 Si consideri di eseguire nuovamente il profilo dell'applicazione tramite una delle opzioni seguenti:  
  
-   Profilare tramite il metodo di strumentazione.  
  
-   Aumentare la frequenza di campionamento per tentare di raccogliere più campioni in modalità utente.