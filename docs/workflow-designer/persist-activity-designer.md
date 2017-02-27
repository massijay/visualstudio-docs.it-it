---
title: "ActivityDesigner Persist | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ActivityDesigner Persist
L'ActivityDesigner **Persist** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Persist>.  
  
## Attività Persist  
 L'attività <xref:System.Activities.Statements.Persist> salva un flusso di lavoro su disco, se possibile.Non è possibile eseguire l'attività <xref:System.Activities.Statements.Persist> in un'area non permanente come, ad esempio, all'interno di un'attività <xref:System.Activities.Statements.TransactionScope>.Se si utilizza un'attività <xref:System.Activities.Statements.Persist> in un ambito non permanente, viene generata un'eccezione in fase di esecuzione.  
  
### Utilizzo dell'ActivityDesigner Persist  
 L'ActivityDesigner **Persist** è disponibile nella categoria **Runtime** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti**. In alternativa, è possibile scegliere **Casella degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Persist** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.Persist> con la proprietà **DisplayName** impostata sul valore predefinito Persist.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Persist** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di Persist  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Persist> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Persist>.Il valore predefinito è Persist.Sebbene il nome visualizzato non sia obbligatorio, se ne consiglia l'utilizzo.|  
  
## Vedere anche  
 [Runtime](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)