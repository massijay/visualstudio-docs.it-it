---
title: "Procedura: aggiungere un metodo Creator"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di istanze di entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Creator"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiunta di istanze di entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Creator"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Procedura: aggiungere un metodo Creator
  Un metodo Creator consente di aggiungere nuovi dati all'origine dati di un'entità.  Il servizio di integrazione applicativa dei dati chiama questo metodo quando gli utenti scelgono il pulsante **Nuovo elemento** sulla barra multifunzione di un elenco basato sul modello.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Per aggiungere un metodo Creator  
  
1.  Nella finestra di progettazione dell'integrazione applicativa dei dati, scegliere un'entità.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Verrà visualizzata la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Per ulteriori informazioni su tale finestra, vedere [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nell'elenco **Aggiungi un metodo**, scegliere **Crea metodo Creatore**.  
  
     In Visual Studio vengono aggiunti gli elementi seguenti al modello e questi elementi vengono visualizzati nella finestra **Dettagli metodo BDC**.  
  
    -   Metodo denominato **Create**.  
  
    -   Parametro di input per il metodo.  
  
    -   Parametro restituito per il metodo.  
  
    -   Descrittori di tipo per i parametri.  
  
    -   Istanza di metodo per il metodo.  
  
     Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  In **Esplora soluzioni**, aprire il menu di scelta rapida del file di codice servizio che è stato generato per l'entità, quindi scegliere **Visualizza codice**.  
  
     Il file di codice servizio dell'entità verrà aperto nell'editor di codice.  Per ulteriori informazioni sul file di codice servizio dell'entità, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Aggiungere codice al metodo Creator per aggiungere dati all'origine dati.  Nell'esempio seguente viene aggiunto un contatto al database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  