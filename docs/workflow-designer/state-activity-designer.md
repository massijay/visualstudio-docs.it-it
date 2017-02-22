---
title: "ActivityDesigner State | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "sdanie"
manager: "erikre"
---
# ActivityDesigner State
Un oggetto <xref:System.Activities.Statements.State> rappresenta uno stato in cui può trovarsi una macchina a stati.  
  
## Utilizzo della Finestra di progettazione di stato.  
 Per aggiungere un oggetto <xref:System.Activities.Statements.State> a un flusso di lavoro, trascinare l'ActivityDesigner **Stato** dalla sezione **Macchina a stati** della **Casella degli strumenti** e rilasciarlo su un'attività <xref:System.Activities.Statements.StateMachine> nell'area di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Un'attività di <xref:System.Activities.Statements.State> può essere rilasciata in <xref:System.Activities.Statements.StateMachine> e le transizioni possono essere aggiunte successivamente, o una transizione può essere creata quando viene rilasciata un'attività di <xref:System.Activities.Statements.State>.Per aggiungere un'attività di <xref:System.Activities.Statements.State> e creare una transizione in un passaggio, trascinare un'attività **Stato** dalla sezione **Macchina a stati** della **Casella degli strumenti** e passarla su un altro stato in Progettazione flussi di lavoro.Quando l'oggetto <xref:System.Activities.Statements.State> trascinato si trova su un altro oggetto <xref:System.Activities.Statements.State>, intorno a quest'ultimo verranno visualizzati quattro triangoli.Se l'oggetto <xref:System.Activities.Statements.State> viene rilasciato su uno dei quattro triangoli, viene aggiunto alla macchina a stati e una transizione viene creata dall'oggetto <xref:System.Activities.Statements.State> di origine all'oggetto <xref:System.Activities.Statements.State> di destinazione rilasciato.Per ulteriori informazioni, vedere [Transition](../workflow-designer/transition-activity-designer.md).  
  
### Proprietà dell'attività di stato nella finestra di progettazione del flusso di lavoro  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.State> che possono essere impostate utilizzando la progettazione flussi di lavoro e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Alcune di queste proprietà possono essere modificate nella griglia delle proprietà, mentre altre possono essere modificate nell'area di progettazione.  
  
|Nome proprietà|Necessaria|Utilizzo|  
|--------------------|----------------|--------------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.State> nell'intestazione.Il valore predefinito di **Stato**.Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<xref:System.Activities.Statements.State.DisplayName%2A> è utilizzato per l'esplorazione tramite la barra di navigazione visualizzata nella parte superiore della Progettazione flussi di lavoro.<br /><br /> Sebbene la proprietà <xref:System.Activities.Statements.State.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Specifica l'azione che si verifica quando viene eseguita la transizione di questo stato.Quando l'attività <xref:System.Activities.Statements.State> viene espansa, questo valore può essere impostato trascinando un'attività da **Casella degli strumenti** e rilasciandola nella sezione **Voce** dello stato.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Specifica l'azione che si verifica quando viene eseguita la transizione da questo stato.Quando l'attività <xref:System.Activities.Statements.State> viene espansa, questo valore può essere impostato trascinando un'attività da **Casella degli strumenti** e rilasciandola nella sezione **Esci** dello stato.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Vengono elencate le transizioni possibili originate da <xref:System.Activities.Statements.State>.Ogni elemento nell'elenco ha un collegamento a <xref:System.Activities.Statements.Transition> collegato e a <xref:System.Activities.Statements.State> di destinazione.Una volta fatto clic sul collegamento la finestra di progettazione passerà a una visualizzazione estesa di <xref:System.Activities.Statements.Transition> o di <xref:System.Activities.Statements.State>.|  
  
## Vedere anche  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)