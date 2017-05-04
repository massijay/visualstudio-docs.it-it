---
title: "Procedura: utilizzare un file di risorse per specificare nomi localizzati, propriet&#224; e autorizzazioni | Microsoft Docs"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], localizzare stringhe"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], proprietà"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], file di risorse"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], stringhe di risorse"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], localizzare stringhe"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], proprietà"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], file di risorse"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], stringhe di risorse"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Procedura: utilizzare un file di risorse per specificare nomi localizzati, propriet&#224; e autorizzazioni
  Utilizzando un file di risorse, è possibile fornire nomi localizzati, definire proprietà e applicare gli oggetti di autorizzazioni tor definiti in un modello Business Data connectivity \(BDC\).  Per specificare queste informazioni, aggiungere un **Elemento risorse di integrazione applicativa dei dati** a un progetto contenente un elemento **Modello di integrazione applicativa dei dati**.  Specificare nomi, proprietà e autorizzazioni modificando l'XML del file di risorse.  
  
### Per aggiungere un file di risorse di integrazione applicativa dei dati a un progetto SharePoint  
  
1.  In **Esplora soluzioni** espandere la cartella del progetto SharePoint, quindi selezionare la cartella contenente il modello di integrazione applicativa dei dati.  
  
2.  Sulla barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.  
  
3.  Espandere il nodo **SharePoint** quindi scegliere il nodo **2010**.  
  
4.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Elemento risorse di integrazione applicativa dei dati**.  
  
5.  Nella casella **Nome** digitare il nome del file di risorse, quindi scegliere **Aggiungi**.  
  
     Un file di risorse con estensione bdcr verrà aggiunto al progetto e aperto per la modifica.  
  
6.  Aggiungere XML per definire i nomi localizzati, le proprietà e le autorizzazioni che si desidera applicare il modello di integrazione applicativa dei dati.  
  
     Per informazioni su come definire questi elementi, vedere [Modello e file di risorse](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## Vedere anche  
 [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  