---
title: "ActivityDesigner If | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# ActivityDesigner If
L'attività <xref:System.Activities.Statements.If> valuta una condizione ed esegue un'attività che dipende dai risultati di tale valutazione.Questa attività è molto utile in caso di utilizzo di un stile di modellazione procedurale della programmazione.Un'attività <xref:System.Activities.Statements.If> può essere ad esempio annidata in un'attività <xref:System.Activities.Statements.Sequence> o in un'attività <xref:System.Activities.Statements.Parallel>.Se si utilizza un'attività <xref:System.Activities.Statements.Flowchart>, si prenda in considerazione l'utilizzo alternativo di un'attività <xref:System.Activities.Statements.FlowDecision>.  
  
## Proprietà di If in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà più utili dell'attività <xref:System.Activities.Statements.If> e ne viene descritto l'utilizzo nella finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|La condizione che determina l'attività figlio da eseguire.Per impostare la proprietà <xref:System.Activities.Statements.If.Condition%2A>, digitare un'espressione [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] nella casella **Condition** nell'ActivityDesigner **If** oppure nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|L'attività da eseguire se la proprietà <xref:System.Activities.Statements.If.Condition%2A> è **false**.Per aggiungere un'attività eseguita dal ramo <xref:System.Activities.Statements.If.Else%2A>, rilasciarla dalla **Casella degli strumenti** nella casella **Else** nell'ActivityDesigner **If** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|L'attività da eseguire se la proprietà <xref:System.Activities.Statements.If.Condition%2A> è **true**.Per aggiungere un'attività eseguita dal ramo <xref:System.Activities.Statements.If.Then%2A>, rilasciarla dalla **Casella degli strumenti** nella casella **Then** nell'ActivityDesigner **If** con il testo di suggerimento "Rilasciare l'attività".|  
  
## Vedere anche  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)