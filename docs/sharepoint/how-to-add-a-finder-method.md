---
title: "Procedura: aggiungere un metodo Finder | Microsoft Docs"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Finder (metodo)"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], ottenere entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], restituire entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Finder (metodo)"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], ottenere entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], restituire entità"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Procedura: aggiungere un metodo Finder
  Per consentire al servizio di integrazione applicativa dei dati di visualizzare un elenco di entità in una web part o in un elenco, è necessario creare un metodo *Finder*.  Un metodo Finder è un metodo particolare che restituisce una raccolta di istanze di entità.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Per creare un metodo Finder  
  
1.  Nella finestra di progettazione dell'integrazione applicativa dei dati, scegliere un'entità.  
  
     Per ulteriori informazioni, vedere [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Verrà visualizzata la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Per ulteriori informazioni sulla finestra **Dettagli metodo di integrazione applicativa dei dati**, vedere [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nell'elenco **Aggiungi un metodo**, scegliere **Crea metodo Trovatore**.  
  
     In Visual Studio verranno aggiunti automaticamente un metodo, un parametro restituito e un descrittore di tipo.  
  
4.  Configurare il descrittore di tipo come descrittore di tipo della raccolta di entità.  Per ulteriori informazioni su come creare un descrittore di tipo della raccolta di entità, vedere [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  Non è necessario eseguire questo passaggio se è stato aggiunto un metodo Finder specifico all'entità.  In Visual Studio viene utilizzato il descrittore di tipo definito nel metodo Finder specifico.  
  
5.  In **Esplora soluzioni**, aprire il menu di scelta rapida del file di codice servizio che è stato generato per l'entità, quindi scegliere **Visualizza codice**.  Per ulteriori informazioni sul file di codice servizio, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Aggiungere codice al metodo Finder.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Recupero di dati da un'origine dati.  
  
    -   Restituzione di un elenco di entità al servizio di integrazione applicativa dei dati.  
  
     Nell'esempio seguente viene restituita una raccolta di entità `Contact` tramite dati dal database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Vedere anche  
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  