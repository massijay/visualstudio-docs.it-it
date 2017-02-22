---
title: "ActivityDesigner TransactedReceiveScope | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ActivityDesigner TransactedReceiveScope
L'ActivityDesigner **TransactedReceiveScope** viene utilizzato per creare e configurare un'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
## Attività TransactedReceiveScope  
 L'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> consente di propagare una transazione in transazioni server create da un flusso di lavoro o da un dispatcher.  
  
### Utilizzo dell'ActivityDesigner TransactedReceiveScope  
 L'ActivityDesigner **TransactedReceiveScope** è disponibile nella categoria **Messaggi** della **Casella degli strumenti**, cui è possibile accedere facendo clic sulla scheda **Casella degli strumenti** in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, è possibile scegliere **Barra degli strumenti** dal menu **Visualizza** oppure premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **TransactedReceiveScope** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività.In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope> con la proprietà **DisplayName** impostata sul valore predefinito TransactedReceiveScope.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **TransactedReceiveScope** o nella casella **DisplayName** della griglia delle proprietà.  
  
 La finestra di progettazione **TransactedReceiveScope** include le caselle **Request** e **Body**.Tali caselle consentono di configurare la proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> che specifica un'attività <xref:System.ServiceModel.Activities.Receive> e una proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> che specifica un'altra <xref:System.Activities.Activity>.La proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> crea una transazione.La transazione viene quindi resa ambiente per l'ambito della proprietà <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> in modo che qualsiasi attività interna a questo ambito venga eseguita in questa transazione.  
  
### Proprietà di TransactedReceiveScope  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.ServiceModel.Activities.TransactedReceiveScope> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà di <xref:System.Activities.Activity.DisplayName%2A> possono essere modificate nella griglia delle proprietà oppure nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], mentre le altre devono essere modificate nell'area di progettazione.  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.TransactedReceiveScope>.Il valore predefinito è TransactedReceiveScope.<br /><br /> Sebbene il nome di <xref:System.Activities.Activity.DisplayName%2A> non sia obbligatorio, se ne consiglia l'utilizzo.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Elimina un'attività <xref:System.ServiceModel.Activities.Receive> nel blocco **Request** nell'area di progettazione dell'attività.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Elimina un'attività <xref:System.Activities.Activity> nel blocco **Body** nell'area di progettazione dell'attività.|  
  
## Vedere anche  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)