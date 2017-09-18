---
title: "Associazione di controlli ai dati in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Origini dati (finestra)"
  - "origini dati, visualizzazione di dati"
  - "dati, visualizzazione"
  - "visualizzazione di dati"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associazione di controlli ai dati in Visual Studio
È possibile visualizzare i dati per gli utenti dell'applicazione mediante l'associazione dei dati ai controlli.  È possibile creare i controlli con associazione a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** a Visual Studio.  
  
 In questo argomento vengono descritte le origini dati che è possibile utilizzare per creare controlli associati a dati.  Vengono inoltre descritte alcune delle attività generali coinvolte nell'associazione ai dati.  Per informazioni più dettagliate su come creare controlli con associazione a dati, vedere [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md), [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) e [Associazione di controlli Silverlight ai dati in Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md).  
  
## Origini dati  
 Un'origine dati rappresenta i dati disponibili per l'applicazione.  È possibile creare origini dati da database, servizi o oggetti.  Per ulteriori informazioni, vedere [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md).  
  
 Solo per alcune origini dati è possibile creare controlli associati a dati mediante il trascinamento di elementi dalla finestra **Origini dati**.  Nella tabella seguente vengono indicate le origini dati supportate.  
  
|Origine dati|Supporto del trascinamento in **Progettazione Windows Form**|Supporto del trascinamento in **WPF Designer**|Supporto del trascinamento in **Silverlight Designer**|  
|------------------|------------------------------------------------------------------|----------------------------------------------------|------------------------------------------------------------|  
|Dataset|Sì|Sì|No|  
|Entity Data Model|No<sup>1</sup>|Sì|Sì|  
|Classi LINQ to SQL|No<sup>2</sup>|No<sup>2</sup>|No<sup>2</sup>|  
|Servizi \(inclusi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], servizi WCF e servizi Web\)|Sì|Sì|Sì|  
|Oggetto|Sì|Sì|Sì|  
|SharePoint|Sì|Sì|Sì|  
  
 1.  Quando **Progettazione Windows Form** è aperto, le entità nella finestra **Origini dati** sono di sola lettura e non possono essere trascinate alla finestra di progettazione.  È comunque possibile creare controlli associati a dati aggiungendo una nuova origine dati dell'oggetto basata sull'Entity Data Model, quindi trascinare tali oggetti nella finestra di progettazione.  
  
 2.  Le classi LINQ to SQL non sono visualizzate nella finestra **Origini dati**.  È comunque possibile aggiungere una nuova origine dati dell'oggetto basata sulle classi LINQ to SQL, quindi trascinare tali oggetti nella finestra di progettazione per creare controlli con associazione a dati.  Per ulteriori informazioni, vedere [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md).  
  
## Finestra Origini dati  
 Nella finestra **Origini dati** sono visualizzate le voci relative alle origini dati disponibili per il progetto.  È possibile trascinare gli elementi da questa finestra per creare controlli associati ai dati sottostanti.  Per ulteriori informazioni, vedere [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
 Per ogni tipo di dati visualizzato nella finestra **Origini dati** viene creato un controllo predefinito quando si trascina l'elemento nella finestra di progettazione.  Prima di trascinare un elemento dalla finestra **Origini dati**, è possibile modificare il controllo che verrà creato.  Per ulteriori informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Attività coinvolte nell'associazione di controlli a dati  
 Nella tabella seguente vengono elencate alcune delle attività più comuni eseguite per associare i controlli ai dati.  
  
|Attività|Ulteriori informazioni|  
|--------------|----------------------------|  
|Aprire la finestra **Origini dati**|[Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md)|  
|Aggiungere un'origine dati al progetto.|[Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [Procedura: connettersi ai dati di un servizio](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|Impostare il controllo che viene creato quando si trascina un elemento dalla finestra **Origini dati** alla finestra di progettazione.|[Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modificare l'elenco dei controlli associati agli elementi nella finestra **Origini dati**.|[Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Creare controlli associati a dati.|[Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [Associazione di controlli Silverlight ai dati in Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 Dopo avere creato controlli associati ai dati, potrebbe essere necessario eseguire una delle attività seguenti.  
  
|Attività|Ulteriori informazioni|  
|--------------|----------------------------|  
|Modificare i dati nell'origine dati sottostante|[Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)|  
|Convalidare le modifiche apportate ai dati|[Convalida dei dati](../Topic/Validating%20Data.md)|  
|Salvare i dati aggiornati nel database|[Salvataggio di dati](../data-tools/saving-data.md)|  
  
## Vedere anche  
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associazione di controlli Silverlight ai dati in Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [Procedura: associare controlli alle immagini di un database](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)   
 [Strumenti per l'utilizzo delle origini dati in Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)