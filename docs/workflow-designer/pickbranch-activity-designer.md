---
title: "ActivityDesigner PickBranch | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner PickBranch
<xref:System.Activities.Statements.PickBranch> offre un percorso di esecuzione basato sugli eventi all'interno di un'attività <xref:System.Activities.Statements.Pick> che può essere attivata da un evento in entrata.  
  
## PickBranch  
 Gli oggetti <xref:System.Activities.Statements.PickBranch> sono contenuti nella raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un'attività <xref:System.Activities.Statements.Pick>.Ogni oggetto <xref:System.Activities.Statements.PickBranch> è contenuto in un ramo dell'attività <xref:System.Activities.Statements.Pick> e può essere eseguito in seguito a un evento in entrata che funge da trigger.In questo modo [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] consente la modellazione di un flusso di controllo basato sugli eventi.Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### Modalità di utilizzo dell'ActivityDesigner Pick  
 L'ActivityDesigner **PickBranch** è disponibile nella categoria **Flusso di controllo** della **Casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** nella [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, selezionare **Barra degli strumenti** dal menu **Visualizza** oppure premere la combinazione CTRL\+ALT\+X.  
  
 Per impostazione predefinita, vengono creati due oggetti <xref:System.Activities.Statements.PickBranch> vuoti con i nomi visualizzati **Branch1** e **Branch2** come elementi di un'attività <xref:System.Activities.Statements.Pick> quando l'ActivityDesigner **Pick** viene inizialmente rilasciato nell'utilità [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].I rispettivi valori della proprietà <xref:System.Activities.Statements.PickBranch.DisplayName%2A> possono essere modificati nell'intestazione dell'ActivityDesigner **PickBranch** o nella finestra **Proprietà** di ogni ramo.  
  
 Esistono due diverse modalità per aggiungere oggetti <xref:System.Activities.Statements.PickBranch> alla raccolta di un oggetto <xref:System.Activities.Statements.Pick>, ovvero mediante il trascinamento dell'ActivityDesigner **PickBranch** dalla **Casella degli strumenti** o mediante il menu di scelta rapida disponibile nell'area di progettazione **Pick**:  
  
1.  L'ActivityDesigner **PickBranch** consente di creare un elemento <xref:System.Activities.Statements.PickBranch> quando viene trascinato dalla **Casella degli strumenti** e rilasciato in uno dei rami di un ActivityDesigner **Pick** nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].I nuovi oggetti <xref:System.Activities.Statements.PickBranch> possono essere posizionati all'interno della finestra di progettazione <xref:System.Activities.Statements.Pick>, a destra o a sinistra di qualsiasi elemento <xref:System.Activities.Statements.PickBranch> esistente già contenuto nella raccolta.Quando si trascina l'ActivityDesigner **PickBranch** nella finestra di progettazione **Pick** mediante il mouse, viene utilizzata dall'ActivityDesigner **Pick** una striscia verticale di colore blu\-grigio per indicare il punto in cui l'attività <xref:System.Activities.Statements.PickBranch> verrà aggiunta in base a una determinata posizione del mouse.  
  
2.  Fare clic con il pulsante destro del mouse sull'ActivityDesigner **Pick**, ma non all'interno della finestra di progettazione **PickBranch**, per visualizzare un menu di scelta rapida e scegliere **Crea ramo** per aggiungere una nuova attività <xref:System.Activities.Statements.PickBranch>.Il nuovo elemento <xref:System.Activities.Statements.PickBranch> verrà aggiunto a destra degli oggetti <xref:System.Activities.Statements.PickBranch> esistenti nella finestra di progettazione **Pick**.  
  
 L'ActivityDesigner **PickBranch** può essere espanso per visualizzare le caselle **Trigger** e **Action** o compresso facendo clic sui due accenti circonflessi sul lato destro delle rispettive intestazioni.Modificare gli elementi <xref:System.Activities.Statements.PickBranch.Trigger%2A> e <xref:System.Activities.Statements.PickBranch.Action%2A> di ogni <xref:System.Activities.Statements.PickBranch> trascinando le attività nelle caselle **Trigger** e **Action** delle rispettive finestre di progettazione.  
  
 Gli oggetti <xref:System.Activities.Statements.PickBranch> della raccolta <xref:System.Activities.Statements.Pick.Branches%2A> di un oggetto <xref:System.Activities.Statements.Pick> possono essere riordinati trascinandoli in una nuova posizione all'interno della finestra di progettazione **Pick**.Nella finestra di progettazione **Pick** viene utilizzata una striscia verticale di colore blu\-grigio per indicare la posizione in cui l'attività <xref:System.Activities.Statements.PickBranch> verrà aggiunta in base a una determinata posizione del mouse.  
  
 Esistono due diverse modalità per eliminare un'attività <xref:System.Activities.Statements.PickBranch>:  
  
1.  Selezionare la finestra di progettazione **PickBranch** ed eliminarla.  
  
2.  Selezionare la finestra di progettazione **PickBranch**, fare clic con il pulsante destro del mouse sul menu di scelta rapida e scegliere **Elimina**.  
  
 Assicurarsi di selezionare la finestra di progettazione **PickBranch**, in quanto la selezione accidentale di una delle attività nella casella **Trigger** o **Action** comporta l'eliminazione di tale attività e non dell'oggetto <xref:System.Activities.Statements.PickBranch>.  
  
### Proprietà di PickBranch in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.PickBranch> e ne viene descritto l'utilizzo in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Nome descrittivo visualizzato nell'intestazione dell'ActivityDesigner **PickBranch**.Il valore predefinito è Branch.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Ogni <xref:System.Activities.Statements.PickBranch> contiene un'azione <xref:System.Activities.Statements.PickBranch.Trigger%2A> che può richiamare l'elemento <xref:System.Activities.Statements.PickBranch.Action%2A>.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Ogni <xref:System.Activities.Statements.PickBranch> contiene un elemento <xref:System.Activities.Statements.PickBranch.Action%2A> che viene eseguito se attivato.|  
  
## Vedere anche  
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)   
 [Attività Pick](../Topic/Pick%20Activity.md)   
 [Utilizzo dell'attività Pick](../Topic/Using%20the%20Pick%20Activity.md)