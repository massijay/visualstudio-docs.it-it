---
title: "Procedura: implementare un&#39;operazione del contratto di Windows Communication Foundation (legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Procedura: implementare un&#39;operazione del contratto di Windows Communication Foundation (legacy)
In questo argomento viene descritto come implementare un'operazione di contratto [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] utilizzando la [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] legacy che fa riferimento a [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] o [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Dopo avere trascinato un'attività **ReceiveActivity** dalla casella degli strumenti all'area di progettazione del flusso di lavoro, è necessario creare un nuovo contratto [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] o importare un contratto esistente e implementare le operazioni.È possibile selezionare e\/o creare il contratto e le relative operazioni tramite la [Finestra di dialogo Seleziona operazione \(legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### Per implementare un'operazione del contratto WCF  
  
1.  Fare doppio clic sull'attività **ReceiveActivity** nella finestra di progettazione o fare clic sul pulsante con i puntini di sospensione accanto alla proprietà **ServiceOperationInfo** nel riquadro **Proprietà**.  
  
2.  Eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Aggiungi contratto** nell'angolo in alto a destra della finestra di dialogo.Vengono creati un nuovo contratto e una nuova operazione [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)].  
  
         \-oppure\-  
  
    -   Fare clic su **Importa** nell'angolo in alto a destra della finestra di dialogo.Viene aperta la [Finestra di dialogo Cerca e seleziona un tipo .NET \(legacy\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).Cercare un assembly o un progetto contenente il contratto desiderato.Selezionare il contratto e fare clic su **OK**.  
  
     Dopo aver creato o importato un contratto, sarà possibile aggiungervi nuove operazioni.Per aggiungere una nuova operazione, selezionare il contratto e fare clic su **Aggiungi operazione** nell'angolo superiore destro della finestra di dialogo.Dopo aver inserito tutte le operazioni, andare al passaggio 3.  
  
3.  Selezionare l'operazione che si desidera associare all'attività **ReceiveActivity**.È possibile modificare la definizione dell'operazione modificando il nome, i parametri, le proprietà e le impostazioni relative alle autorizzazioni.  
  
     Per modificare il nome, immettere il nuovo nome nella casella di testo **Nome operazione**.  
  
     Fare clic sulla scheda **Parametri** per accedere ai parametri dell'operazione.È possibile modificare il nome, il tipo o la direzione di un parametro così come aggiungere o eliminare parametri dall'operazione.  
  
     Fare clic sulla scheda **Proprietà** per accedere al livello di protezione dell'operazione e alla funzionalità di scambio di messaggi supportata dell'operazione.  
  
     Fare clic sulla scheda **Autorizzazioni** per specificare quale gruppo è consentito implementare l'operazione.  
  
4.  Fare clic su **OK** e sull'attività **ReceiveActivity** per visualizzare il nome dell'operazione per l'operazione che sta implementando.  
  
5.  Posizionare le attività del flusso di lavoro che si desidera utilizzare per l'implementazione dell'operazione all'interno dell'attività **ReceiveActivity**.  
  
## Vedere anche  
 [Finestra di dialogo Seleziona operazione \(legacy\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Procedura: richiamare un'operazione del contratto WCF \(legacy\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Attività del flusso di lavoro legacy](../workflow-designer/legacy-workflow-activities.md)