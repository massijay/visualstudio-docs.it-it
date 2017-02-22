---
title: "ActivityDesigner CompensableActivity | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CompensableActivity.UI"
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner CompensableActivity
L'ActivityDesigner **CompensableActivity** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.CompensableActivity>.  
  
## Attività CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> definisce un'unità di lavoro che può essere confermata o compensata dopo l'esito positivo del completamento.  
  
### Utilizzo dell'ActivityDesigner CompensableActivity  
 L'ActivityDesigner **CompensableActivity** è disponibile nella categoria **Transazione** della **Casella degli strumenti**, a cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** a sinistra della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere la combinazione CTRL\+ALT\+X.  
  
 L'ActivityDesigner **CompensableActivity** può essere trascinato dalla **Casella degli strumenti** e rilasciato nel punto in cui vengono in genere posizionate le attività nell'area della [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], , ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.CompensableActivity> con un elemento <xref:System.Activities.Activity.DisplayName%2A> predefinito di CompensableActivity.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **CompensableActivity** o nella casella**DisplayName** della griglia delle proprietà.  
  
### Proprietà di CompensableActivity  
 Nella tabella seguente sono elencate le proprietà di <xref:System.Activities.Statements.CompensableActivity> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.È possibile modificare le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Activity%601.Result%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CompensableActivity>.Il valore predefinito è CompensableActivity.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Specifica il valore restituito di <xref:System.Activities.Statements.CompensableActivity>.Questa proprietà deve essere modificata nella griglia delle proprietà.|  
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di compensazione, di annullamento e di conferma.Per aggiungere l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>, rilasciare un'attività dalla **Casella degli strumenti** nella casella **Body** dell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Specifica l'attività eseguita in caso di annullamento.Per aggiungere l'attività, rilasciarne la finestra di progettazione dalla **Casella degli strumenti** nella casella **CancellationHandler** dell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Specifica l'attività da eseguire quando si esegue la compensazione per l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>.È possibile richiamare questo gestore in modo esplicito utilizzando l'attività <xref:System.Activities.Statements.Compensate>.<br /><br /> Per aggiungere l'attività, rilasciarne la finestra di progettazione dalla **Casella degli strumenti** nella casella **CompensationHandler** dell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Specifica l'attività da eseguire quando si conferma l'attività <xref:System.Activities.Statements.CompensableActivity.Body%2A>.È possibile richiamare questo gestore in modo esplicito utilizzando l'attività <xref:System.Activities.Statements.Confirm>.<br /><br /> Per aggiungere l'attività, rilasciarne la finestra di progettazione dalla **Casella degli strumenti** nella casella **ConfirmationHandler** dell'ActivityDesigner **CompensableActivity** con il testo di suggerimento "Rilasciare l'attività".|  
  
## Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)