---
title: "Finestra di dialogo Definizione contenuto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Finestra di dialogo Definizione contenuto
La finestra di dialogo **Definizione del contenuto** viene utilizzata in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] per configurare le proprietà delle attività**Content**, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] le finestre di progettazione di attività che utilizzano questa casella, vedere gli argomenti di [Send](../workflow-designer/send-activity-designer.md), di [Receive](../workflow-designer/receive-activity-designer.md), di [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e di [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md).  
  
 Nella tabella seguente sono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Inizializza correlazione**.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|--------------------------------------|-----------------|  
|**Messaggio**|Consente di specificare il contenuto del messaggio con la casella di testo dell'espressione **Dati del messaggio** e il tipo mediante la casella di riepilogo a discesa **Tipo di messaggio**.Per impostazione predefinita, **Definizione contenuto** utilizza <xref:System.ServiceModel.Activities.ReceiveMessageContent>, che prevede un elemento <xref:System.ServiceModel.Channels.Message> o un tipo di contratto messaggio all'interno della definizione del servizio flusso di lavoro.|  
|**Parametri**|Fare clic sul pulsante di opzione **Parametri** per utilizzare <xref:System.ServiceModel.Activities.ReceiveParametersContent>, che prevede un contratto dati.Utilizzare la griglia dei dati per impostare una raccolta generica di coppie chiave\/valore <xref:System.Activities.OutArgument> i cui valori vengono assegnati ai parametri variabili nel flusso di lavoro corrente.|  
  
 La finestra di dialogo **Definizione contenuto** viene utilizzata nelle finestre di progettazione **Send**, **Receive**, **ReceiveAndSendReply** e **SendAndReceiveReply**.La procedura di accesso è simile per tutte le finestre. In questo esempio verrà utilizzata la finestra di progettazione Receive.  
  
 È possibile trascinare l'ActivityDesigner **Receive** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività.In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive.Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo \(contenuto\) relativo alla proprietà **Content** nella griglia delle proprietà per visualizzare la finestra di dialogo **Definizione contenuto**.  
  
 Il contenuto può essere specificato all'interno della sezione **Messaggio** per un'attività <xref:System.ServiceModel.Activities.ReceiveMessageContent> o all'interno della sezione **Parametro** per un'attività <xref:System.ServiceModel.Activities.ReceiveParametersContent>.  
  
## Vedere anche  
 [Guida dell'interfaccia utente della finestra di progettazione dei flussi di lavoro](../workflow-designer/workflow-designer-ui-help.md)