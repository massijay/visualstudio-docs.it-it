---
title: "Finestra di dialogo Definizione di CorrelatesOn | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CorrelatesOnDefinition.UI"
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Finestra di dialogo Definizione di CorrelatesOn
La finestra di dialogo **CorrelatesOn** viene utilizzata in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] per modificare la proprietà <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> di un'attività <xref:System.ServiceModel.Activities.Receive>.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)] l'argomento [Receive](../workflow-designer/receive-activity-designer.md).  
  
 La correlazione tra le attività <xref:System.ServiceModel.Activities.Receive> specifica come operazioni del servizio diverse si connettono tra loro in un flusso di lavoro.  
  
 Nella tabella seguente vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **CorrelatesOn**.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|--------------------------------------|-----------------|  
|**CorrelatesWith**|Oggetto <xref:System.ServiceModel.Activities.CorrelationHandle> utilizzato per indirizzare il messaggio all'istanza del flusso di lavoro appropriata.|  
|**Query XPath**|Una coppia chiave\/valore che contiene le query utilizzate per estrarre dati di correlazione dai messaggi in ingresso.Questa proprietà corrisponde alla proprietà <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>.Le query XPath sono incluse in un oggetto <xref:System.ServiceModel.MessageQuerySet>.|  
  
## Per aprire la finestra di dialogo CorrelatesOn.  
 È possibile trascinare l'ActivityDesigner **Receive** dalla **Casella degli strumenti** e rilasciarlo nell'area di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], nel punto in cui vengono in genere posizionate le attività.In questo modo viene creata un'attività <xref:System.ServiceModel.Activities.Receive> con la proprietà <xref:System.Activities.Activity.DisplayName%2A> impostata sul valore predefinito Receive.Selezionare l'ActivityDesigner **Receive** e fare clic sul pulsante con i puntini di sospensione accanto al testo \(raccolta\) relativo alla proprietà **CorrelatesOn** nella griglia delle proprietà per visualizzare la finestra di dialogo **Definizione di CorrelatesOn**.  
  
## Vedere anche  
 <xref:System.ServiceModel.Activities.Receive>   
 [Finestra di dialogo Aggiungi inizializzatori di correlazione](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Add Correlation Dialog Box](http://msdn.microsoft.com/it-it/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Finestra di dialogo Inizializza correlazione](../workflow-designer/initialize-correlation-dialog-box.md)