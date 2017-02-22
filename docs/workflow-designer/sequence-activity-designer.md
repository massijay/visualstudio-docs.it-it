---
title: "ActivityDesigner Sequence | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Sequence
L'attività <xref:System.Activities.Statements.Sequence> contiene una raccolta ordinata di attività figlio eseguite nell'ordine.  
  
 Un altro sistema per eseguire un set delle attività nell'ordine consiste nell'utilizzare un'attività <xref:System.Activities.Statements.Flowchart>.Utilizzare [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md) quando si dispone di un flusso semplice di programma per la creazione di rami e cicli da modellare graficamente.  
  
## Utilizzo dell'ActivityDesigner Sequence  
 Per aggiungere un'attività <xref:System.Activities.Statements.Sequence>, trascinare l'ActivityDesigner **Sequence** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].Per aggiungere un'attività figlio a questa attività <xref:System.Activities.Statements.Sequence>, trascinare un'altra attività dalla **Casella degli strumenti** e rilasciarla sul triangolo nella casella con il testo di suggerimento "Rilasciare l'attività".  
  
### Proprietà dell'attività della sequenza nella finestra di progettazione del flusso di lavoro  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Sequence> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Specifica il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Sequence> nell'intestazione.Il valore predefinito è Sequence.Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
  
## Vedere anche  
 [Diagramma di flusso](../workflow-designer/flowchart-activity-designer.md)   
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)