---
title: "ActivityDesigner Assign | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Assign
L'ActivityDesigner **Assign** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Assign>.  
  
## Attività Assign  
 L'attività <xref:System.Activities.Statements.Assign> assegna un valore a una variabile o a un argomento.  
  
### Utilizzo dell'ActivityDesigner Assign  
 L'ActivityDesigner **Assign** è disponibile nella categoria **Primitive** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti**. In alternativa, è possibile scegliere **Casella degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Assign** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.Assign> con la proprietà **DisplayName** impostata sul valore predefinito Assign.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **Assign** o nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di Assign  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Assign> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.Activities.Statements.Assign>.L'impostazione predefinita è Assign.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.Assign.To%2A>|True|La variabile o l'argomento cui è assegnata la proprietà <xref:System.Activities.Statements.Assign.Value%2A>.È necessario che sia un identificativo valido di Visual Basic.Per impostare la proprietà, digitare un'espressione Visual Basic nella casella **To** dell'ActivityDesigner **Assign** o nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.Assign.Value%2A>|True|Valore assegnato alla variabile.Per impostare la proprietà <xref:System.Activities.Statements.Assign.Value%2A>, digitare un'espressione Visual Basic nella casella **Value** nell'ActivityDesigner **Assign** o nella griglia delle proprietà.|  
  
## Vedere anche  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)