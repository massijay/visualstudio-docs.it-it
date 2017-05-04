---
title: "Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], importare un modello"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], rimuovere un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], importare un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], riutilizzare un modello"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint
  È possibile personalizzare, assemblare e ridistribuire un modello Business Data connectivity \(BDC\) tramite Visual Studio per aggiungere il file modello \(.bdcm\) a qualsiasi progetto farm di SharePoint.  Per ulteriori informazioni, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### Per aggiungere un file di modello BDC ad un progetto SharePoint  
  
1.  In **Esplora soluzioni**, scegliere la cartella di un progetto SharePoint.  
  
2.  Sulla barra dei menu, scegliere **Progetto**, **Aggiungi elemento esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi elemento esistente**, individuare il percorso del file di definizione del modello che si desidera aggiungere al progetto, selezionare il file, quindi selezionare il pulsante **Aggiungi**.  
  
     Se il modello non definisce un *Sistema Line of Business \(LOB\) di tipo .NET assembly*, verrà aperta la finestra di dialogo **Aggiungi .NET assembly LobSystem**.  
  
4.  Se viene visualizzata la finestra di dialogo, eseguire una delle seguenti operazioni:  
  
    -   Se si desidera scrivere codice personalizzato e viene utilizzata una finestra di progettazione per definire i metadati per il modello importato, selezionerà il pulsante **Sì**, denominare il sistema e quindi scegliere il pulsante **OK**.  
  
    -   Altrimenti, selezionare il pulsante **No**, quindi fare clic sul pulsante **OK**.  
  
     L'elemento **Modello di integrazione applicativa dei dati** verrà aggiunto al progetto.  
  
## Vedere anche  
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  