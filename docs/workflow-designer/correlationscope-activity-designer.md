---
title: "ActivityDesigner CorrelationScope | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ActivityDesigner CorrelationScope
L'ActivityDesigner **CorrelationScope** viene utilizzato per creare e configurare un'attività <xref:System.ServiceModel.Activities.CorrelationScope> che offre la gestione implicita di attività di messaggistica figlio mediante un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
## Attività CancellationScope  
 La proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> specifica l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato per gestire le attività di messaggistica figlio.Le attività <xref:System.ServiceModel.Activities.Send> e <xref:System.ServiceModel.Activities.Receive> contenute in <xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> sono configurate per utilizzare la proprietà <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> dell'attività <xref:System.ServiceModel.Activities.CorrelationScope> contenitore per eseguire la correlazione.  
  
### Utilizzo dell'ActivityDesigner CorrelationScope  
 L'ActivityDesigner **CorrelationScope** è disponibile nella categoria **Messaggistica** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** nella parte sinistra di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **CorrelationScope** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.CorrelationScope> con la proprietà **DisplayName** impostata sul valore predefinito CorrelationScope.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **CorrelationScope** oppure nella casella **DisplayName** della finestra **Proprietà**.  
  
 Per specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato dalle attività di messaggistica figlio, fare clic sul pulsante con i puntini di sospensione accanto al campo **CorrelatesWith** nella finestra **Proprietà** per visualizzare la finestra di dialogo **Editor espressioni**.È possibile impostare questa proprietà anche nell'area di progettazione dell'attività.  
  
 Le attività il cui ambito è all'interno della correlazione vengono specificate rilasciando le rispettive finestre di progettazione nella casella **Body** all'interno della finestra di progettazione **CorrelationScope**.  
  
### Proprietà di CancellationScope  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.ServiceModel.Activities.CorrelationScope> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.È possibile modificare queste proprietà nella finestra **Proprietà** o nell'area di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] e spesso in entrambe.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|False|Consente di specificare l'oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato per gestire le attività di messaggistica figlio.Se non si imposta questa proprietà, <xref:System.ServiceModel.Activities.CorrelationScope> crea automaticamente un oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> implicito.|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|False|Consente di specificare le attività all'interno dell'ambito della correlazione.|  
  
## Vedere anche  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)