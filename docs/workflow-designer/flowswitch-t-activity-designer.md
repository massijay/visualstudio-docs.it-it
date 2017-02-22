---
title: "ActivityDesigner FlowSwitch&lt;T&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner FlowSwitch&lt;T&gt;
L'attività <xref:System.Activities.Statements.FlowSwitch%601> è un nodo condizionale che consente la creazione di rami per il flusso di controllo in base ai criteri di corrispondenza quando sono necessari più di due rami alternativi.Se la creazione di rami per il flusso richiede solo due percorsi, utilizzare invece l'attività <xref:System.Activities.Statements.FlowDecision>.  
  
## Attività FlowSwitch\<T\>  
 L'attività <xref:System.Activities.Statements.FlowSwitch%601> contiene un oggetto <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> che restituisce un valore di tipo *T* \(specificato dal parametro generico\) al momento della valutazione.L'attività contiene inoltre un set di <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> che specifica un mapping univoco tra i possibili risultati di questa valutazione e un set di oggetti <xref:System.Activities.Statements.FlowNode>.L'elemento <xref:System.Activities.Statements.FlowNode> eseguito è quello il cui oggetto di tipo *T* corrisponde al valore dell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> valutato.È possibile fornire facoltativamente un case <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> se non è presente alcuna corrispondenza.  
  
### Utilizzo dell'ActivityDesigner FlowSwitch\<T\>  
 L'ActivityDesigner **FlowSwitch\<T\>** è disponibile nella categoria **Diagramma di flusso** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** nella parte sinistra di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **FlowSwitch\<T\>** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] all'interno di un ActivityDesigner **Flowchart**.Utilizzare la finestra **Seleziona tipi** visualizzata per specificare il tipo \(associato nel codice all'oggetto <xref:System.Activities.Statements.FlowSwitch%601> tramite il relativo parametro generico\) ottenuto dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>.Questa procedura crea un'attività <xref:System.Activities.Statements.FlowSwitch%601> denominata **Switch** all'interno dell'attività <xref:System.Activities.Statements.Flowchart>.È possibile digitare <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> nella casella **Expression** della finestra **Proprietà** facendo clic nella posizione del testo di suggerimento "Immettere un'espressione VB".  
  
 Spostare il mouse sull'ActivityDesigner **FlowSwitch\<T\>** in modo da visualizzare gli handle quadrati utilizzati per collegare <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> intorno ai relativi bordi.Dopo aver rilasciato l'ActivityDesigner **FlowSwitch\<T\>** e altri ActivityDesigner su **Flowchart**, sarà possibile collegare gli oggetti <xref:System.Activities.Activity> che rappresentano per specificare l'ordine di esecuzione.Per creare uno degli oggetti <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associati a <xref:System.Activities.Statements.FlowSwitch%601>, fare clic su uno degli handle quadrati dei case sul perimetro di **FlowSwitch\<T\>** e trascinarlo, tenendo premuto il pulsante del mouse, su uno degli handle visualizzati in modo simile intorno all'attività di destinazione durante il passaggio del mouse sulla finestra di progettazione.Rilasciare il pulsante del mouse. Verrà visualizzata una freccia che collega **FlowSwitch\<T\>** alla finestra di progettazione di destinazione che rappresenta questo case.Il valore predefinito per questo case viene visualizzato sulla freccia e può essere modificato nella casella **Case** della finestra **Proprietà**.  
  
### Proprietà di FlowSwitch\<T\>  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.FlowSwitch%601> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Specifica l'espressione valutata per identificare l'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> cui passare nel percorso di esecuzione.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Specifica un mapping univoco tra i possibili risultati ottenuti dalla valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> e un set di oggetti <xref:System.Activities.Statements.FlowNode>.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Specifica il mapping quando la valutazione di <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> non corrisponde a uno dei valori contenuti nell'oggetto <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>.|  
  
## Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designers.md)   
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)