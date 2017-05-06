---
title: "Procedura: creare un modello di integrazione applicativa dei dati"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creazione di un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creazione di un modello"
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: creare un modello di integrazione applicativa dei dati
  È possibile creare un modello di integrazione applicativa dei dati tramite il modello per tale tipo di elemento e quindi aggiungere il modello a qualsiasi progetto SharePoint.  Per ulteriori informazioni, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  Per ulteriori informazioni sulla progettazione del modello, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Per creare un progetto di integrazione applicativa dei dati  
  
1.  Nella barra dei menu, scegliere **File**, **Nuovo**, **Progetto**.  
  
    > [!NOTE]  
    >  Se l'IDE è configurato per utilizzare le impostazioni di sviluppo di Visual Basic, scegliere **Nuovo progetto** dal menu **File**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  In **Visual Basic** o **Visual C\#**, scegliere **Office\/SharePoint**, **Soluzioni di SharePoint**.  
  
3.  Nel riquadro **Modelli**, scegliere la voce **SharePoint 2013 – Progetto vuoto**, quindi fare clic sul pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
4.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** specificare l'URL di un sito di SharePoint nel computer locale, scegliere il pulsante di opzione **Distribuisci come soluzione farm**, quindi scegliere il pulsante **Fine**.  
  
     Verrà testato il modello sul sito SharePoint specificato.  
  
    > [!IMPORTANT]  
    >  È necessario distribuire il progetto come soluzione farm in quanto i modelli BDC supportano solo le soluzioni farm.  
  
     Un progetto SharePoint vuoto viene creato.  
  
5.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
6.  Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Office\/SharePoint**.  
  
7.  Nell'elenco di modelli di SharePoint scegliere **Modello di integrazione applicativa dei dati \(solo soluzioni farm\)**.  
  
8.  Nella casella **Nome** specificare un nome per il modello BDC, quindi scegliere il pulsante **Aggiungi**.  
  
     Un elemento **Modello di integrazione applicativa dei dati** verrà aggiunto al progetto.  Per impostazione predefinita, il modello viene visualizzato nella finestra di progettazione di integrazione applicativa dei dati.  Per ulteriori informazioni, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Vedere anche  
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  