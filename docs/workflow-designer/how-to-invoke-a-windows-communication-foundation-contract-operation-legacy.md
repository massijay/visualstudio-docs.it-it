---
title: "Procedura: richiamare un&#39;operazione del contratto Windows Communication Foundation (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: richiamare un&#39;operazione del contratto Windows Communication Foundation (legacy)
In questo argomento viene descritto come richiamare un'operazione di contratto [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Dopo avere trascinato un'attività **SendActivity** dalla casella degli strumenti all'area di progettazione del flusso di lavoro, è necessario importare un contratto esistente e determinare quale operazione verrà richiamata dall'attività **SendActivity**.È possibile selezionare il contratto e le relative operazioni tramite la [Finestra di dialogo Seleziona operazione \(legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Se con il servizio si sta utilizzando un file di configurazione, sarà inoltre necessario specificare un elemento <xref:System.Workflow.Activities.ChannelToken>.<xref:System.Workflow.Activities.ChannelToken> identifica la configurazione dell'endpoint che l'attività di trasmissione utilizzerà per connettersi al servizio del flusso di lavoro.  
  
### Per richiamare un'operazione di contratto WCF da un'attività SendActivity  
  
1.  Fare doppio clic sull'attività  **SendActivity** nella finestra di progettazione o fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **ServiceOperationInfo** nel riquadro **Proprietà**.  
  
2.  Quando viene visualizzata la finestra di dialogo **Seleziona operazione**, fare clic su **Importa** nell'angolo in alto a destra della finestra di dialogo.  
  
     Viene aperta la [Finestra di dialogo Cerca e seleziona un tipo .NET \(legacy\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).  
  
3.  Cercare un assembly o un progetto contenente il contratto desiderato.  
  
4.  Selezionare il contratto e fare clic su **OK**.  
  
5.  In **Operazioni disponibili** selezionare l'operazione che si desidera richiamare e fare clic **su OK**.  
  
### Per specificare un token del canale  
  
1.  Selezionare l'attività <xref:System.Workflow.Activities.SendActivity> nella finestra di progettazione.  
  
2.  Nel riquadro **Proprietà**, specificare un nome per <xref:System.Workflow.Activities.ChannelToken>.Questo nome identifica in modo univoco il token del canale.  
  
3.  Espandere il nodo del token del canale e specificare un nome per l'endpoint client che si desidera utilizzare nel campo <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>.La configurazione di endpoint con lo stesso nome nel file di configurazione verrà utilizzata per configurare il canale.  
  
4.  Creare la configurazione dell'endpoint nel file di configurazione, se non esiste già.Per ulteriori informazioni sulla configurazione del client, vedere [Panoramica dei client WCF](../Topic/WCF%20Client%20Overview.md).  
  
## Vedere anche  
 [Finestra di dialogo Seleziona operazione \(legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procedura: implementare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)