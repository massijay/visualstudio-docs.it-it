---
title: "ActivityDesigner Confirm | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Confirm.UI"
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner Confirm
L'ActivityDesigner **Confirm** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.Confirm>.  
  
## Attività Confirm  
 L'attività <xref:System.Activities.Statements.Confirm> richiama in modo esplicito <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> per un'attività inclusa in un'attività <xref:System.Activities.Statements.CompensableActivity>.Se l'attività <xref:System.Activities.Statements.Confirm> non viene utilizzata in un'attività <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> o <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> appartenente a un'attività <xref:System.Activities.Statements.CompensableActivity>, è necessario specificare la proprietà <xref:System.Activities.Statements.Confirm.Target%2A>.  
  
 L'oggetto <xref:System.Activities.Statements.CompensationToken> specificato da <xref:System.Activities.Statements.Compensate.Target%2A> consente di confermare o compensare esplicitamente un oggetto <xref:System.Activities.Statements.CompensableActivity> dopo che è stata completata l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A> appartenente all'attività <xref:System.Activities.Statements.CompensableActivity>.  
  
### Utilizzo dell'ActivityDesigner Confirm  
 L'ActivityDesigner **Confirm** è disponibile nella categoria **Transazione** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** nella parte sinistra di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **Confirm** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.Confirm> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Confirm.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesign **Confirm** oppure nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di Confirm  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.Confirm> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.La proprietà <xref:System.Activities.Activity.DisplayName%2A> può essere modificata nella griglia delle proprietà o nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], mentre la proprietà <xref:System.Activities.Statements.Confirm.Target%2A> deve essere modificata nella griglia delle proprietà.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Consente di specificare il nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>.L'impostazione predefinita è Confirm.|  
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Consente di specificare l'oggetto <xref:System.Activities.InArgument%601> che contiene l'oggetto <xref:System.Activities.Statements.CompensationToken> per questa attività <xref:System.Activities.Statements.Confirm>.|  
  
## Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)