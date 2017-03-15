---
title: "ActivityDesigner Pick | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Pick
Nell'attività <xref:System.Activities.Statements.Pick> è disponibile il flusso di controllo basato sugli eventi.L'attività esegue uno di diversi rami in risposta a un evento di attivazione.  
  
## Attività Pick  
 Un'attività <xref:System.Activities.Statements.Pick> contiene una raccolta di oggetti <xref:System.Activities.Statements.PickBranch>, uno dei quali può essere eseguito dall'attività <xref:System.Activities.Statements.Pick> per effetto di un evento in entrata che funge da trigger.In questo modo [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] consente la modellazione di un flusso di controllo basato sugli eventi.Ciascun oggetto <xref:System.Activities.Statements.PickBranch> contiene una proprietà <xref:System.Activities.Statements.PickBranch.Trigger%2A> e una proprietà <xref:System.Activities.Statements.PickBranch.Action%2A>.All'inizio dell'esecuzione di un'attività <xref:System.Activities.Statements.Pick>, tutte le attività del trigger degli elementi <xref:System.Activities.Statements.PickBranch> sono pianificate.Quando la prima attività viene completata, l'attività dell'azione corrispondente è pianificata e tutte le altre attività del trigger sono annullate.  
  
### Modalità di utilizzo dell'ActivityDesigner Pick  
 L'ActivityDesigner **Pick** è disponibile nella categoria **Flusso di controllo** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Pick** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un ActivityDesigner **Sequence**.Dopo averlo rilasciato in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], viene creata un'attività <xref:System.Activities.Statements.Pick> che per impostazione predefinita contiene due attività <xref:System.Activities.Statements.PickBranch> vuote come elementi i cui nomi visualizzati sono Branch1 e Branch2.I rispettivi valori della proprietà <xref:System.Activities.Statements.PickBranch.DisplayName%2A> possono essere modificati nell'intestazione dell'ActivityDesigner **PickBranch** o nella finestra **Proprietà** di ogni ramo.  
  
 Esistono due diverse modalità per aggiungere attività <xref:System.Activities.Statements.PickBranch> alla raccolta di un oggetto <xref:System.Activities.Statements.Pick>, ovvero mediante il trascinamento della finestra di progettazione **PickBranch** dalla **Casella degli strumenti** o mediante il menu di scelta rapida disponibile nell'area della finestra di progettazione **Pick**.Per informazioni dettagliate, vedere l'argomento [PickBranch](../workflow-designer/pickbranch-activity-designer.md).Si noti che l'unico elemento che può essere inserito in un ActivityDesigner **Pick** è un ActivityDesigner **PickBranch**.  
  
### Proprietà dell'attività di prelievo nella Progettazione flussi di lavoro  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Pick> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà o nell'area della finestra di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Consente di specificare il nome descrittivo dell'ActivityDesigner <xref:System.Activities.Statements.Pick> nell'intestazione.Il valore predefinito è Pick.Facoltativamente, è possibile modificare il valore nella griglia Proprietà o direttamente nell'intestazione dell'ActivityDesigner.<br /><br /> Sebbene la proprietà <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatoria, se ne consiglia l'utilizzo.|  
  
## Vedere anche  
 [Flusso di controllo](../workflow-designer/control-flow-activity-designers.md)   
 [Attività Pick](../Topic/Pick%20Activity.md)   
 [Utilizzo dell'attività Pick](../Topic/Using%20the%20Pick%20Activity.md)