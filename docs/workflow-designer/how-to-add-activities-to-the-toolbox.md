---
title: "Procedura: aggiungere attivit&#224; nella Casella degli strumenti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: aggiungere attivit&#224; nella Casella degli strumenti
Esistono diversi modi per aggiungere attività alla **Casella degli strumenti** nella propria soluzione.È possibile aggiungerli dall'interno il progetto corrente oppure fare riferimento a essi da un progetto diverso o da un assembly diverso.  
  
### Per aggiungere un'attività dall'interno del progetto corrente  
  
1.  Aggiungere una nuova attività personalizzata al progetto del flusso di lavoro corrente.[!INCLUDE[crabout](../test/includes/crabout_md.md)] aggiunta di una nuova attività personalizzata al progetto, vedere [Procedura: aggiungere un nuovo elemento ad un progetto flusso di lavoro](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).  
  
2.  Aggiungere la logica personalizzata all'attività.  
  
3.  Compilare il progetto.Se la compilazione viene eseguita correttamente, viene visualizzata una nuova categoria nella **Casella degli strumenti** denominata "\<*project name*\>" con l'attività personalizzata in essa inclusa.  
  
    > [!NOTE]
    >  Se la casella degli strumenti viene reimpostata, le attività personalizzate verranno rimosse, anche se la soluzione viene compilata nuovamente.Per ripopolare la casella degli strumenti con le attività personalizzate dopo che è stata reimpostata, riavviare [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
    > [!NOTE]
    >  La casella degli strumenti può mostrare solo un'attività di un nome specificato.Se due attività derivanti da assembly differenti hanno lo stesso nome della classe, solo una viene visualizzata.  
  
    > [!NOTE]
    >  Il dominio applicazione viene condiviso tra le istanze dell'editor; se vengono utilizzate le variabili statiche, queste verranno condivise anche tra le istanze dell'editor.Se non si tratta del comportamento desiderato, un servizio deve essere utilizzato per tenere traccia delle istanze variabili.Vedere [Utilizzo del contesto di modifica ModelItem](../Topic/Using%20the%20ModelItem%20Editing%20Context.md) per ulteriori informazioni sull'utilizzo dei servizi all'interno della finestra di progettazione.  
  
### Per aggiungere un'attività dall'interno di un altro progetto  
  
1.  Aprire una soluzione che contiene almeno un progetto flusso di lavoro e un progetto libreria attività personalizzato oppure un altro progetto flusso di lavoro che definisce un'attività personalizzata.  
  
2.  Compilare entrambi i progetti.Se le compilazioni vengono eseguite correttamente, viene visualizzata una nuova categoria nella **Casella degli strumenti** denominata "\<*project name*\>" con l'attività personalizzata in essa inclusa.  
  
### Per aggiungere un'attività alla Casella degli strumenti da un assembly  
  
1.  Aprire una soluzione per flussi di lavoro.  
  
2.  Scegliere **Scegli elementi della Casella degli strumenti** dal menu **Strumenti**.  
  
3.  Nella finestra di dialogo **Scegli elementi della Casella degli strumenti** selezionare la scheda **Componenti System.Activities**, quindi fare clic su **Sfoglia** per passare all'assembly che contiene l'attività personalizzata che si desidera aggiungere.  
  
4.  Selezionare l'assembly e scegliere **OK**.Il componente attività personalizzata viene aggiunto all'elenco dei componenti e viene selezionato automaticamente.  
  
    1.  Scegliere **OK** per chiudere la finestra di dialogo.  
  
5.  Per visualizzare la casella degli strumenti, scegliere **Casella degli strumenti** dal menu **Visualizza**.  
  
6.  L'attività personalizzata viene visualizzata nella **Casella degli strumenti** sotto la categoria che aveva lo stato attivo prima che fosse aggiunto l'elemento.Se ad esempio prima di aggiungere l'elemento della casella degli strumenti è stata selezionata la categoria **Generale** nella **Casella degli strumenti**, l'attività viene visualizzata sotto la categoria **Generale**.  
  
## Vedere anche  
 [Utilizzo di Progettazione flussi di lavoro](../workflow-designer/using-the-workflow-designer.md)