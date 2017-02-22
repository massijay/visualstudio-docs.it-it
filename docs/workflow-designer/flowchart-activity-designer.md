---
title: "ActivityDesigner Diagramma di flusso | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Flowchart.UI"
  - "System.Activities.Statements.FlowStep.UI"
  - "System.Activities.Core.Presentation.FlowStart.UI"
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Diagramma di flusso
L'attività <xref:System.Activities.Statements.Flowchart> viene utilizzata per creare flussi di lavoro che definiscono e gestiscono controlli di flusso complessi.È possibile creare un'attività <xref:System.Activities.Statements.Flowchart> tramite codice o utilizzando [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].In questo argomento viene descritto come utilizzare [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] a tale scopo.L'ActivityDesigner per i flussi di lavoro di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] consente agli sviluppatori di creare flussi di lavoro in modo naturale.  
  
## Attività Flowchart  
 <xref:System.Activities.Statements.Flowchart> specifica un elemento <xref:System.Activities.Statements.Flowchart.StartNode%2A> univoco che viene eseguito all'avvio del flusso di lavoro e utilizza una rete di <xref:System.Activities.Statements.Flowchart.Nodes%2A> collegati per creare cicli arbitrari o per deviare in un determinato momento il flusso dell'esecuzione in un altro punto del flusso di lavoro.  
  
### Utilizzo dell'ActivityDesigner Flowchart  
 L'ActivityDesigner **Flowchart** è disponibile nella categoria **Messaggi** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Flowchart** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono generalmente posizionati gli ActivityDesigner, come attività radice o come attività figlio di un'altra attività del flusso di controllo.Se l'ActivityDesigner **Flowchart** viene rilasciato in un'area vuota di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene creata un'attività <xref:System.Activities.Statements.Flowchart>, che per impostazione predefinita si presenta sotto forma di visualizzazione espansa in cui il nodo iniziale che avvia l'esecuzione è rappresentato come una palla di colore verde.Se l'ActivityDesigner **Flowchart** viene rilasciato in un'altra attività del flusso di controllo, si presenta come visualizzazione ridotta a icona che può essere espansa facendo doppio clic sull'ActivityDesigner **Flowchart**.Le attività incluse nella **Casella degli strumenti** possono essere trascinate direttamente nell'ActivityDesigner **Flowchart**, insieme ad altre attività del flusso di controllo.  
  
 Dopo aver rilasciato diversi ActivityDesigner nell'area di disegno di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], è possibile collegare tra loro gli oggetti <xref:System.Activities.Activity> che rappresentano per specificarne l'ordine di esecuzione.Per creare un collegamento tra un'attività di origine e un'attività di destinazione, spostare il mouse sulla finestra di progettazione dell'attività di origine in modo da visualizzare handle quadrati su ciascun lato.Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno all'attività di destinazione durante il passaggio del mouse.Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra queste due attività rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.  
  
### Proprietà dell'attività Flowchart  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.Flowchart> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome visualizzato nell'intestazione dell'ActivityDesigner.Il valore predefinito è Flowchart.Il valore può essere modificato nella finestra **Proprietà** o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Raccolta di variabili incluse nell'ambito di questa attività <xref:System.Activities.Statements.Flowchart> per condividere lo stato tra le relative attività figlio.|  
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> eseguito all'avvio di <xref:System.Activities.Statements.Flowchart>.|  
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Contiene la raccolta di oggetti <xref:System.Activities.Statements.FlowNode> inclusi nell'attività <xref:System.Activities.Statements.Flowchart>.|  
  
## Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)