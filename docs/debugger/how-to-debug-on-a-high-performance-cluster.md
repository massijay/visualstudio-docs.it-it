---
title: "Procedura: eseguire il debug su un cluster ad alte prestazioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug di cluster"
  - "debug ad alte prestazioni"
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: eseguire il debug su un cluster ad alte prestazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug di un programma con multiprocessing in un cluster ad alte prestazioni è simile al debug di un programma normale in un computer remoto.  È tuttavia necessario fare alcune considerazioni specifiche.  Per i requisiti generali relativi all'impostazione del debug remoto, vedere [Debug remoto](../debugger/remote-debugging.md).  
  
 Quando si esegue il debug in un cluster ad alte prestazioni, è possibile usare tutte le tecniche e le finestre di debug di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] disponibili per il debug remoto.  Poiché, tuttavia, il debug viene eseguito in remoto, la finestra della console esterna non è disponibile.  
  
 Le finestre **Thread** e **Processi** sono particolarmente utili per il debug di applicazioni parallele.  Per suggerimenti relativi all'utilizzo di queste finestre, vedere [How to: Use the Processes Window](http://msdn.microsoft.com/it-it/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) e [Procedura: utilizzare la finestra Thread](../debugger/how-to-use-the-threads-window.md).  
  
 Nelle procedure riportate di seguito sono illustrate alcune tecniche che risultano particolarmente utili per il debug in un cluster ad alte prestazioni.  
  
 Quando si esegue il debug di un'applicazione parallela, è possibile impostare un punto di interruzione in un thread, in un processo o in un computer specifico.  A tale scopo, è possibile creare un punto di interruzione normale e quindi aggiungere un apposito filtro.  
  
### Per aprire la finestra di dialogo Filtro punto di interruzione  
  
1.  Fare clic con il pulsante destro del mouse su un glifo del punto di interruzione in una finestra di origine, nella finestra **Disassembly**, nella finestra **Stack di chiamate** o nella finestra **Punti di interruzione**.  
  
2.  Scegliere **Filtro** dal menu di scelta rapida.  Questa opzione può essere presente nel menu di livello superiore o nel sottomenu sotto **Punti di interruzione**.  
  
### Per impostare un punto di interruzione in un computer specifico  
  
1.  Ottenere il nome del computer nella finestra **Processi**.  
  
2.  Selezionare un punto di interruzione e aprire la finestra di dialogo **Filtro punto di interruzione** come descritto nella procedura precedente.  
  
3.  Nella finestra di dialogo **Filtro punto di interruzione** digitare:  
  
     MachineName \=*yourmachinename*  
  
     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.  
  
4.  Fare clic su **OK**.  
  
### Per impostare un punto di interruzione in un processo specifico  
  
1.  Ottenere il nome o il numero di ID del processo nella finestra **Processi**.  
  
2.  Selezionare un punto di interruzione e aprire la finestra di dialogo **Filtro punto di interruzione** come descritto nella prima procedura.  
  
3.  Nella finestra di dialogo **Filtro punto di interruzione** digitare:  
  
     `ProcessName =`  *yourprocessname*  
  
     \-oppure\-  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.  
  
4.  Fare clic su **OK**.  
  
### Per impostare un punto di interruzione in un thread specifico  
  
1.  Ottenere il nome o il numero ID del thread nella finestra **Thread**.  
  
2.  Selezionare un punto di interruzione e aprire la finestra di dialogo **Filtro punto di interruzione** come descritto nella prima procedura.  
  
3.  Nella finestra di dialogo **Filtro punto di interruzione** digitare:  
  
     `ThreadName =` *yourthreadname*  
  
     \-oppure\-  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Per creare un filtro più complesso, è possibile combinare clausole utilizzando `&`, l'operatore AND, `||`, l'operatore OR, `!`, l'operatore NOT e le parentesi.  
  
4.  Fare clic su **OK**.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come creare un filtro per un punto di interruzione in un computer denominato `marvin` e un thread denominato `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## Vedere anche  
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug remoto](../debugger/remote-debugging.md)   
 [How to: Use the Processes Window](http://msdn.microsoft.com/it-it/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Procedura: utilizzare la finestra Thread](../debugger/how-to-use-the-threads-window.md)   
 [Threads and Processes](http://msdn.microsoft.com/it-it/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)