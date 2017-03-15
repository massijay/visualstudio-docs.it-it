---
title: "Finestra di dialogo Aggiungi inizializzatori di correlazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "AddCorrelationInitializers.UI"
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Finestra di dialogo Aggiungi inizializzatori di correlazione
La finestra di dialogo **Aggiungi inizializzatori di correlazione** viene utilizzata in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] per configurare le proprietà delle attività **CorrelationInitializers**, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> e <xref:System.ServiceModel.Activities.ReceiveReply>.[!INCLUDE[crabout](../test/includes/crabout_md.md)] le finestre di progettazione di attività che utilizzano questa casella, vedere gli argomenti di [Send](../workflow-designer/send-activity-designer.md), di [Receive](../workflow-designer/receive-activity-designer.md), di [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)e di [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) .  
  
 Gli inizializzatori di correlazione della raccolta specificata con questa finestra di dialogo possono inizializzare correlazioni tra le attività di messaggistica basate su query, di contesto, di contesto di callback o correlazioni richiesta\-risposta.  
  
 Nella tabella seguente sono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Aggiungi inizializzatori di correlazione**.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|--------------------------------------|-----------------|  
|**Aggiungi inizializzatore**|Fare clic sulla casella **Aggiungi inizializzatore** per aggiungere un ulteriore inizializzatore alla raccolta.|  
|**Tipo di correlazione**|Consente di specificare il tipo di inizializzatore di correlazione.Sono disponibili quattro tipi:<br /><br /> 1.  Un inizializzatore di correlazione di callback che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.<br />2.  Un inizializzatore di correlazione di contesto che consente di specificare un oggetto <xref:System.ServiceModel.Activities.CorrelationInitializer>.<br />3.  Un inizializzatore di correlazione richiesta\-risposta che consente di specificare un oggetto <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>.<br />4.  Un inizializzatore di correlazione query che consente di specificare un oggetto <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.<br /><br /> Per modificare il **Tipo di correlazione**<br /><br /> 1.  Passare alla riga specifica nel DataGrid di **Aggiungi inizializzatore**.<br />2.  Premere CTRL \+ TAB per spostare lo stato attivo su **CorrelationTypeComboBox**<br />3.  Premere ALT\+freccia GIÙ per aprire l'elemento **ComboBox** e modificarlo.|  
|**Query XPath**|Una coppia chiave\/valore che contiene le query utilizzate per estrarre dati di correlazione dai messaggi in ingresso e in uscita.Questo elenco è valido solo in caso di utilizzo di tipi <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>.|  
  
## Per avviare la finestra di dialogo Aggiungi inizializzatori di correlazione  
 La finestra di dialogo **Aggiungi inizializzatori di correlazione** viene utilizzata nelle finestre di progettazione **Send**, **Receive**, **ReceiveAndSendReply** e **SendAndReceiveReply**.La procedura di accesso è simile per tutte le finestre. In questo esempio verrà utilizzata la finestra di progettazione **Receive**.  
  
 È possibile trascinare l'ActivityDesigner **Receive** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività.In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive.Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo \(raccolta\) relativo alla proprietà **CorrelationInitializers** nella griglia delle proprietà per visualizzare la finestra di dialogo **Aggiungi inizializzatore di correlazione**.  
  
## Vedere anche  
 [Add Correlation Dialog Box](http://msdn.microsoft.com/it-it/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)