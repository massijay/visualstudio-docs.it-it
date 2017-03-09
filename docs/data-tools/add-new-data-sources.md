---
title: "Cenni preliminari sulle origini dati | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], origini dati"
  - "origini dati"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cenni preliminari sulle origini dati
Le origini dati rappresentano i dati disponibili per l'applicazione  o, più precisamente, rappresentano i dati che si sa già di voler utilizzare nell'applicazione.  È possibile ottenere le origini dati da database \(inclusi i file di database locali\), servizi e oggetti.  
  
 Nella finestra **Origini dati** sono visualizzate le origini dati che vengono aggiunte al progetto.  In molti casi è possibile trascinare le origini dati in Progettazione Windows Form, in WPF Designer e in Silverlight Designer per creare controlli che vengono associati ai dati sottostanti.  Per ulteriori informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 In Visual Studio sono disponibili strumenti che consentono di creare e modificare le origini dati in modo da poterle utilizzare nell'applicazione.  Nei progetti Visual Studio le origini dati sono rappresentate come Entity data Model, dataset, oggetti proxy restituiti da un servizio o altri tipi di oggetti, a seconda degli oggetti restituiti dall'archivio dati sottostante.  
  
 È possibile creare e modificare le origini dati mediante la **Configurazione guidata origine dati**.  
  
## Origini dati create da database  
 È possibile creare un'origine dati da un database eseguendo la **Configurazione guidata origine dati** e selezionando il tipo di origine dati **Database**.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
 Quando si crea un'origine dati da un database, Visual Studio genera un *modello dati* e lo aggiunge al progetto.  Un modello dati è una visualizzazione programmabile fortemente tipizzata dei dati sottostanti nel database.  È possibile utilizzare Visual Studio per creare i tipi di modelli dati seguenti:  
  
-   Un modello concettuale basato su [Entity Data Model](../Topic/Entity%20Data%20Model.md).  Questo tipo di modello può essere utilizzato da Entity Framework o dai Servizi dati WCF.  Per ulteriori informazioni, vedere [Panoramica su Entity Framework](../Topic/Entity%20Framework%20Overview.md) e [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).  
  
-   Dataset tipizzato.  Per ulteriori informazioni, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Classi LINQ to SQL.  Per ulteriori informazioni, vedere [LINQ to SQL](../Topic/LINQ%20to%20SQL.md).  
  
    > [!NOTE]
    >  A differenza di quanto accade per i modelli concettuali e i dataset basati su Entity Data Model, non è possibile creare le classi LINQ to SQL mediante la **Configurazione guidata origine dati**.  Le classi LINQ to SQL inoltre non sono visualizzate nella finestra **Origini dati** e pertanto non possono essere trascinate direttamente in una finestra di progettazione per creare controlli con associazione a dati.  È tuttavia possibile creare un'origine dati dell'oggetto basata sulle classi LINQ to SQL e trascinare gli oggetti nella finestra di progettazione.  Per ulteriori informazioni, vedere [Procedura: creare classi LINQ to SQL con mapping a tabelle e visualizzazioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
### Origini dati create da file di database locali  
 È inoltre possibile creare le origini dati dai seguenti tipi di file di database: database Access \(file con estensione mdb\), database LocalDB di SQL Server Express \(file con estensione mdb\) e database di SQL Server Express \(file con estensione mdf\).  Quando si creano origini dati da questi file di database, è possibile aggiungere direttamente i file di database al progetto.  Per ulteriori informazioni, vedere i seguenti argomenti:  
  
-   [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md)  
  
-   [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## Origini dati create dai servizi  
 È possibile creare un'origine dati da un servizio eseguendo la **Configurazione guidata origine dati** e selezionando il tipo di origine dati **Servizio**.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
 Quando si crea un'origine dati da un servizio, Visual Studio aggiunge un riferimento al servizio al progetto.  Vengono inoltre creati oggetti proxy che corrispondono agli oggetti restituiti dal servizio.  Se, ad esempio, un servizio restituisce un dataset, verrà rappresentato come dataset all'interno del progetto. Se invece restituisce un tipo specifico, verrà rappresentato esattamente come il tipo restituito.  
  
 È possibile creare un'origine dati dai tipi di servizi seguenti:  
  
-   Servizi dati WCF.  Per ulteriori informazioni, vedere [Cenni preliminari](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Servizi WCF \(Windows Communication Foundation\).  Per ulteriori informazioni, vedere [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   servizi Web.  Per ulteriori informazioni, vedere [Not in Build: Introduction to Programming Web Services in Managed Code](http://msdn.microsoft.com/it-it/bd8861f3-39e1-4c06-995e-677e007eb961).  
  
    > [!NOTE]
    >  Gli elementi visualizzati nella finestra **Origini dati** dipendono dai dati restituiti dal servizio.  Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili.  Se ad esempio il servizio restituisce un dataset non tipizzato, al termine della procedura guidata nella finestra **Origini dati** non verrà visualizzato alcun elemento.  I dataset non tipizzati, infatti, non forniscono alcuno schema e, pertanto, la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.  
  
## Origini dati create da oggetti  
 È possibile creare un'origine dati da qualsiasi oggetto che espone una o più proprietà pubbliche eseguendo la **Configurazione guidata origine dati** e quindi selezionando il tipo di origine dati **Oggetto**.  Tutte le proprietà pubbliche di un oggetto vengono visualizzate nella finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati negli oggetti](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Per ulteriori informazioni sull'associazione agli oggetti, vedere [Associazione di oggetti in Visual Studio](../data-tools/bind-objects-in-visual-studio.md).  
  
## Origini dati create dagli elenchi di SharePoint  
 È possibile creare un'origine dati da un elenco di SharePoint eseguendo la **Configurazione guidata origine dati** e selezionando il tipo di origine dati **SharePoint**.  SharePoint espone i dati mediante [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], pertanto la creazione di un'origine dati SharePoint corrisponde alla creazione di un'origine dati da un servizio.  Selezionando la voce **SharePoint** nella **Configurazione guidata origine dati**, viene visualizzata la finestra di dialogo **Aggiungi riferimento al servizio** in cui è possibile connettersi al servizio dati di SharePoint puntando al server SharePoint.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Vedere anche  
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)