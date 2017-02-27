---
title: "Procedura: impostare punti di interruzione nei flussi di lavoro (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "punti di interruzione, impostazione nei flussi di lavoro"
  - "debug dei flussi di lavoro, impostazione di punti di interruzione"
  - "debug, impostazione di punti di interruzione nei flussi di lavoro"
  - "flussi di lavoro, impostazione di punti di interruzione"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Procedura: impostare punti di interruzione nei flussi di lavoro (legacy)
In questo argomento viene descritto come impostare punti di interruzione nelle applicazioni [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy.Utilizzare la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy quando l'applicazione [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] deve fare riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando si utilizza la [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] legacy in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] per compilare un'applicazione [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)], è possibile impostare punti di interruzione nei codici C\# e Visual Basic come in Visual Studio.Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.  
  
 Un punto di interruzione ha tre stati: *In sospeso*, *Associato* ed *Errore*.Quando si imposta un punto di interruzione, sarà In sospeso e verrà rappresentato da un icona di colore rosso vuota.Quando il tipo del flusso di lavoro viene caricato dal runtime, diventa Associato e viene rappresentato da un’icona  rossa a tinta unita.Se si specifica un formato non corretto per il punto di interruzione, come avviene quando un nome di attività non è valido, verrà visualizzata una finestra di errore.Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.  
  
 È possibile impostare punti di interruzione su un'attività sull'area di progettazione del flusso di lavoro nelle modalità seguenti:  
  
-   fare clic con il pulsante destro del mouse sull'attività e selezionare **Punto di interruzione \\ Inserire Punto di interruzione**.  
  
-   Selezionare l’attività e premere F9.  
  
-   Scegliere **Nuovo punto di interruzione** dal menu **Debug**.  
  
     È inoltre possibile utilizzare questa opzione per impostare un nuovo punto di interruzione durante l'esecuzione del debug, quando il debugger si arresta in corrispondenza di un punto di interruzione.  
  
    > [!NOTE]
    >  L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.  
  
### Per impostare un punto di interruzione utilizzando l'opzione Nuovo punto di interruzione nel menu Debug  
  
1.  Scegliere **Nuovo punto di interruzione** dal menu **Debug**.  
  
2.  Fare clic su **Interrompi alla funzione**.  
  
     Verrà aperta la finestra di dialogo **Nuovo punto di interruzione**.  
  
3.  Specificare il nome di un'attività nella casella di testo **Funzione** utilizzando questa sintassi: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Facoltativamente, anziché utilizzare il nome di attività nella casella di testo **Funzione**, è possibile impostare un punto di interruzione specificando il percorso assoluto dell'attività del flusso di lavoro.Si supponga ad esempio di avere una soluzione del flusso di lavoro denominata **WorkflowConsoleApplication1** e un flusso di lavoro nella soluzione denominato **Workflow1** che utilizza un'attività chiamata **Delay1**.È possibile utilizzare il nome dell'attività **Delay1** o specificare il percorso come **Delay1:WorkflowConsoleApplication1 .Workflow1** o **Delay1:WorkflowConsoleApplication1 .Workflow1: {6614886A\-608E\-412B\-BF98\-99FF1559DDDF}**.  
  
4.  Selezionare la casella di controllo **Utilizza IntelliSense** per verificare il nome della funzione.  
  
     Se questa casella di controllo non è selezionata, non viene eseguita nessuna verifica del nome del punto di interruzione.  
  
5.  Selezionare **Flusso di lavoro** dall'elenco **Linguaggio**.  
  
6.  Scegliere **OK**.  
  
## Vedere anche  
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)   
 [Richiamo del debugger di Visual Studio per Windows Workflow Foundation \(legacy\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)