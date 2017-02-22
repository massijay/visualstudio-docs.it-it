---
title: "ActivityDesigner FinalState | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# ActivityDesigner FinalState
La finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> viene utilizzata per creare un <xref:System.Activities.Statements.State> che termina un'istanza della macchina a stati.  
  
## Utilizzo di ActivityDesigner FinalState  
 La finestra di progettazione **FinalState** viene utilizzata per creare un <xref:System.Activities.Statements.State> preconfigurato come stato finale in una macchina a stati.Un oggetto <xref:System.Activities.Statements.State> creato utilizzando l'ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> con la proprietà <xref:System.Activities.Statements.State.IsFinal%2A> impostata su **true** e nessuna attività <xref:System.Activities.Statements.State.Exit%2A> o nessuna transizione che abbia origine da essa.Per utilizzare un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> per aggiungere un'attività di <xref:System.Activities.Statements.State> preconfigurata come stato finale in una macchina a stati, trascinare un ActivityDesigner **FinalState** dalla sezione **Macchina a stati** della **Casella degli strumenti** e rilasciarlo nella Progettazione flussi di lavoro.Un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState> può essere rilasciato in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciato un ActivityDesigner di <xref:System.Activities.Core.Presentation.FinalState>.Per ulteriori informazioni sulla creazione delle transizioni, vedere [Transition](../workflow-designer/transition-activity-designer.md).  
  
### Proprietà dell'attività di stato nella finestra di progettazione del flusso di lavoro  
 Nella tabella seguente sono elencate le proprietà che possono essere impostate utilizzando la finestra di progettazione di <xref:System.Activities.Core.Presentation.FinalState> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.  
  
|Nome proprietà|Necessaria|Utilizzo|  
|--------------------|----------------|--------------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione.Il valore predefinito di **Stato**.Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<xref:System.Activities.Statements.State.DisplayName%2A> è utilizzato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato.Questo valore può essere impostato trascinando un'attività dalla **Casella degli strumenti** e rilasciandola nella sezione di <xref:System.Activities.Statements.State.Entry%2A> dello stato.|  
  
## Vedere anche  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)