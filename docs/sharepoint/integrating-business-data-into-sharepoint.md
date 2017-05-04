---
title: "Integrazione di dati business in SharePoint | Microsoft Docs"
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
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggregazione di dati"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati business"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creazione di un modello"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggregazione di dati"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati business"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creazione di un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Integrazione di dati business in SharePoint
  In SharePoint è possibile integrare i dati business.  Tali dati possono provenire da applicazioni server di back\-end, ad esempio [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel e SAP o da un servizio Web.  Gli utenti possono visualizzare, aggiungere, aggiornare o eliminare dati business tramite elenchi esterni o web part di dati business in SharePoint. Inoltre, possono accedere a questi dati offline in un'applicazione Microsoft Office quale Microsoft Outlook.  Per ulteriori informazioni, vedere [Modalità di visualizzazione dei dati esterni](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Per integrare i dati in SharePoint, creare un modello per il servizio di integrazione applicativa dei dati \(BDC\).  Il servizio BDC è un'applicazione di SharePoint che consente di archiviare le informazioni sui dati nelle applicazioni aziendali.  Per ulteriori informazioni, vedere [Servizio di integrazione applicativa dei dati \(BDC\)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## Modelli di Visual Studio  
 I modelli di Visual Studio consentono di scrivere codice personalizzato per recuperare e aggiornare i dati dalle origini dati back\-end.  È anche possibile aggregare i dati di più origini.  Ad esempio si può visualizzare un elenco di clienti in cui sono contenuti i dati di un database di [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] e un servizio Web.  
  
 Inoltre, è possibile importare i modelli già distribuiti in SharePoint.  Dopo aver importato un modello, si può aggiungere codice personalizzato o utilizzare semplicemente Visual Studio per assemblare e distribuire il modello in diverse server farm di SharePoint.  Per ulteriori informazioni, vedere [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Progettazione di un modello in Visual Studio  
 Un modello può essere progettato tramite una finestra di progettazione e diverse finestre degli strumenti.  Mentre si progetta il modello, Visual Studio consente di generare il codice XML del modello.  Per ulteriori informazioni, vedere [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
 In un modello sono contenuti entità e metodi.  
  
### Entità  
 Un'entità descrive una raccolta di campi.  Ad esempio un'entità può rappresentare una tabella di un database.  Un'entità viene visualizzata come tipo di contenuto esterno in SharePoint.  Per ulteriori informazioni sui tipi di contenuto esterno, vedere [Cosa sono tipi di contenuto esterni?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### Metodi  
 Un metodo consente agli utenti di un tipo di contenuto esterno di effettuare un'azione nei campi di un'entità.  Ad esempio un metodo Updater potrebbe consentire agli utenti di modificare l'indirizzo e la data di nascita di un cliente dove `Address` e `BirthDate` sono campi dell'entità `Customer`.  
  
 Visual Studio consente di generare un file di codice di servizio per ogni entità nel modello.  Quando si aggiunge un metodo al modello, tramite Visual Studio viene generato un metodo corrispondente nel file di codice di servizio.  Aggiungere codice a ogni metodo per effettuare l'attività appropriata.  Ad esempio se si aggiunge un metodo Creator al modello, tramite Visual Studio viene generato un metodo Creator nel file di codice di servizio.  Questo metodo viene chiamato dal servizio BDC quando un utente fa clic sul pulsante **Nuovo elemento** in un elenco basato sul modello.  Pertanto, aggiungere codice al metodo Creator che consente di aggiungere nuovi dati a un'origine.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)|Viene illustrato come creare un nuovo modello o importare un modello esportato da SharePoint.|  
|[Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)|Viene illustrato come progettare gli elementi di un modello tramite gli strumenti di progettazione di Visual Studio.|  
|[Quando si utilizza SharePoint Designer e Visual Studio per la compilazione di soluzioni tramite BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Consente di stabilire se utilizzare Visual Studio o SharePoint Designer per la creazione di un modello per BDC.|  
  
  