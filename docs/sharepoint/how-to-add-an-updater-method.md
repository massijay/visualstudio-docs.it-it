---
title: "Procedura: aggiungere un metodo Updater"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Updater"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiornamento di dati"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiornamento di istanze di entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], Updater"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiornamento di dati"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiornamento di istanze di entità"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Procedura: aggiungere un metodo Updater
  È possibile consentire agli utenti di aggiornare dettagli di integrazione applicativa dei dati in un elenco esterno di SharePoint mediante la creazione di un metodo *Updater*.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Per creare un metodo Updater  
  
1.  Nella finestra di progettazione dell'integrazione applicativa dei dati, scegliere un'entità.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Viene visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati  Per ulteriori informazioni su questa finestra, vedere [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  Nell'elenco **Aggiungi un metodo**, scegliere **Crea metodo Updater**.  
  
     In Visual Studio vengono aggiunti gli elementi seguenti al modello.  Questi elementi vengono visualizzati nella finestra Dettagli metodo di integrazione applicativa dei dati.  
  
    -   Un metodo denominato **Aggiorna**.  
  
    -   Parametro di input per il metodo.  
  
    -   Descrittore di tipo per il parametro.  Per impostazione predefinita, in Visual Studio viene utilizzato il descrittore di tipo relativo all'entità definito per il metodo Finder \(ad esempio, Contact\).  
  
    -   Istanza di metodo per il metodo.  
  
     Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Se l'identificatore del tipo di entità rappresenta un campo in una tabella di un database che non è generato automaticamente, impostare la proprietà **Campo Pre\-Updater** su **True**.  
  
4.  In **Esplora soluzioni**, aprire il menu di scelta rapida del file di codice servizio che è stato generato per l'entità, quindi scegliere **Visualizza codice**.  
  
     Il file di codice servizio dell'entità verrà aperto nell'editor di codice.  Per ulteriori informazioni su questo file, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Aggiungere il metodo Updater per aggiornare i dati.  Nell'esempio seguente vengono aggiornate le informazioni per un contatto nel database di esempio AdventureWorks per SQL Server.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)  
  
  