---
title: "Debug di applicazioni multithreading in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.gputthreads"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], calcolo ad alte prestazioni"
  - "debug [Visual Studio], multithreading"
  - "debug ad alte prestazioni"
  - "debug con multithreading"
  - "threading [Visual Studio], debug"
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug di applicazioni multithreading in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un thread è una sequenza di istruzioni in base alla quale il sistema operativo esegue l'allocazione del tempo processore.  Ogni processo in esecuzione nel sistema operativo è composto da almeno un thread.  I processi composti da più di un thread sono detti multithreading.  
  
 I computer multiprocessore, i processori multicore e i processi hyperthreading sono in grado di eseguire contemporaneamente più thread.  Se da un lato l'elaborazione parallela di più thread può migliorare notevolmente le prestazioni dei programmi, dall'altro può rendere il debug più difficoltoso poiché introduce la necessità di tenere traccia di più thread.  
  
 Il multithreading introduce inoltre nuovi tipi di possibili bug.  Accade spesso, ad esempio, che due o più thread debbano accedere alla stessa risorsa, alla quale però può accedere un solo thread alla volta.  Deve necessariamente esistere una qualche forma di esclusione reciproca per garantire l'accesso alla risorsa di un solo thread alla volta.  Se l'esclusione reciproca non viene eseguita in modo corretto, può venirsi a creare una condizione di *deadlock* in cui non è possibile eseguire alcun thread.  I deadlock possono rappresentare un problema particolarmente difficile da risolvere con il debug.  
  
 Visual Studio fornisce un **Thread** finestra, una finestra thread GPU, una finestra Espressioni di controllo parallelo e altre funzionalità che rendono il debug multithreading. Il modo migliore per acquisire ulteriori informazioni sulle nuove funzionalità dell'interfaccia di threading consiste nell'eseguire le procedure dettagliate.  Vedere [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md) e [Procedura dettagliata: Debug di un'applicazione C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md).  
  
 Visual Studio offre anche potenti punti di interruzione e punti di analisi che possono rivelarsi molto utili per il debug di applicazioni multithreading.  È possibile applicare filtri dei punti di interruzione per inserire punti di interruzione in corrispondenza di singoli thread.  Vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md) di Visual Studio  
  
 Il debug di un'applicazione multithreading dotata di un'interfaccia utente può essere particolarmente complesso.  In tal caso, potrebbe essere necessario eseguire l'applicazione in un secondo computer e utilizzare il debug remoto.  Per ulteriori informazioni, vedere [Debug remoto](../debugger/remote-debugging.md).  
  
## In questa sezione  
 [Debug di thread e processi](../debugger/debug-threads-and-processes.md)  
 Vengono illustrate le nozioni fondamentali di debug di thread e processi.  
  
 [Debug di processi](../debugger/debug-multiple-processes.md)  
 Spiega la procedura per eseguire il debug di più processi  
  
 [Procedura: utilizzare la finestra Thread](../debugger/how-to-use-the-threads-window.md)  
 Procedure utili per il debug dei thread mediante la finestra **Thread**.  
  
 [Procedura: passare a un altro thread durante il debug](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Tre modi per passare il contesto di debug a un altro thread.  
  
 [Procedura: impostare e rimuovere i flag dei thread](../debugger/how-to-flag-and-unflag-threads.md)  
 Aggiunta di contrassegni o flag ai thread a cui è opportuno prestare particolare attenzione durante il debug.  
  
 [Procedura: impostare il nome di un thread in codice nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Attribuzione di un nome da visualizzare nella finestra **Thread**.  
  
 [Procedura: impostare il nome di un thread in codice gestito](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Attribuzione di un nome da visualizzare nella finestra **Thread**.  
  
 [Procedura dettagliata: debug di un'applicazione multithreading](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Presentazione guidata delle funzionalità di debug dei thread, con particolare attenzione alle funzionalità procedura [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 [Procedura: eseguire il debug su un cluster ad alte prestazioni](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Tecniche per il debug di applicazioni in esecuzione su un cluster ad alte prestazioni.  
  
 [Suggerimenti per il debug dei thread in codice nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Semplici tecniche utili per il debug di thread nativi.  
  
 [Utilizzo della finestra Attività](../debugger/using-the-tasks-window.md)  
 Visualizza un elenco di tutti gli oggetti attività gestiti o nativi con il rispettivo stato e altre informazioni utili.  
  
 [Utilizzo della finestra Stack in parallelo](../debugger/using-the-parallel-stacks-window.md)  
 Visualizza gli stack di chiamate di più thread \(o attività\) in un'unica visualizzazione e riunisce inoltre i segmenti dello stack comuni ai vari thread \(o attività\).  
  
 [Procedura dettagliata: debug di un'applicazione parallela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Procedura dettagliata che illustra come utilizzare le finestre Attività in parallelo e Stack in parallelo.  
  
 [Procedura: utilizzare la finestra Espressione di controllo in parallelo](../debugger/how-to-use-the-parallel-watch-window.md)  
 Controllare i valori e le espressioni in più thread.  
  
 [Procedura: utilizzare la finestra Thread GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
 Esaminare e utilizzare i thread in esecuzione sulla GPU durante il debug.  
  
## Sezioni correlate  
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)  
 -   Usare filtri dei punti di interruzione per inserire un punto di interruzione in corrispondenza di un singolo thread.  
  
-   I punti di traccia consentono di tracciare l'esecuzione dei programmi senza interruzioni.  Ciò può risultare utile nello studio di problemi quali i deadlock.  
  
 [Threading](../Topic/Managed%20Threading.md)  
 Informazioni sul threading ed esempio di codice nella programmazione di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)  
 Utilizzo del multithreading nei componenti di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Supporto del multithreading per il codice precedente \(Visual C\+\+\)](/visual-cpp/parallel/multithreading/multithreading-support-for-older-code-visual-cpp)  
 Informazioni sul threading ed esempio di codice per programmatori C\+\+ che utilizzano MFC.  
  
## Vedere anche  
 [Debug di thread e processi](../debugger/debug-threads-and-processes.md)   
 [Debug remoto](../debugger/remote-debugging.md)