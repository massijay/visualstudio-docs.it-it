---
title: "ActivityDesigner InitializeCorrelation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# ActivityDesigner InitializeCorrelation
L'ActivityDesigner **InitializeCorrelation** viene utilizzato per creare e configurare un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> che consente di stabilire una correlazione tra i messaggi prima del relativo invio o della relativa ricezione.  
  
## Attività InitializeCorrelation  
 Un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> viene utilizzata per inizializzare le correlazioni senza inviare o ricevere un messaggio.La correlazione viene in genere inizializzata quando si invia o riceve un messaggio.Se è necessario stabilire la correlazione prima che un messaggio venga inviato o ricevuto, utilizzare <xref:System.ServiceModel.Activities.InitializeCorrelation> per inizializzarla.  
  
### Utilizzo dell'ActivityDesigner InitializeCorrelation  
 L'ActivityDesigner **InitializeCorrelation** è disponibile nella categoria **Messaggi** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **InitializeCorrelation** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.InitializeCorrelation> con il valore <xref:System.Activities.Activity.DisplayName%2A> predefinito InitializeCorrelation.È possibile modificare il valore di <xref:System.Activities.Activity.DisplayName%2A> nell'intestazione dell'ActivityDesigner **InitializeCorrelation** o nella casella **DisplayName** della finestra **Proprietà**.  
  
 È possibile specificare <xref:System.ServiceModel.Activities.CorrelationHandle> nel campo **Correlation** della finestra **Proprietà** nell'area dell'ActivityDesigner **InitializeCorrelation**.  
  
 Fare clic sul pulsante con i puntini di sospensione accanto al campo **CorrelationData** nella finestra **Proprietà** o sul testo di suggerimento "Visualizza..." nell'area dell'ActivityDesigner **InitializeCorrelation** per visualizzare la finestra di dialogo **Inizializza correlazione**, in cui è possibile specificare l'handle della correlazione e le coppie chiave\-valore utilizzate per l'inizializzazione.[!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizzo di questa finestra di dialogo, vedere l'argomento [Finestra di dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md).  
  
### Proprietà di InitializeCorrelation  
 Nella tabella seguente vengono elencate le proprietà di <xref:System.ServiceModel.Activities.InitializeCorrelation> con una descrizione delle relative modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella finestra **Proprietà** o nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo dell'attività <xref:System.ServiceModel.Activities.InitializeCorrelation>.Il valore predefinito è InitializeCorrelation.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|<xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato per associare le attività del flusso di lavoro nella correlazione.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Dizionario dei dati di correlazione che mette in correlazione i messaggi all'istanza del flusso di lavoro.<br /><br /> Utilizzare la finestra di dialogo **Inizializza correlazione** per configurare <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizzo di questa finestra di dialogo, vedere l'argomento [Finestra di dialogo Editor raccolta di tipi](../workflow-designer/type-collection-editor-dialog-box.md).|  
  
## Vedere anche  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)