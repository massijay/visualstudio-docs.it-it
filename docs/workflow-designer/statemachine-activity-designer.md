---
title: "ActivityDesigner StateMachine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "StateMachine Designer"
  - "System.Activities.Statements.StateMachine.UI"
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityDesigner StateMachine
L'attività <xref:System.Activities.Statements.StateMachine> contiene una raccolta di stati e modella i flussi di lavoro utilizzando il paradigma comune della macchina a stati.  
  
## Utilizzo dell'ActivityDesigner StateMachine  
 Per aggiungere un'attività <xref:System.Activities.Statements.StateMachine>, trascinare l'ActivityDesigner **StateMachine** dalla sezione **Macchina a stati** della **Casella degli strumenti** e rilasciarla nell'area di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Per aggiungere uno stato figlio a questa attività <xref:System.Activities.Statements.StateMachine>, trascinare un <xref:System.Activities.Statements.State> o <xref:System.Activities.Core.Presentation.FinalState> dalla **Casella degli strumenti** e rilasciarlo in **StateMachine**.  
  
### Proprietà dell'attività StateMachine in Progettazione flussi di lavoro  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.StateMachine> che possono essere impostate utilizzando la progettazione flussi di lavoro e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione.  
  
|Nome proprietà|Necessaria|Utilizzo|  
|--------------------|----------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.StateMachine> nell'intestazione.Il valore predefinito è **StateMachine**.Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<xref:System.Activities.Activity.DisplayName%2A> è utilizzato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
  
## Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)