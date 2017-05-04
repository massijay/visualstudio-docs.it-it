---
title: "Procedura: aggiungere un metodo Finder specifico | Microsoft Docs"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], ottenere un'entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], restituire un'entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Finder specifico"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], ottenere un'entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], restituire un'entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Finder specifico"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Procedura: aggiungere un metodo Finder specifico
  È possibile restituire una sola istanza di entità creando un metodo *Finder specifico*.  Il servizio di integrazione applicativa dei dati \(BDC\) esegue il metodo Finder specifico quando un utente sceglie un'entità in una Web part di integrazione applicativa dei dati o in un elenco esterno.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Per creare un metodo Finder specifico  
  
1.  Nella finestra di progettazione dell'integrazione applicativa dei dati, scegliere un'entità.  
  
     Per ulteriori informazioni riguardanti l'aggiunta di un'entità alla finestra di progettazione dell'integrazione applicativa dei dati in Visual Studio, vedere [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Viene visualizzata la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Per ulteriori informazioni su tale finestra, vedere [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nell'elenco di **Aggiungi un metodo**, scegliere **Crea metodo Finder specifico**.  
  
     In Visual Studio vengono aggiunti gli elementi seguenti al modello.  Questi elementi vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati**.  
  
    -   Metodo.  
  
    -   Parametro di input per il metodo.  
  
    -   Parametro restituito per il metodo.  
  
    -   Descrittore di tipo per ogni parametro.  
  
    -   Istanza di metodo per il metodo.  
  
     Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Aprire la finestra **Proprietà** di Visual Studio.  
  
5.  Configurare il descrittore di tipo del parametro restituito come descrittore di tipo di entità.  Per ulteriori informazioni su come creare un descrittore di tipo di entità, vedere [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Non è necessario eseguire questo passaggio se è stato aggiunto un metodo Finder all'entità.  In Visual Studio viene utilizzato il descrittore di tipo definito nel metodo Finder.  
  
    > [!NOTE]  
    >  Se il campo dell'identificatore del tipo di entità rappresenta un campo in una tabella del database generata automaticamente, impostare la proprietà **Sola lettura** del campo identificatore su **True**.  
  
6.  Nella finestra **Dettagli del metodo** scegliere l'istanza metodo del metodo.  
  
7.  Nella finestra **Proprietà** impostare la proprietà **Nome parametro restituito** sul nome del parametro restituito del metodo.  Per ulteriori informazioni sulle proprietà delle istanze di metodo, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  In **Esplora soluzioni**, aprire il menu di scelta rapida del file di codice servizio che è stato generato per l'entità, quindi scegliere **Visualizza codice**.  
  
     Il file di codice servizio dell'entità verrà aperto nell'editor di codice.  Per ulteriori informazioni sul file di codice servizio dell'entità, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Aggiungere codice al metodo Finder specifico.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Recuperare un record da dati di origine.  
  
    -   Restituisce un'entità al servizio di integrazione applicativa dei dati.  
  
     Nell'esempio seguente viene restituito un contatto dal database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  