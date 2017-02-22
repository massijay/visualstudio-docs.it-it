---
title: "ActivityDesigner TerminateWorkflow | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner TerminateWorkflow
L'ActivityDesigner **TerminateWorkflow** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.TerminateWorkflow>.  
  
## Attività TerminateWorkflow  
 L'attività <xref:System.Activities.Statements.TerminateWorkflow> termina l'esecuzione di un flusso di lavoro.  
  
### Utilizzo dell'ActivityDesigner TerminateWorkflow  
 L'ActivityDesigner **TerminateWorkflow** è disponibile nella categoria **Runtime** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti**. In alternativa, scegliere **Casella degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **TerminateWorkflow** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.TerminateWorkflow> con una proprietà **DisplayName** predefinita TerminateWorkflow.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **TerminateWorkflow** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di TerminateWorkflow  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.TerminateWorkflow> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.TerminateWorkflow>.Il valore predefinito è TerminateWorkflow.Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'utilizzo.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|Eccezione da generare quando viene terminato il flusso di lavoro.Questa proprietà viene impostata nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|Motivo che spiega perché è stato terminato il flusso di lavoro.Questa proprietà viene impostata nella griglia delle proprietà.|  
  
## Vedere anche  
 [Runtime](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)