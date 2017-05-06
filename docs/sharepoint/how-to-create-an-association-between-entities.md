---
title: "Procedura: creare un&#39;associazione tra entit&#224;"
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
  - "AssociationGroupTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associare tipi di contenuto esterno"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associazioni tra entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creare un'associazione"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], entità correlate"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associare tipi di contenuto esterno"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associazioni tra entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creare un'associazione"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], entità correlate"
ms.assetid: 0c095df8-1f40-4c4d-9fed-e125a8429724
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: creare un&#39;associazione tra entit&#224;
  È possibile definire relazioni tra entità nel modello di integrazione applicativa dei dati mediante la creazione di associazioni.  In Visual Studio vengono generati metodi che forniscono informazioni su ogni associazione agli utenti del modello.  Questi metodi possono essere utilizzati da web part di SharePoint, elenchi o applicazioni personalizzate per visualizzare relazioni dei dati in un'interfaccia utente.  
  
 È possibile creare due tipi di associazioni nella finestra di progettazione dell'integrazione applicativa dei dati: associazioni basate su chiave esterna e associazioni senza chiave esterna.  Per ulteriori informazioni, vedere [Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).  
  
### Per creare un'associazione tra entità  
  
1.  Nella scheda **BusinessDataConnectivity** della **Casella degli strumenti** scegliere l'elemento **Associazione**.  
  
2.  Nella finestra di progettazione dell'integrazione applicativa dei dati scegliere l'entità di origine, quindi l'entità di destinazione.  
  
     Verrà visualizzato l'**Editor di associazione**.  
  
3.  Se si desidera creare un'associazione basata su chiave esterna, selezionare la casella di controllo **Associazione chiave esterna**.  
  
    1.  Nella colonna **ID origine** della tabella **Mapping identificatori** selezionare l'identificatore accanto a ogni descrittore di tipo corrispondente visualizzato nella colonna **Campo**.  
  
         Nella colonna **ID origine**, ad esempio, selezionare `ContactID` accanto al descrittore di tipo e `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` e al descrittore di tipo `ReadItem.salesOrder.SalesOrder.ContactID`.  
  
4.  Se si desidera creare un'associazione senza chiave esterna, deselezionare la casella di controllo **Associazione chiave esterna**.  
  
5.  Fare clic sul pulsante **OK**.  
  
6.  Nella finestra di progettazione dell'integrazione applicativa dei dati verrà visualizzata una linea che rappresenta l'associazione tra l'entità di origine e l'entità di destinazione.  
  
     In Visual Studio viene aggiunto un metodo AssociationNavigator alla classe di servizio dell'entità di destinazione e a quella dell'entità di origine.  Per ulteriori informazioni sui metodi Association Navigation, vedere [Operazioni supportate](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  Nel metodo AssociationNavigator dell'entità di origine aggiungere codice che restituisca una raccolta di entità di destinazione.  
  
8.  Nel metodo AssociationNavigator dell'entità di destinazione aggiungere codice che restituisca l'entità di origine correlata.  
  
     Per alcuni esempi sull'utilizzo dei metodi di tipo AssociationNavigator, vedere [Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md).  
  
## Vedere anche  
 [Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
  
  