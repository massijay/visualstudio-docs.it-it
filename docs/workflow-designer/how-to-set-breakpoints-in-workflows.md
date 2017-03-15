---
title: "Procedura: impostare punti di interruzione nei flussi di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Procedura: impostare punti di interruzione nei flussi di lavoro
Quando si utilizza [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], è possibile impostare punti di interruzione nei flussi di lavoro grafici come si farebbe nel codice Visual Basic o C\#.Come previsto, l'esecuzione del flusso di lavoro viene arrestata a ogni punto di interruzione impostato.  
  
 Un punto di interruzione ha tre stati: *In sospeso*, *Associato* ed *Errore*.Quando viene impostato, un punto di interruzione si trova nello stato In sospeso e viene rappresentato da un'icona rossa.Quando il runtime carica il tipo di flusso di lavoro, lo stato passa ad Associato.Se si specifica un formato non corretto per il punto di interruzione, ad esempio un nome di attività non valido, viene visualizzata una finestra di errore.Il punto di interruzione risulta ancora aggiunto alla finestra del punto di interruzione, ma è contrassegnato con una piccola “x”.  
  
> [!NOTE]
>  L'impostazione dei punti di interruzione sui flussi di lavoro richiamati non è supportata.  
  
> [!WARNING]
>  Assicurarsi che sia selezionata l'opzione **Abilita Just My Code \(solo gestito\)** visualizzabile selezionando il menu **Strumenti**, **Opzioni**, quindi **Debug** prima di eseguire il debug.Se si dispone di due sequenze annidate in un'altra sequenza e si imposta un punto di interruzione sulla prima sequenza interna, quando si preme **F11** non verrà eseguito il debug nella seconda sequenza interna se non è selezionata l'opzione **Abilita Just My Code \(solo gestito\)**.  
  
> [!WARNING]
>  I punti di interruzione in un flusso di lavoro non vengono raggiunti se il percorso completo per la proprietà del file XAML non è corretto. Il percorso completo del file XAML non è preciso dopo avere spostato il progetto o la soluzione in un'altra cartella o a un altro computer. Selezionare CTRL\+S per salvare e aggiornare la proprietà percorso completo.  
  
### Per impostare un punto di interruzione su un'attività nella visualizzazione Progettazione  
  
1.  Selezionare l'attività in corrispondenza della quale si desidera che il debugger si interrompa.  
  
2.  Scegliere **Imposta\/Rimuovi punto di interruzione** dal menu **Debug**.Verrà visualizzata un'icona rossa sul bordo superiore sinistro dell'attività.  
  
     In alternativa, è anche possibile premere il tasto di scelta rapida **F9** dopo aver selezionato l'attività o fare clic con il pulsante destro del mouse sull'attività e scegliere **Punto di interruzione**, quindi **Inserisci punto di interruzione** dal menu di scelta rapida.  
  
## Vedere anche  
 [Procedura: richiamare il debugger del flusso di lavoro.](../workflow-designer/how-to-invoke-the-workflow-debugger.md)   
 [Debug dei flussi di lavoro mediante Progettazione flussi di lavoro](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)   
 [Procedura: debug di XML mediante Progettazione flussi di lavoro](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)