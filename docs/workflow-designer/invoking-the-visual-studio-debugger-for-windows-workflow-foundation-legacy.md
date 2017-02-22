---
title: "Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "debugger, flusso di lavoro"
  - "debug dei flussi di lavoro, avvio del debugger"
  - "debug, utilizzo del debugger del flusso di lavoro"
  - "Esegui istruzione (comando)"
  - "Esci da istruzione/routine (comando)"
  - "Esegui istruzione/routine (comando)"
  - "istruzioni (esecuzione)"
  - "istruzioni (esecuzione), comandi"
  - "debugger del flusso di lavoro, avvio"
  - "flussi di lavoro, debugger"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Richiamo del debugger di Visual Studio per Windows Workflow Foundation (legacy)
In questo argomento viene descritto come utilizzare il Debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire il debug di applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando è necessario fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Il debug dei flussi di lavoro legacy viene in genere eseguito nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio.È possibile avviare il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per Windows Workflow Foundation nei modi seguenti:  
  
-   Selezionare **Connetti a processo** nel menu **Debug** per selezionare un'istanza del flusso di lavoro in esecuzione dai processi disponibili.  
  
-   Premere **F5** per avviare un'istanza del flusso di lavoro o per non arrestare l'esecuzione dopo aver raggiunto un punto di interruzione.  
  
## Avanzamento tramite codice  
 Il debugger supporta una delle procedure di debug più comuni, l’avanzamento, che consiste nell'esecuzione di una riga di codice alla volta.Esistono tre comandi di avanzamento tramite codice:  
  
-   **Esegui istruzione**: è possibile avanzare in un'attività utilizzando **F11**.Il debugger avanza in qualsiasi gestore definito.Se nessun gestore è definito, viene eseguita l'istruzione\/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione.L’avanzamento in gestori del codice dalla finestra di progettazione non è supportato per le attività seguenti: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup** o **ReplicatorActivity**.Per eseguire il debug dei gestori associati a queste attività è necessario inserire punti di interruzione espliciti nel codice.  
  
-   **Esci da istruzione\/routine**: è possibile uscire dall'istruzione\/routine di un'attività utilizzando **Shift\-F11**.Uscendo dall'istruzione\/routine di un'attività, l'attività corrente viene eseguita e tutte le relative attività di pari livello vengono completate.Il debugger reimposta quindi il padre dell'attività corrente.Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.  
  
-   **Passa**: è possibile passare a un'altra attività utilizzando **F10**.Quando si passa a un'altra attività composta.Il debugger reimposta il primo figlio eseguibile dell'attività composta.Scavalcando un’attività non composta, ad esempio **CodeActivity**, il debugger esegue l'attività e i gestori ad essa associati e reimposta l’attività successiva.Se l'attività eseguita è l'ultima attività figlio di un'attività composta, dopo l'esecuzione il debugger reimposterà l'attività padre.  
  
## Connessione a un processo  
 Per eseguire il debug di un flusso di lavoro tramite una connessione a un processo, selezionare il processo disponibile dalla casella di riepilogo **Processi disponibili** nella finestra di dialogo **Connetti a un processo**.Se nella casella di testo **Connetti a** non viene visualizzato **Automatico: codice del flusso di lavoro** fare clic su **Seleziona**.Nella finestra di dialogo **Seleziona tipo di codice** fare clic su **Esegui il debug di questi tipi di codice** e selezionare **Flusso di lavoro**.Scegliere quindi **OK** e fare clic su **Connetti**.  
  
## Debug con F5  
 Se un'applicazione host del flusso di lavoro e una DLL del flusso di lavoro si trovano in progetti di Visual Studio differenti, ad esempio, quando si sta utilizzando una raccolta di attività del flusso di lavoro, per eseguire il debug del flusso di lavoro, è necessario impostare il progetto di DLL del flusso di lavoro come progetto di avvio della soluzione di Visual Studio, utilizzando **F5**.È necessario, inoltre, impostare il percorso all'applicazione host nella proprietà **Avvia programma esterno** del progetto di DLL del flusso di lavoro.  
  
 Per impostare un progetto di avvio in Esplora soluzioni, fare clic con il pulsante destro del mouse sul nome del progetto e scegliere **Imposta come progetto di avvio**.Per impostare il percorso all’host nella proprietà **Avvia programma esterno**, fare doppio clic sul nodo **Proprietà** del progetto del flusso di lavoro in Esplora soluzioni e selezionare la scheda **Debug**.Sotto **Azione di avvio**, selezionare **Avvia programma esterno** e immettere il percorso al file exe che sta ospitando il flusso di lavoro per il quale si desidera eseguire il debug.  
  
 Se l'applicazione host è impostata come progetto di avvio, solo il debugger di Visual Studio viene richiamato per l'esecuzione del debug. Il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per Windows Workflow Foundation non viene richiamato.Se viene utilizzato il debugger di Visual Studio, vengono eseguiti solo i punti di interruzione del codice C\# o di Visual Basic, mentre i punti di interruzione impostati nella finestra di progettazione del flusso di lavoro non vengono eseguiti.Ad esempio, un punto di interruzione impostato su un'attività <xref:System.Workflow.Activities.ParallelActivity> nella finestra di progettazione verrà eseguito se viene utilizzato il debugger di [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] per Windows Workflow Foundation, ma non quando si utilizza il debugger di Visual Studio.  
  
## Vedere anche  
 [Procedura: impostare punti di interruzione nei flussi di lavoro \(legacy\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)