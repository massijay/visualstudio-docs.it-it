---
title: "ActivityDesigner FlowDecision | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# ActivityDesigner FlowDecision
Il nodo <xref:System.Activities.Statements.FlowDecision> è un nodo condizionale che fornisce due rami alternativi per il flusso di controllo a seconda che venga soddisfatta una condizione specificata.Se il flusso richiede più di due rami, utilizzare invece <xref:System.Activities.Statements.FlowSwitch%601>.  
  
## Nodo FlowDecision  
 Utilizzare <xref:System.Activities.Statements.FlowDecision> quando per il flusso è possibile creare due rami in due percorsi.Un nodo <xref:System.Activities.Statements.FlowDecision> presenta un oggetto <xref:System.Activities.Statements.FlowDecision.Condition%2A> e un oggetto <xref:System.Activities.Statements.FlowNode> associato a ognuno dei due possibili risultati: <xref:System.Activities.Statements.FlowDecision.True%2A> o <xref:System.Activities.Statements.FlowDecision.False%2A>.L'elemento <xref:System.Activities.Statements.FlowDecision.Condition%2A> viene valutato e il valore di questa valutazione determina il successivo nodo <xref:System.Activities.Statements.FlowNode> da elaborare nell'oggetto <xref:System.Activities.Statements.Flowchart>.  
  
### Utilizzo dell'ActivityDesigner FlowDecision  
 L'ActivityDesigner **FlowDecision** è disponibile nella categoria **Diagramma di flusso** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **FlowDecision** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] all'interno di un ActivityDesigner **Flowchart**.In questo modo viene creato un nodo <xref:System.Activities.Statements.FlowDecision> denominato **Decision** all'interno dell'attività <xref:System.Activities.Statements.Flowchart>.Spostare il mouse sull'ActivityDesigner in modo da visualizzare gli handle quadrati **True** e **False** per i due rami.  
  
 Dopo avere trascinato l'ActivityDesigner **FlowDecision** e le altre finestre di progettazione su **Flowchart**, i nodi possono essere collegati per specificare l'ordine di esecuzione.Per creare un collegamento tra un nodo di origine \(inclusi i rami **True** e **False** di **FlowDecision**\) e un nodo di destinazione, spostare il mouse sulla finestra di progettazione del nodo di origine in modo da visualizzare handle quadrati su ogni lato.Fare clic su uno degli handle quadrati e, tenendo premuto il pulsante del mouse, trascinarlo su uno degli handle visualizzati in modo simile intorno al nodo di destinazione durante il passaggio del mouse.Dopo aver rilasciato il pulsante del mouse, verrà creato un collegamento tra questi due nodi rappresentato da una freccia che collega la finestra di progettazione di origine a quella di destinazione.  
  
 L'espressione che dichiara <xref:System.Activities.Statements.FlowDecision.Condition%2A> può essere digitata nella casella **Condition** della finestra **Proprietà** facendo clic nella posizione del testo di suggerimento "Immettere un'espressione VB".  
  
### Proprietà di FlowDecision  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.FlowDecision> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|Condizione che determina il percorso seguito dal controllo di flusso.|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|Percorso seguito dal controllo di flusso se viene soddisfatta <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|Percorso seguito dal controllo di flusso se non viene soddisfatta <xref:System.Activities.Statements.FlowDecision.Condition%2A>.|  
  
## Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)   
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)