---
title: "Procedura: debug di XML mediante Progettazione flussi di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Procedura: debug di XML mediante Progettazione flussi di lavoro
I flussi di lavoro vengono definiti mediante codice XAML.La rappresentazione dell'interfaccia utente del flusso di lavoro si basa sulla struttura ad albero XAML che definisce il flusso di lavoro.Il processo di debug è simile a quello eseguito per i flussi di lavoro di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Durante il debug di XAML, ad esempio, le finestre delle variabili locali, delle espressioni di controllo e dei thread funzionano esattamente come durante il debug di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Durante il debug di XAML, inoltre, la visualizzazione degli stack di chiamate si presenta sotto forma di visualizzazione gerarchica basata sulle righe del flusso di esecuzione del flusso di lavoro.  
  
> [!NOTE]
>  Se XAML per un flusso di lavoro si trova nello stesso assembly delle attività, la parte dell'assembly dei nomi di classe non è inclusa.Senza questa parte dei nomi di classe \(attività\), XAML non può essere caricato in fase di esecuzione.Non è consigliabile per definire le attività nello stesso spazio dei nomi del progetto principale; in caso contrario, XAML dovrà essere modificato a mano dopo essere stato modificato nella finestra di progettazione.  
  
### Per eseguire il debug del flusso di lavoro XAML  
  
1.  Aprire un flusso di lavoro o un progetto di attività in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Impostare un punto di interruzione nell'attività o nelle attività da sottoporre a debug come descritto in [Procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3.  Fare clic con il pulsante destro del mouse sul file con estensione xaml contenente la definizione del flusso di lavoro e scegliere **Visualizza codice**.Verrà visualizzato un punto di interruzione nella stessa riga in cui si trova la dichiarazione dell'elemento XAML dell'attività per la quale è stato impostato il punto di interruzione nella visualizzazione Progettazione.  
  
4.  Richiamare il debugger come descritto in [Procedura: richiamare il debugger del flusso di lavoro.](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Quando l'esecuzione del codice raggiunge uno dei punti di interruzione, l'elemento XAML associato a tale punto verrà evidenziato.Per spostarsi sul punto di interruzione successivo, utilizzare il tasto **F10** o **F11**.  
  
## Vedere anche  
 [Procedura: impostare punti di interruzione nei flussi di lavoro](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Procedura: richiamare il debugger del flusso di lavoro.](../workflow-designer/how-to-invoke-the-workflow-debugger.md)