---
title: "ActivityDesigner TransactionScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ActivityDesigner TransactionScope
L'ActivityDesigner **TransactionScope** viene utilizzato per creare e configurare un'attività <xref:System.Activities.Statements.TransactionScope>.  
  
## Attività TransactionScope  
 L'attività <xref:System.Activities.Statements.TransactionScope> esegue in un'unica transazione l'attività contenuta.Il commit della transazione viene eseguito quando l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A> e tutti gli altri partecipanti della transazione sono stati completati correttamente.  
  
### Utilizzo dell'ActivityDesigner TransactionScope  
 L'ActivityDesigner **TransactionScope** è disponibile nella categoria **Transazione** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda a **Casella degli strumenti** di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **TransactionScope** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività, ad esempio all'interno di un elemento <xref:System.Activities.Statements.Sequence>.In questo modo viene creata un'attività <xref:System.Activities.Statements.TransactionScope> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito TransactionScope.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **TransactionScope** oppure nella casella **DisplayName** della griglia delle proprietà.  
  
### Proprietà di TransactionScope  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.Activities.Statements.TransactionScope> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Le proprietà <xref:System.Activities.Activity.DisplayName%2A> e <xref:System.Activities.Statements.TransactionScope.Body%2A> possono essere modificate nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Le altre proprietà devono invece essere modificate nella griglia delle proprietà.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.Activities.Statements.TransactionScope>.Il valore predefinito è TransactionScope.Sebbene non sia obbligatorio specificare il valore di <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|True|Consente di specificare l'attività da eseguire in un'unica transazione.Per aggiungere l'attività <xref:System.Activities.Statements.TransactionScope.Body%2A>, rilasciare un'attività dalla **Casella degli strumenti** nella casella **Body** dell'ActivityDesigner **TransactionScope** con il testo di suggerimento "Rilasciare l'attività".|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|Consente di specificare la proprietà <xref:System.Transactions.IsolationLevel> per questa attività <xref:System.Activities.Statements.TransactionScope>.|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|Consente di specificare l'intervallo di tempo \(nel formato 00:00:00, che indica ore:minuti:secondi\) disponibile per il completamento della transazione.Il valore predefinito è 1 minuto \(00:01:00\).|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|Specifica il valore che indica se il flusso di lavoro deve essere interrotto se la transazione si interrompe.|  
  
## Vedere anche  
 [Transazione](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)