---
title: "Procedura: connettersi ai dati di un database | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "dati [Visual Studio], connessione a database"
  - "origini dati, creazione"
  - "origini dati, database"
  - "database (connessioni)"
  - "database, connessione"
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
caps.handback.revision: 55
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: connettersi ai dati di un database
È possibile connettere l'applicazione a un database usando Visual Studio.  Dopo avere creato la connessione dati, Visual Studio genera un modello dati che verrà usato dall'applicazione per interagire con i dati del database.  Gli oggetti presenti nel modello dati vengono visualizzati nella [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  È quindi possibile creare controlli associati a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** a un'area di progettazione.  Per altre informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 In questo argomento vengono fornite istruzioni per la connessione a un database e la creazione dei tipi di modelli dati seguenti:  
  
-   Set di dati  
  
-   Entity Data Model \(EDM\)  
  
> [!NOTE]
>  È inoltre possibile usare Visual Studio per creare classi LINQ to SQL da un database.  Le classi LINQ to SQL non sono visualizzate nella finestra **Origini dati**, pertanto non possono essere trascinate direttamente in una finestra di progettazione per creare controlli associati a dati.  Per altre informazioni sulla creazione delle classi LINQ to SQL da un database, vedere [Procedura: creare classi LINQ to SQL con mapping a tabelle e visualizzazioni \(Progettazione relazionale oggetti\)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
##  <a name="dataset"></a> Connessione a un database e creazione di un set di dati  
 Quando si crea un set di dati basato su un database, Visual Studio crea un set di classi che rappresentano una visualizzazione programmabile dei dati.  La classe principale viene chiamata *dataset tipizzato*.  Il dataset tipizzato contiene oggetti della tabella dati che rappresentano tabelle del database.  Per altre informazioni sui dataset tipizzati, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Dopo avere creato un set di dati, è possibile creare controlli WPF o Windows Form con associazione a dati trascinando oggetti dataset dalla finestra Origini dati a Progettazione WPF o a Progettazione Windows Form.  
  
#### Per connettere l'applicazione a un database e creare un set di dati  
  
1.  Creare un nuovo progetto o aprirne uno esistente in Visual Studio.  
  
2.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Verrà avviata la **Configurazione guidata origine dati**.  
  
3.  Nella pagina **Seleziona un tipo di origine dati** selezionare **Database**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina **Scegli modello database** selezionare **DataSet** e scegliere **Avanti**.  
  
5.  Nella pagina **Seleziona connessione dati** selezionare una connessione dati nell'elenco delle connessioni disponibili e fare clic su **Avanti**.  
  
     Se la connessione dati desiderata non è disponibile, creare una nuova connessione seguendo i passaggi illustrati in [Creazione di una nuova connessione al database](#CreatingDataConnection).  
  
6.  Nella pagina **Salva la stringa di connessione nel file di configurazione applicazione** è possibile deselezionare la casella di controllo **Sì, salva la connessione con nome** se si desidera salvare la stringa di connessione direttamente nell'applicazione compilata.  Per impostazione predefinita, la connessione viene salvata nel file di configurazione dell'applicazione.  Per altre informazioni, vedere [Procedura: salvare e modificare stringhe di connessione](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
7.  Nella pagina **Seleziona oggetti di database** selezionare gli oggetti di database che si desidera usare nell'applicazione.  È inoltre possibile sostituire il **Nome DataSet** predefinito.  
  
8.  Scegliere **Fine**.  Il set di dati appena creato sarà ora disponibile nella finestra **Origini dati**.  
  
    > [!NOTE]
    >  Se la finestra **Origini dati** non è aperta, aprirla scegliendo **Mostra origini dati** dal menu **Dati**.  
  
9. A questo punto è possibile trascinare elementi dalla finestra **Origini dati** a Progettazione WPF, Progettazione Windows Form o [Component Designer](../Topic/Component%20Designer.md) per creare controlli associati a dati.  Per altre informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> Connessione al database e creazione di un Entity Data Model  
 Quando si crea un Entity Data Model basato su un database, Visual Studio crea un set di classi che rappresentano una visualizzazione programmabile dei dati.  Per altre informazioni sugli Entity Data Model e su ADO.NET Entity Framework, vedere [Panoramica su Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
 Dopo avere creato un Entity Data Model, è possibile creare controlli WPF o Windows Form con associazione a dati trascinando oggetti entità dalla finestra Origini dati a Progettazione WPF.  
  
#### Per connettere l'applicazione a un database e creare un Entity Data Model  
  
1.  Creare un nuovo progetto o aprirne uno esistente in Visual Studio.  
  
2.  Seguire i passaggi nella **Procedura guidata Entity Data Model** per connettersi a un database e specificare il contenuto del modello.  Per altre informazioni, vedere [How to: Create a New .edmx File](http://msdn.microsoft.com/it-it/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Dopo avere completato la **Procedura guidata Entity Data Model**, l'Entity Data Model creato si apre in Entity Data Model Designer e gli oggetti dati diventano disponibili nella finestra **Origini dati**.  
  
    > [!NOTE]
    >  Se la finestra **Origini dati** non è aperta, aprirla scegliendo **Mostra origini dati** dal menu **Dati**.  
  
4.  Se Progettazione WPF è aperto, è possibile trascinare elementi dalla finestra **Origini dati** alla finestra di progettazione per creare controlli associati a Entity Data Model.  Per altre informazioni, vedere [Procedura: associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Se Progettazione Windows Form è aperto, non è possibile trascinare elementi da **Origini dati** alla finestra di progettazione.  Per creare controlli associati a Entity Data Model, è necessario compilare il progetto, aggiungere una nuova origine dati dell'oggetto basata sull'Entity Data Model, quindi trascinare tali oggetti nella finestra di progettazione.  
  
##  <a name="CreatingDataConnection"></a> Creazione di una nuova connessione al database  
 Quando si usa la **Configurazione guidata origine dati** o la **Procedura guidata Entity Data Model**, è necessario specificare la connessione al database che si desidera usare.  Se non è già presente una connessione al database, crearne una eseguendo la procedura indicata di seguito.  
  
 Queste istruzioni presuppongono che sia già stata avviata la **Configurazione guidata origine dati** o la **Procedura guidata Entity Data Model**, come descritto in [Connessione a un database e creazione di un set di dati](#dataset) e [Connessione al database e creazione di un Entity Data Model](#edm).  
  
#### Per creare una nuova connessione al database  
  
1.  Nella pagina **Seleziona connessione dati** della **Configurazione guidata origine dati** o della **Procedura guidata Entity Data Model** fare clic su **Nuova connessione**.  
  
     Si verificherà una delle azioni seguenti:  
  
    -   Se è stata già creata una connessione dati in Visual Studio, viene visualizzata la finestra di dialogo **Aggiungi connessione**.  
  
    -   Se questa è la prima connessione dati che viene creata in Visual Studio, viene visualizzata la finestra di dialogo **Scegli origine dati**.  Selezionare il tipo di database al quale si desidera connettersi, quindi fare clic su **OK** per visualizzare la finestra di dialogo **Aggiungi connessione**.  
  
2.  Nella finestra di dialogo **Aggiungi connessione** immettere le informazioni richieste.  La finestra di dialogo **Aggiungi connessione** è diversa per ogni tipo di provider di dati.  
  
    > [!NOTE]
    >  Se l'**Origine dati** selezionata nella finestra di dialogo **Aggiungi connessione** non è quella a cui si desidera connettersi, fare clic su **Modifica** per aprire la finestra di dialogo **Modifica origine dati**, quindi scegliere un'origine dati diversa.  
  
3.  Nella finestra di dialogo **Aggiungi connessione** scegliere **OK**.  
  
     Verrà visualizzata nuovamente la pagina **Seleziona connessione dati** della **Configurazione guidata origine dati** o della **Procedura guidata Entity Data Model**.  
  
4.  Nella pagina **Seleziona connessione dati** verificare che la nuova connessione dati sia selezionata, quindi fare clic su **Avanti**.  
  
5.  Completare i passaggi rimanenti nella **Configurazione guidata origine dati** o nella **Procedura guidata Entity Data Model**.  
  
## Sicurezza di .NET Framework  
 L'archiviazione di informazioni riservate, ad esempio una password, può avere implicazioni sulla sicurezza dell'applicazione.  L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro.  Per altre informazioni, vedere [Protezione delle informazioni di connessione](../Topic/Protecting%20Connection%20Information.md).  
  
## Vedere anche  
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Connessione a un'origine dati](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md)