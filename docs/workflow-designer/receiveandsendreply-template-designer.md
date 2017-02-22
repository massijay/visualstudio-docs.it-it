---
title: "Finestra di progettazione del modello ReceiveAndSendReply | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Finestra di progettazione del modello ReceiveAndSendReply
Il modello **ReceiveAndSendReply** viene utilizzato per creare una coppia di attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> preconfigurate all'interno di un'attività <xref:System.Activities.Statements.Sequence>, correlate tra loro come parte di un modello di scambio di messaggi di richiesta\/risposta sul server.  
  
## Modello ReceiveAndSendReply  
 L'aggiunta di un modello **ReceiveAndSendReply** comporta l'esecuzione di tre operazioni, oltre alla creazione delle attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> con un'attività <xref:System.Activities.Statements.Sequence>:  
  
1.  Configurazione delle proprietà <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> dell'attività <xref:System.ServiceModel.Activities.Receive>.  
  
2.  Associazione della proprietà <xref:System.ServiceModel.Activities.SendReply.Request%2A> dell'attività <xref:System.ServiceModel.Activities.Receive> all'attività <xref:System.ServiceModel.Activities.Send>.  
  
3.  Creazione di un elemento <xref:System.ServiceModel.Activities.CorrelationHandle> come variabile nell'attività padre.  
  
### Utilizzo della finestra di progettazione del modello ReceiveAndSendReply  
 L'ActivityDesigner **ReceiveAndSendReply** è disponibile nella categoria **Messaggi** della **Casella degli strumenti**, accessibile facendo clic sulla scheda **Casella degli strumenti** in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]. In alternativa, scegliere **Barra degli strumenti** dal menu **Visualizza** o premere CTRL\+ALT\+X.  
  
 È possibile trascinare l'ActivityDesigner **ReceiveAndSendReply** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività.In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> configurabile con l'ActivityDesigner **Send** e un'attività correlata <xref:System.ServiceModel.Activities.SendReply> configurabile con la finestra di progettazione SendReplyToReceive.  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizzo della finestra di progettazione **Receive** per configurare l'attività <xref:System.ServiceModel.Activities.Receive>, vedere l'argomento [Receive](../workflow-designer/receive-activity-designer.md).  
  
 [!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizzo della finestra di progettazione **SendReplyToReceive** per configurare l'attività <xref:System.ServiceModel.Activities.SendReply>, vedere la sezione seguente.  
  
### Proprietà di SendReply  
 Nella tabella seguente sono elencate le proprietà di <xref:System.ServiceModel.Activities.SendReply> e ne viene descritta la modalità di utilizzo nella finestra di progettazione.Tali proprietà possono essere modificate nella griglia delle proprietà e, in alcuni casi, nell'area della finestra di progettazione di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome proprietà|Obbligatoria|Utilizzo|  
|--------------------|------------------|--------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nome descrittivo facoltativo dell'attività <xref:System.ServiceModel.Activities.SendReply>.Il valore predefinito è SendReplyToReceive.<br /><br /> Sebbene non sia obbligatorio specificare un valore non predefinito per la proprietà descrittiva <xref:System.Activities.Activity.DisplayName%2A>, è consigliabile farlo.|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|True|Riferimento all'attività <xref:System.ServiceModel.Activities.Receive> correlata a questa attività <xref:System.ServiceModel.Activities.SendReply>.Questa proprietà non deve essere **null**.Le attività <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> sono utilizzate insieme sul server per modellare un modello di messaggistica di richiesta\/risposta.Questa proprietà specifica quale attività <xref:System.ServiceModel.Activities.Send> viene associata.Nella finestra di progettazione non è possibile modificarla in quanto viene associata automaticamente all'attività <xref:System.ServiceModel.Activities.Send> dalla quale è stata creata l'attività <xref:System.ServiceModel.Activities.SendReply>.|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|False|Specifica il contenuto del messaggio o del parametro da ricevere.Può essere un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>.Modificare questa proprietà facendo clic sul pulsante con i puntini di sospensione accanto al campo **Content** nella griglia delle proprietà o facendo clic sul pulsante **Definisci** accanto all'etichetta **Content** nell'area dell'ActivityDesigner **Receive**.Entrambi visualizzano la finestra di dialogo **Definizione del contenuto** .[!INCLUDE[crabout](../test/includes/crabout_md.md)] come utilizzare questa casella, vedere l'argomento [Finestra di dialogo Definizione contenuto](../workflow-designer/content-definition-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|False|Specifica la raccolta di oggetti <xref:System.ServiceModel.Activities.CorrelationInitializer> che inizializzano più oggetti <xref:System.ServiceModel.Activities.CorrelationHandle> che configurano questa attività <xref:System.ServiceModel.Activities.Receive> all'interno del flusso di lavoro.Fare clic sul pulsante con i puntini di sospensione accanto alla proprietà <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> nella griglia delle proprietà per aprire la finestra di dialogo **Aggiungi inizializzatori di correlazione**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] utilizzo di questa casella, vedere l'argomento [Finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md).|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|False|Specifica l'intestazione Action del messaggio.Se non viene impostata esplicitamente, assume il valore predefinito:<br /><br /> **https:\/\/tempuri.org\/{spazio dei nomi contratto di servizio}\/{nome contratto di servizio}\/{nome operazione}**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|Specifica se l'istanza di servizio del flusso di lavoro deve essere salvata in modo permanente prima di inviare il messaggio di risposta.Il valore predefinito è **false**.|  
  
## Vedere anche  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)