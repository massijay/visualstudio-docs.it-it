---
title: "Procedura dettagliata: creazione di un oggetto TableAdapter con pi&#249; query | Microsoft Docs"
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
  - "dati [Visual Studio], TableAdapters"
  - "dati [Visual Studio], procedure dettagliate"
  - "query [Visual Studio], TableAdapters"
  - "TableAdapter (query), creazione"
  - "TableAdapters, creazione"
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: creazione di un oggetto TableAdapter con pi&#249; query
In questa procedura dettagliata verrà creato un TableAdapter in un set di dati mediante [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  Verrà descritto come aggiungere una seconda query nel [TableAdapter](../data-tools/tableadapter-overview.md) usando la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md) all'interno di [Progettazione DataSet](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto **Applicazione Windows**.  
  
-   Creazione e configurazione di un'origine dati nell'applicazione creando un set di dati con **Configurazione guidata origine dati**.  
  
-   Apertura del nuovo set di dati in **Progettazione DataSet**.  
  
-   Aggiunta di query al TableAdapter con la **Configurazione guidata query TableAdapter**.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind nella versione SQL Server o Access.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione di una nuova applicazione Windows  
 Il primo passaggio consiste nella creazione di un'applicazione Windows.  
  
#### Per creare un nuovo progetto Applicazione Windows  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Scegliere un linguaggio di programmazione nel riquadro **Tipi progetto**.  
  
3.  Fare clic su **Applicazione Windows** nel riquadro **Modelli**.  
  
4.  Assegnare al progetto il nome `TableAdapterQueriesWalkthrough`, quindi fare clic **OK**.  
  
     Visual Studio aggiunge il progetto a **Esplora soluzioni** e visualizza un nuovo form nella finestra di progettazione.  
  
## Creazione di un'origine dati di database con un TableAdapter  
 Questo passaggio crea un set di dati usando la **Configurazione guidata origine dati** basata sulla tabella `Customers` nel database di esempio Northwind.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         \-oppure\-  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi\/Modifica connessione**.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi scegliere **Avanti**.  
  
6.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare la tabella **Customers**, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella **Customers** viene visualizzata nella finestra **Origini dati**.  
  
## Apertura del set di dati in Progettazione DataSet.  
  
#### Per aprire il set di dati in Progettazione DataSet.  
  
1.  Fare clic con il pulsante destro del mouse su **NorthwindDataset** nella finestra **Origini dati**.  
  
2.  Scegliere **Modifica il Dataset con la finestra di progettazione** dal menu di scelta rapida.  
  
     NorthwindDataset viene aperto in **Progettazione DataSet**.  
  
## Aggiunta di una seconda query a CustomersTableAdapter  
 Con la procedura guidata è stato creato il set di dati con una tabella dati **Customers** e un oggetto **CustomersTableAdapter**.  In questa sezione della procedura dettagliata viene aggiunta una seconda query a **CustomersTableAdapter**.  
  
#### Per aggiungere una query a CustomersTableAdapter  
  
1.  Trascinare una **Query** dalla scheda **Set di dati** della **Casella degli strumenti** alla tabella **Customers**.  
  
     Verrà avviata la [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md).  
  
2.  Selezionare **Usa istruzioni SQL** e fare clic su **Avanti**.  
  
3.  Selezionare **SELECT che restituisce righe** e fare clic su **Avanti**.  
  
4.  Aggiungere una clausola WHERE alla query in modo da ottenere quanto segue:  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Se si usa la versione Access di Northwind, sostituire il parametro @City con un punto interrogativo.  \(`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`\)  
  
5.  Nella pagina **Scegliere i metodi per generare** assegnare al metodo **Riempi un DataTable** il nome `FillByCity`.  
  
    > [!NOTE]
    >  Il metodo **Restituisci un DataTable** non è usato in questa procedura dettagliata, quindi è possibile deselezionare la casella di controllo o lasciare il nome predefinito.  
  
6.  Fare clic su **Avanti** e completare la procedura guidata.  
  
     La query **FillByCity** viene aggiunta a **CustomersTableAdapter**.  
  
## Aggiunta di codice per l'esecuzione della query aggiuntiva nel form  
  
#### Per eseguire la query  
  
1.  Selezionare **Form1** in **Esplora soluzioni**, quindi fare clic su **Progettazione visualizzazioni**.  
  
2.  Trascinare il nodo **Customers** dalla finestra **Origini dati** a **Form1**.  
  
3.  Passare alla visualizzazione del codice scegliendo **Codice** dal menu **Visualizza**.  
  
4.  Sostituire il codice nel gestore eventi `Form1_Load` con il codice seguente per eseguire la query `FillByCity`.  
  
     [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
## Esecuzione dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5.  
  
-   La griglia viene compilata con i clienti il cui valore `City` corrisponde a `Seattle`.  
  
## Passaggi successivi  
  
### Per aggiungere funzionalità all'applicazione  
  
-   Aggiungere un controllo <xref:System.Windows.Forms.TextBox> e un controllo <xref:System.Windows.Forms.Button> e passare il valore contenuto nella casella di testo alla query.  \(`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`\).  
  
-   Aggiungere la logica di convalida all'evento <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> delle tabelle dati nel set di dati.  Per altre informazioni, vedere [Convalida dei dati nei dataset](../data-tools/validate-data-in-datasets.md).  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: creare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)