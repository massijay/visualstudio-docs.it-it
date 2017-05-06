---
title: "Procedura: aggiungere un&#39;entit&#224; al modello"
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
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di un'entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di un'entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], entità"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Procedura: aggiungere un&#39;entit&#224; al modello
  Per creare un'entità, aggiungere un controllo entità dalla **Casella degli strumenti** di Visual Studio nella finestra di progettazione dell'integrazione applicativa dei dati.  
  
### Per aggiungere un'entità al modello  
  
1.  Creare un progetto di integrazione applicativa dei dati o aprirne uno esistente.  Per ulteriori informazioni, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  Nella **Casella degli strumenti** trascinare una **Entità** dal gruppo **BusinessDataCatalog** alla finestra di progettazione.  
  
     La nuova entità verrà visualizzata nella finestra di progettazione.  In Visual Studio viene aggiunto un elemento `<Entity>` all'XML del file modello di integrazione applicativa dei dati nel progetto.  Per ulteriori informazioni sugli attributi di un elemento dell'entità, vedere [Entità](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  In progettazione, aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi**, quindi scegliere **Identificatore**.  
  
     Il nuovo identificatore verrà visualizzato nell'entità.  
  
    > [!NOTE]  
    >  È possibile modificare il nome dell'entità e l'identificatore nella finestra **Proprietà**.  
  
4.  Definire i campi dell'entità in una classe,  È possibile aggiungere una nuova classe al progetto o utilizzare una classe esistente creata tramite altri strumenti, ad esempio Progettazione relazionale oggetti.  Nell'esempio seguente viene illustrata una classe di entità denominata Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## Vedere anche  
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  