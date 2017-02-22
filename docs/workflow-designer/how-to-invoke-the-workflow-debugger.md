---
title: "Procedura: richiamare il debugger del flusso di lavoro. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: richiamare il debugger del flusso di lavoro.
Il debug dei flussi di lavoro viene in genere eseguito nello stesso modo in cui si esegue il debug di programmi scritti negli altri linguaggi di programmazione di Visual Studio.È possibile avviare il debugger del flusso di lavoro nei modi seguenti:  
  
-   Selezionare **Connetti a processo** nel menu **Debug** per selezionare il processo host in esecuzione per l'istanza del flusso di lavoro.La procedura è identica a quella di collegamento a un processo host nel codice gestito.  
  
-   Premere **F5** per avviare un'istanza del flusso di lavoro o per non arrestare l'esecuzione dopo aver raggiunto un punto di interruzione.  
  
-   Utilizzare debug remoto.Per informazioni sul debug remoto, vedere [Procedura: attivare il debug remoto](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Se l'applicazione flusso di lavoro è destinata all'architettura x86 ed è contenuta in un computer che esegue un sistema operativo a 64 bit, il debug remoto non funzionerà a meno che [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sia installato nel computer remoto o la destinazione dell'applicazione flusso di lavoro è stata modificata in **Qualsiasi CPU**.  
  
### Esecuzione di codice istruzione per istruzione  
  
-   **Esegui istruzione**: è possibile avanzare in un'attività utilizzando **F11**.Il debugger avanza in qualsiasi gestore definito.Se nessun gestore è definito, viene eseguita l'istruzione\/routine dell'attività oppure, con CompositeActivity contenenti altre attività, viene eseguita l'istruzione della prima attività in stato di esecuzione.  
  
-   **Esci da istruzione\/routine**: è possibile uscire dall'istruzione\/routine di un'attività utilizzando **MAIUSC\+F11**.Uscendo dall'istruzione\/routine di un'attività, l'attività corrente viene eseguita e tutte le relative attività di pari livello vengono completate.Il debugger reimposta quindi il padre dell'attività corrente.Uscendo da un gestore del codice, il debugger reimposta l'attività alla quale è associato il gestore.  
  
-   **Esegui istruzione\/routine**: è possibile eseguire l'istruzione\/routine di un'altra attività utilizzando **F10**.Quando viene eseguita l'istruzione\/routine di un oggetto CompositeActivity, il debugger reimposta il primo figlio eseguibile del CompositeActivity.Quando viene eseguita l'istruzione\/routine di un attività diversa da CompositeActivity, ad esempio <xref:System.Activities.Statements.Assign>, il debugger esegue l'attività e i gestori ad essa associati e reimposta l’attività successiva.Se l'attività eseguita è l'ultima attività figlio di un oggetto CompositeActivity, dopo l'esecuzione il debugger reimposterà l'attività padre.  
  
### Debug con F5  
  
-   Se si compila un progetto Applicazione console flusso di lavoro, è sufficiente premere **F5** per avviare il debug nell'applicazione e nel flusso di lavoro.Se si compila una libreria attività autonomamente, è necessario utilizzare come progetto di avvio un'applicazione host eseguibile.Per impostare un progetto di avvio in **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul nome del progetto dell'host e scegliere **Imposta come progetto di avvio**.  
  
## Vedere anche  
 [Procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)