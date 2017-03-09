---
title: "Connessione ai dati nelle applicazioni Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "System.Data.SqlClient.SqlConnection"
  - "System.Data.Odbc.OdbcConnection"
  - "System.Data.OleDb.OleDbConnection"
  - "System.Data.OracleClient.OracleConnection"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "connessione a database, connessioni ADO.NET"
  - "Connection (oggetti)"
  - "Connection (oggetti), strumenti per attività"
  - "Connection (oggetti), tipi"
  - "pool di connessioni, connessioni ADO.NET"
  - "stringhe di connessione [Visual Studio], ADO.NET"
  - "connessioni, informazioni"
  - "connessioni, fase di progettazione"
  - "dati [Visual Studio], connessione"
  - "adattatori dati, connessioni"
  - "connessioni a database [Visual Studio], ADO.NET"
  - "database [Visual Studio], connessione"
  - "connessioni in fase di progettazione"
  - "proprietà dinamiche, connessioni ADO.NET"
  - "OleDbConnection (classe), ADO.NET (oggetti Connection)"
  - "SqlConnection (classe), ADO.NET (oggetti Connection)"
  - "TableAdapters, connessioni"
  - "transazioni, ADO.NET"
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Connessione ai dati nelle applicazioni Windows Form
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre strumenti per connettere l'applicazione a dati da molte origini diverse, ad esempio database, servizi Web e oggetti.  Se si usano strumenti per la progettazione di dati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], spesso non occorre creare in modo esplicito un oggetto connessione per il form o il componente.  L'oggetto connessione è in genere creato come risultato del completamento di una delle procedure guidate relative ai dati o del trascinamento di oggetti dati nel form.  Per connettere l'applicazione a dati in un database, un servizio Web o un oggetto, eseguire la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) selezionando **Aggiungi nuova origine dati** dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
 Il diagramma seguente mostra il flusso standard di operazioni durante la connessione a dati tramite l'esecuzione di una query TableAdapter per recuperare dati e visualizzarli in un form in un'applicazione Windows.  
  
 ![Flusso dei dati in un'applicazione client](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 In alcune situazioni è utile creare un oggetto connessione senza usare strumenti per la progettazione di dati.  Per informazioni sulla creazione di connessioni a livello di codice, vedere [Connessione a un'origine dati](../Topic/Connecting%20to%20a%20Data%20Source%20in%20ADO.NET.md).  
  
> [!NOTE]
>  Per informazioni sulla connessione di applicazioni Web ai dati, vedere [ASP.NET Data Access Content Map](http://msdn.microsoft.com/it-it/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## Procedure dettagliate per la connessione di applicazioni Windows Forms ai dati  
 Le procedure dettagliate seguenti includono procedure correlate alla connessione ai dati in applicazioni Windows Forms:  
  
-   [Procedura dettagliata: connessione ai dati in un database \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)  
  
-   [Procedura dettagliata: connessione ai dati in un file di database lodale \(Windows Form\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Procedura dettagliata: connessione ai dati in un servizio Web \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Web%20Service%20\(Windows%20Forms\).md)  
  
-   [Procedura dettagliata: connessione ai dati negli oggetti \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)  
  
-   [Procedura dettagliata: connessione ai dati in un database di Access \(Windows Form\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## Creazione di connessioni  
 In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le connessioni sono configurate tramite la finestra di dialogo **Aggiungi\/Modifica connessione**.  La finestra di dialogo **Aggiungi connessione** sarà visualizzata quando si modificano o si creano connessioni in una delle procedure guidate relative ai dati o in [Esplora server\/Esplora database](../Topic/Server%20Explorer.md) oppure quando si modificano le proprietà delle connessioni nella finestra **Proprietà**.  
  
 Le connessioni dati sono configurate automaticamente quando si esegue una delle azioni seguenti.  
  
|Azione|Descrizione|  
|------------|-----------------|  
|Eseguire la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).|Le connessioni sono configurate quando si sceglie il percorso del database nella **Configurazione guidata origine dati**.  Per altre informazioni, vedere [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Eseguire la [TableAdapter \(configurazione guidata\)](../Topic/TableAdapter%20Configuration%20Wizard.md).|Le connessioni sono create nella **Configurazione guidata TableAdapter**.  Per altre informazioni, vedere [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Eseguire la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md).|Le connessioni sono create nella **Configurazione guidata query TableAdapter**.  Per altre informazioni, vedere [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Trascinare elementi dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) in un form o in [Component Designer](../Topic/Component%20Designer.md).|Gli oggetti connessione sono creati quando si trascinano elementi dalla finestra **Origini dati** in **Progettazione Windows Form** o in **Progettazione componenti**.  Per altre informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Aggiungere nuove connessioni dati a [Esplora server\/Esplora database](../Topic/Server%20Explorer.md).|Le connessioni dati in **Esplora server\/Esplora database** sono visualizzate nell'elenco di connessioni disponibili nelle procedure guidate relative ai dati.|  
  
## Stringhe di connessione  
 Le stringhe di connessione possono essere archiviate nell'applicazione compilata o nel file di configurazione dell'applicazione.  Per altre informazioni, vedere [Procedura: salvare e modificare stringhe di connessione](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
## Informazioni di connessione e sicurezza  
 Poiché la creazione di una connessione comporta l'accesso a una risorsa importante, ovvero un database, la configurazione e l'uso di una connessione presentano spesso problemi di sicurezza.  
  
 Il livello di sicurezza dell'applicazione e dell'accesso all'origine dati dipende dall'architettura del sistema.  In un'applicazione basata su Web, ad esempio, gli utenti ottengono in genere l'accesso anonimo a Internet Information Services \(IIS\) e non forniscono quindi credenziali di sicurezza.  In questo caso, l'applicazione gestisce e usa le proprie informazioni di accesso, invece di usare informazioni utente specifiche, per aprire le connessioni e accedere al database.  
  
> [!IMPORTANT]
>  L'archiviazione dei dettagli relativi alle stringhe di connessione, ad esempio una, può influire sulla sicurezza dell'applicazione.  La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.  Per altre informazioni, vedere [Protezione delle informazioni di connessione](../Topic/Protecting%20Connection%20Information.md).  
  
 In applicazioni Intranet o a più livelli è possibile usare l'opzione di sicurezza integrata offerta da Windows, IIS e SQL Server.  In questo modello le credenziali di autenticazione di un utente per la rete locale sono usate anche per accedere alle risorse del database e nella stringa di connessione non si usano password o nomi utente espliciti.  Le autorizzazioni sono in genere definite nel computer server di database tramite i gruppi. Non sarà quindi necessario definire autorizzazioni individuali per ogni utente che potrebbe accedere al database.  In questo modello non occorre archiviare le informazioni di accesso per la connessione e non sono necessari passaggi aggiuntivi per proteggere le informazioni della stringa di connessione.  
  
 Per altre informazioni sulla sicurezza, vedere gli argomenti seguenti:  
  
-   [Protezione di applicazioni ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md)  
  
-   [More Secure File and Data Access in Windows Forms](../Topic/More%20Secure%20File%20and%20Data%20Access%20in%20Windows%20Forms.md)  
  
## Connessioni in fase di progettazione in Esplora server\/Esplora database  
 **Esplora server\/Esplora database** consente di creare connessioni in fase di progettazione alle origini dati.  Sarà quindi possibile esplorare le origini dati disponibili, visualizzare informazioni su tabelle, colonne e altri elementi in esse contenuti e infine modificare e creare elementi di database.  
  
 L'applicazione non usa direttamente le connessioni disponibili in **Esplora server\/Esplora database**.  Queste connessioni sono usate da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per operazioni relative al database in fase di progettazione.  Per altre informazioni, vedere [Visual Database Tools](http://msdn.microsoft.com/it-it/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Ad esempio, in fase di progettazione è possibile usare **Esplora server\/Esplora database** per creare una connessione a un database.  Successivamente, durante la progettazione di un form, sarà possibile esplorare il database, selezionare colonne da una tabella e trascinarle in [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md).  Questa procedura consente di creare un [TableAdapter](../data-tools/tableadapter-overview.md) nel set di dati,  oltre a creare un nuovo oggetto connessione, che fa parte del TableAdapter appena creato.  
  
 Le informazioni sulle connessioni in fase di progettazione sono archiviate nel computer locale in modo indipendente rispetto a in progetto specifico o una particolare soluzione.  Dopo la creazione di una connessione in fase di progettazione durante l'uso di un'applicazione, la connessione sarà quindi visualizzata in **Esplora server\/Esplora database** ogni volta che si usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], purché il server a cui fa riferimento la connessione sia disponibile.  Per altre informazioni, vedere [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/it-it/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../data-tools/includes/sqlobjectexplorer_md.md)]  
  
## Vedere anche  
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Procedura dettagliata: connessione ai dati in un database \(Windows Form\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Database%20\(Windows%20Forms\).md)   
 [ASP.NET Data Access Content Map](http://msdn.microsoft.com/it-it/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)