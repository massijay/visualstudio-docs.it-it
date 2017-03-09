---
title: "Procedura dettagliata: passaggio di dati tra Windows Form | Microsoft Docs"
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
  - "dati [Visual Studio], passaggio tra form"
  - "form, passaggio di dati tra"
  - "procedure dettagliate [Visual Studio], dati"
  - "procedure dettagliate [Windows Form], dati"
  - "Windows Form, procedure dettagliate"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: passaggio di dati tra Windows Form
Questa procedura dettagliata fornisce istruzioni passo\-passo per il passaggio dei dati da un form a un altro.  Usando le tabelle relative a clienti e ordini del database Northwind, un form consentirà agli utenti di selezionare un cliente, mentre in un altro verranno visualizzati gli ordini del cliente selezionato.  In questa procedura dettagliata viene descritto come creare in un form un metodo che riceve dati dal primo form.  
  
> [!NOTE]
>  Questa procedura dettagliata illustra solo un modo per passare dati tra i form.  Esistono altre alternative per passare dati a un form, incluse la creazione di un secondo costruttore per la ricezione dei dati o la creazione di una proprietà pubblica da impostare con i dati del primo form.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto **Applicazione Windows**.  
  
-   Creazione e configurazione di un set di dati con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selezione del controllo da creare nel form durante il trascinamento di elementi dalla finestra **Origini dati**.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione del controllo associato a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.  
  
-   Creazione di un secondo form con una griglia per la visualizzazione dei dati.  
  
-   Creazione di una query TableAdapter per recuperare gli ordini di uno specifico cliente.  
  
-   Passaggio dei dati da un form all'altro.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione dell'applicazione Windows  
  
#### Per creare il nuovo progetto Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome `PassingDataBetweenForms`.  
  
3.  Selezionare **Applicazione Windows Form** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **PassingDataBetweenForms** verrà creato e aggiunto a **Esplora soluzioni**.  
  
## Creazione dell'origine dati  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Scegli modello database** verificare che sia specificato **DataSet**, quindi scegliere **Avanti**.  
  
5.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         \-oppure\-  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi\/Modifica connessione**.  
  
6.  Se per il database è necessaria una password ed è selezionata l'opzione per l'inclusione dei dati sensibili, selezionare l'opzione e fare clic su **Avanti**.  
  
7.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.  
  
8.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
9. Selezionare le tabelle **Customers** e **Orders**, quindi scegliere **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle **Customers** e Orders vengono visualizzate nella finestra **Origini dati**.  
  
## Creazione del primo form \(Form1\)  
 È possibile creare una griglia con associazione a dati, ovvero un controllo <xref:System.Windows.Forms.DataGridView> trascinando il nodo **Customers** dalla finestra **Origini dati** nel form.  
  
#### Per creare una griglia con associazione a dati nel form  
  
-   Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.  
  
     In **Form1** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## Creazione del secondo form \(Form2\)  
  
#### Per creare un secondo form al quale passare i dati  
  
1.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.  
  
2.  Lasciare il nome predefinito **Form2** e scegliere **Aggiungi**.  
  
3.  Trascinare il nodo **Orders** principale dalla finestra **Origini dati** a **Form2**.  
  
     In **Form2** vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
4.  Eliminare l'oggetto **OrdersBindingNavigator** dalla barra dei componenti.  
  
     **OrdersBindingNavigator** scompare da **Form2**.  
  
## Aggiunta di una query TableAdapter a Form2 per caricare gli ordini del cliente selezionato nel Form1  
  
#### Per creare una query TableAdapter  
  
1.  Fare doppio clic sul file **NorthwindDataSet.xsd** in **Esplora soluzioni**.  
  
2.  Fare clic con il pulsante destro del mouse su **OrdersTableAdapter** e selezionare **Aggiungi query**.  
  
3.  Lasciare l'opzione predefinita di **Usa istruzioni SQL** e scegliere **Avanti**.  
  
4.  Lasciare l'opzione predefinita di **SELECT che restituisce righe** e scegliere **Avanti**.  
  
5.  Aggiungere una clausola WHERE alla query per restituire gli `Orders` in base al `CustomerID`.  La query dovrebbe essere simile alla seguente:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Verificare che la sintassi dei parametri sia corretta per il database.  In Microsoft Access, ad esempio, la clausola WHERE presenta la seguente sintassi: `WHERE CustomerID = ?`.  
  
6.  Scegliere **Avanti**.  
  
7.  Nel campo **Nome metodo** relativo a **Riempi un DataTable**, digitare `FillByCustomerID`.  
  
8.  Deselezionare l'opzione **Restituisci una DataTable**, quindi scegliere **Avanti**.  
  
9. Scegliere **Fine**.  
  
## Creazione di un metodo su Form2 al quale passare i dati  
  
#### Per creare un metodo al quale passare i dati  
  
1.  Fare clic con il pulsante destro del mouse su **Form2** e selezionare **Visualizza codice** per aprire **Form2** nell'**editor di codice**.  
  
2.  Aggiungere il codice riportato di seguito a **Form2** dopo il metodo `Form2_Load`:  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## Creazione di un metodo su Form1 per il passaggio dei dati e la visualizzazione di Form2  
  
#### Per creare un metodo per il passaggio dei dati a Form2  
  
1.  In **Form1** fare clic con il pulsante destro del mouse sulla griglia dati del cliente, quindi scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** fare clic su **Eventi**.  
  
3.  Fare doppio clic sull'evento **CellDoubleClick**.  
  
     Verrà visualizzato l'editor del codice.  
  
4.  Aggiornare la definizione del metodo in modo che corrisponda all'esempio seguente:  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## Esecuzione dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
-   Fare doppio clic sul record di un cliente in **Form1** per aprire **Form2** e visualizzare gli ordini di quel cliente.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta passati i dati da un form all'altro.  È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Modifica del set di dati per aggiungere o rimuovere oggetti di database.  Per altre informazioni, vedere [Procedura: modificare un dataset](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
-   Aggiunta di funzionalità per il salvataggio dei dati nel database.  Per altre informazioni, vedere [Procedura: salvare le modifiche di un dataset in un database](../data-tools/how-to-save-dataset-changes-to-a-database.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)