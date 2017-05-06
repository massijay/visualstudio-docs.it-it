---
title: "Procedura: definire un&#39;istanza di metodo"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], metodo"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], istanza di metodo"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], metodo"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], istanza di metodo"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: definire un&#39;istanza di metodo
  È necessario definire almeno un'istanza di metodo per ogni metodo contenuto nel modello.  
  
 Aggiungere un'istanza di metodo tramite la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Quando si aggiunge un'istanza di metodo, in Visual Studio viene aggiunto un elemento `<MethodInstance>` all'XML del file modello incluso nel progetto.  Per ulteriori informazioni sugli attributi di un elemento `<MethodInstance>`, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### Per definire un'istanza di metodo  
  
1.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** espandere il nodo di un metodo, quindi espandere il nodo **Istanze**.  
  
2.  Nell'elenco a discesa **Aggiungi istanza metodo**, selezionare **Crea istanza Finder**.  
  
     Sotto il nodo **Istanze** verrà visualizzata una nuova istanza di metodo.  
  
3.  Nella barra dei menu, scegliere **Visualizza**, selezionare **Finestra proprietà**.  
  
4.  Nel finestra **Proprietà** impostare le proprietà dell'istanza di metodo.  Per ulteriori informazioni su ogni proprietà, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## Vedere anche  
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  