---
title: "ActivityDesigner CancellationScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ActivityDesigner CancellationScope
L'ActivityDesigner **CancellationScope** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.CancellationScope>.  
  
## Attività CancellationScope  
 L'attività <xref:System.Activities.Statements.CancellationScope> consente di specificare un'attività per la relativa logica di esecuzione e di annullamento.  
  
### Utilizzo dell'ActivityDesigner CancellationScope  
 L'ActivityDesigner **CancellationScope**T è disponibile nella categoria **Transazione** della **Casella degli strumenti**, accessibile facendo clic sulla scheda [!INCLUDE[Casella degli strumentiwfd2 di]()]. In alternativa, scegliere **Barra degli strumenti** dal menu Visualizza o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **CancellationScope**T dalla [!INCLUDE[Casella degli strumentiwfd2 e rilasciarlo nell'area di]()]<xref:System.Activities.Statements.Sequence>, nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento.In questo modo viene creata un'attività <xref:System.Activities.Statements.CancellationScope> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito CancellationScope.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **CancellationScope**T o nella casella DisplayName della griglia delle proprietà.  
  
### Proprietà di CancellationScope  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.CancellationScope> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.È possibile modificare la proprietà <xref:System.Activities.Activity.DisplayName%2A> nella griglia delle proprietà ma le altre proprietà devono essere modificate nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.CancellationScope>.Il valore predefinito è CancellationScope.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Specifica l'attività per la quale viene fornita la logica di annullamento.Per aggiungere l'attività <xref:System.Activities.Statements.CancellationScope.Body%2A>, rilasciare un'attività dalla **Casella degli strumenti** nella casella **Body** dell'ActivityDesigner **CancellationScope** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Specifica l'attività eseguita in caso di annullamento.Per aggiungere l'attività <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>, rilasciare un'attività dalla **Casella degli strumenti** nella casella **CancellationHandler** dell'ActivityDesigner **CancellationScope** con il testo di suggerimento "Rilasciare l'attività".|  
  
## Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)