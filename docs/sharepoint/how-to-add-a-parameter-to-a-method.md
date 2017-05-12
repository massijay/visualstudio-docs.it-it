---
title: "Procedura: aggiungere un parametro a un metodo"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di un metodo a un parametro"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], parametri di metodo"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], parametro"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di un metodo a un parametro"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], parametri di metodo"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], parametro"
ms.assetid: c5b6fd32-bf85-4b2a-a01e-f9199f0fb26e
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: aggiungere un parametro a un metodo
  Utilizzare un parametro per passare informazioni al metodo o restituire informazioni da un metodo.  Tutti i metodi devono avere almeno un parametro.  Per ulteriori informazioni sulla progettazione di un parametro per supportare il tipo di metodo che si desidera creare, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Quando si aggiunge un parametro a un metodo, in Visual Studio viene aggiunto l'elemento `<Parameter>` all'XML del file modello nel progetto.  Per ulteriori informazioni sugli attributi di un elemento `<Parameter>`, vedere [Parametro](http://go.microsoft.com/fwlink/?LinkId=169284).  
  
### Per aggiungere un parametro a un metodo  
  
1.  Aggiungere un metodo a un'entità.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Viene visualizzata la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Per ulteriori informazioni, vedere [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** espandere il nodo del metodo, quindi espandere il nodo **Parametri**.  
  
4.  Nell'elenco **Aggiungi un parametro**, scegliere **Crea parametro**.  
  
     Un nuovo parametro verrà visualizzato sotto il nodo **Parametri**.  
  
5.  Nella barra dei menu, scegliere **Visualizza**, **Finestra proprietà**.  
  
6.  Nel finestra **Proprietà** impostare la proprietà **Nome** su qualsiasi nome significativo.  Se, ad esempio, il metodo restituirà clienti, è possibile denominarlo GetCustomers.  
  
7.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** aprire l'elenco che viene visualizzato per la direzione del parametro, quindi selezionare **In**, **InOut**, **Out** o **Return**.  
  
     Per ulteriori informazioni sulla direzione che è opportuno scegliere per il metodo di tipo in fase di creazione, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
8.  Modificare il descrittore di tipo del parametro.  Per ulteriori informazioni, vedere [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## Vedere anche  
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  