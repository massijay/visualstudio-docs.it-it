---
title: "Procedura dettagliata: personalizzazione del comportamento di Insert, Update e Delete delle classi di entit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: personalizzazione del comportamento di Insert, Update e Delete delle classi di entit&#224;
In [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md) è disponibile un'area di progettazione visiva per la creazione e la modifica di classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] \(classi di entità\) basate sugli oggetti in un database.Mediante [LINQ to SQL](../Topic/LINQ%20to%20SQL.md), è possibile utilizzare la tecnologia LINQ per accedere ai database SQL.Per ulteriori informazioni, vedere [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 Per impostazione predefinita, la logica per eseguire gli aggiornamenti viene fornita dal runtime [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].Nel runtime vengono create istruzioni Insert, Update e Delete predefinite in base allo schema della tabella \(definizioni di colonna e informazioni sulla chiave primaria\).Quando non si desidera utilizzare il comportamento predefinito, è possibile configurare il comportamento di aggiornamento e definire stored procedure specifiche per eseguire i comandi di inserimento, aggiornamento ed eliminazione necessari per l'utilizzo dei dati nel database.Questa operazione può essere eseguita anche quando non viene generato il comportamento predefinito, ad esempio quando viene eseguito il mapping delle classi di entità alle visualizzazioni.Inoltre, è possibile eseguire l'override del comportamento di aggiornamento predefinito quando il database richiede l'accesso alla tabella tramite stored procedure.Per ulteriori informazioni, vedere [Personalizzazione delle operazioni tramite l'utilizzo di stored procedure](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md).  
  
> [!NOTE]
>  In questa procedura dettagliata è richiesta la disponibilità delle stored procedure **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** per il database Northwind.Per informazioni dettagliate sulla creazione di queste stored procedure, vedere [Procedura dettagliata: creazione delle stored procedure di aggiornamento per la tabella Customers Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 In questa procedura dettagliata vengono forniti i passaggi da completare per eseguire l'override del comportamento in fase di esecuzione LINQ to SQL predefinito per salvare i dati in un database utilizzando stored procedure.  
  
 In questa procedura dettagliata viene illustrato come completare le seguenti attività:  
  
-   Creazione di una nuova applicazione Windows Form e aggiunta ad essa di un file [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
-   Creazione di una classe di entità con mapping alla tabella Customers di Northwind.  
  
-   Creazione dell'origine dati di un oggetto che fa riferimento alla classe LINQ to SQL Customer.  
  
-   Creazione di un Windows Form che contiene un oggetto <xref:System.Windows.Forms.DataGridView> associato alla classe Customer.  
  
-   Implementazione della funzionalità di salvataggio per il form.  
  
-   Creazione di metodi <xref:System.Data.Linq.DataContext> mediante l'aggiunta di stored procedure a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configurazione della classe Customer in modo che utilizzi stored procedure per l'esecuzione dei comandi di inserimento, aggiornamento ed eliminazione.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre dei seguenti elementi:  
  
-   Accesso alla versione SQL Server del database di esempio Northwind.Per ulteriori informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
-   Stored procedure **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** per il database Northwind.Per ulteriori informazioni, vedere [Procedura dettagliata: creazione delle stored procedure di aggiornamento per la tabella Customers Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## Creazione di un'applicazione e aggiunta di classi LINQ to SQL  
 Poiché verranno utilizzate classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] e verranno visualizzati i dati in un Windows Form, creare una nuova applicazione Windows Form e aggiungere un file di classi LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per creare un nuovo progetto Applicazione Windows che contenga classi LINQ to SQL  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome UpdatingwithSProcsWalkthrough.  
  
    > [!NOTE]
    >  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] è supportato nei progetti di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e di C\#.Pertanto, creare il nuovo progetto in uno di questi linguaggi.  
  
3.  Fare clic sul modello **Applicazione Windows Form**, quindi scegliere **OK**.Per ulteriori informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto UpdatingwithSProcsWalkthrough viene creato e aggiunto a **Esplora soluzioni**.  
  
4.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
5.  Fare clic sul modello **Classi LINQ to SQL** e digitare Northwind.dbml nella casella **Nome**.  
  
6.  Scegliere **Aggiungi**.  
  
     Viene aggiunto al progetto un file di classi LINQ to SQL vuoto \(Northwind.dbml\) e viene aperto [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Creazione della classe di entità Customer e dell'origine dati di un oggetto  
 Creare classi [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] con mapping alle tabelle di database trascinando le tabelle da **Esplora server**\/**Esplora database** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Il risultato è rappresentato da classi di entità LINQ to SQL con mapping alle tabelle nel database.Dopo aver creato le classi di entità, è possibile utilizzarle come origini dati di un oggetto analogamente alle altre classi che dispongono di proprietà pubbliche.  
  
#### Per creare una classe di entità Customer e configurare un'origine dati con tale classe  
  
1.  In **Esplora server**\/**Esplora database**, individuare la tabella Customer nella versione SQL Server del database di esempio Northwind.Per ulteriori informazioni, vedere [Procedura dettagliata: connettersi al database Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Trascinare il nodo **Customers** da **Esplora server**\/**Esplora database** nell'area di [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Viene creata una classe di entità denominata **Customer**,che presenta proprietà corrispondenti alle colonne della tabella Customers.La classe di entità viene denominata **Customer** \(e non **Customers**\) perché rappresenta un solo cliente della tabella Customers.  
  
    > [!NOTE]
    >  Questo comportamento di ridenominazione viene definito *pluralizzazione*e può essere attivato o disattivato nella [Finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md).Per ulteriori informazioni, vedere [Procedura: attivare e disattivare la pluralizzazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  Scegliere **Compila UpdatingwithSProcsWalkthrough** dal menu **Compila** per compilare il progetto.  
  
4.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
5.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
6.  Nella pagina **Seleziona un tipo di origine dati** fare clic su **Oggetto**, quindi su **Avanti**.  
  
7.  Espandere il nodo **UpdatingwithSProcsWalkthrough**, quindi individuare e selezionare la classe **Customer**.  
  
    > [!NOTE]
    >  Se la classe **Customer** non è disponibile, chiudere la procedura guidata, compilare il progetto ed eseguire nuovamente la procedura guidata.  
  
8.  Fare clic su **Fine** per creare l'origine dati e aggiungere la classe di entità **Customer** alla finestra **Origini dati**.  
  
## Creazione di un controllo DataGridView per visualizzare i dati dei clienti in un Windows Form  
 Creare controlli associati alle classi di entità trascinando gli elementi delle origini dati [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] dalla finestra **Origini dati** in un Windows Form.  
  
#### Per aggiungere controlli associati alle classi di entità  
  
1.  Aprire Form1 nella visualizzazione Progettazione.  
  
2.  Trascinare il nodo **Customer** dalla finestra **Origini dati** in Form1.  
  
    > [!NOTE]
    >  Per visualizzare la finestra **Origini dati**, scegliere **Mostra origini dati** dal menu **Dati**.  
  
3.  Aprire Form1 nell'editor del codice.  
  
4.  Aggiungere al form il seguente codice, che verrà applicato all'intero form, all'esterno di un metodo specifico ma all'interno della classe Form1:  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Creare un gestore eventi per l'evento `Form_Load` e aggiungere il seguente codice al gestore:  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## Implementazione della funzionalità di salvataggio  
 Per impostazione predefinita, il pulsante Salva non è abilitato e la funzionalità di salvataggio non è implementata.Inoltre, quando vengono creati controlli associati a dati per le origini dati di un oggetto, non viene aggiunto codice automaticamente per salvare i dati modificati nel database.In questa sezione viene illustrato come abilitare il pulsante Salva e implementare la funzionalità di salvataggio per gli oggetti [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
#### Per implementare la funzionalità di salvataggio  
  
1.  Aprire Form1 nella visualizzazione Progettazione.  
  
2.  Selezionare il pulsante Salva in **CustomerBindingNavigator** \(il pulsante con l'icona del disco floppy\).  
  
3.  Nella finestra **Proprietà** impostare la proprietà **Enabled** su **True**.  
  
4.  Fare doppio clic sul pulsante Salva per creare un gestore eventi e passare all'editor del codice.  
  
5.  Aggiungere il seguente codice nel gestore eventi del pulsante Salva:  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## Override del comportamento predefinito per l'esecuzione degli aggiornamenti \(comandi di inserimento, aggiornamento ed eliminazione\)  
  
#### Per eseguire l'override del comportamento di aggiornamento predefinito  
  
1.  Aprire il file LINQ to SQL in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].\(fare doppio clic sul file **Northwind.dbml** in **Esplora soluzioni**\).  
  
2.  In **Esplora server**\/**Esplora database** espandere il nodo **Stored procedure** dei database Northwind e individuare le stored procedure **InsertCustomers**, **UpdateCustomers** e **DeleteCustomers**.  
  
3.  Trascinare tutte e tre le stored procedure in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Le stored procedure vengono aggiunte al riquadro dei metodi come metodi <xref:System.Data.Linq.DataContext>.Per ulteriori informazioni, vedere [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selezionare la classe di entità **Customer** in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  Nella finestra **Proprietà** selezionare la proprietà **Insert**.  
  
6.  Fare clic sui puntini di sospensione \(...\) accanto a **Usa fase di esecuzione** per aprire la finestra di dialogo **Configura comportamento**.  
  
7.  Selezionare **Personalizza**.  
  
8.  Selezionare il metodo **InsertCustomers** nell'elenco **Personalizza**.  
  
9. Fare clic su **Applica** per salvare la configurazione relativa alla classe e al comportamento selezionati.  
  
    > [!NOTE]
    >  È possibile continuare a configurare il comportamento per ogni combinazione di classe\/comportamento purché si faccia clic su **Applica** dopo ogni modifica apportata.Se si modifica la classe o il comportamento prima di fare clic su **Applica**, verrà visualizzata una finestra di dialogo di avviso che offre la possibilità di applicare le eventuali modifiche apportate.  
  
10. Selezionare **Aggiorna** nell'elenco **Comportamento**.  
  
11. Selezionare **Personalizza**.  
  
12. Selezionare il metodo **UpdateCustomers** nell'elenco **Personalizza**.  
  
     Controllare l'elenco di **Argomenti metodo** e **Proprietà classe** e notare che sono disponibili due **Argomenti metodo** e due **Proprietà classe** per alcune colonne nella tabella.In tal modo, vengono facilitati il rilevamento delle modifiche e la creazione di istruzioni che verifichino la presenza di eventuali violazioni di concorrenza.  
  
13. Eseguire il mapping dell'argomento di metodo **Original\_CustomerID** alla proprietà di classe **CustomerID \(Original\)**.  
  
    > [!NOTE]
    >  Per impostazione predefinita, verrà eseguito il mapping degli argomenti di metodo alle proprietà di classe quando i nomi corrispondono.Se i nomi di proprietà vengono modificati e non vi è più corrispondenza tra quelli della tabella e quelli della classe di entità, potrebbe essere necessario selezionare la proprietà di classe equivalente a cui eseguire il mapping nel caso in cui Progettazione relazionale oggetti non sia in grado di determinare il mapping corretto.Inoltre, se per gli argomenti di metodo non sono disponibili proprietà di classe valide a cui eseguire il mapping, è possibile impostare il valore **Proprietà classe** su **\(Nessuna\)**.  
  
14. Fare clic su **Applica** per salvare la configurazione relativa alla classe e al comportamento selezionati.  
  
15. Selezionare **Elimina** nell'elenco **Comportamento**.  
  
16. Selezionare **Personalizza**.  
  
17. Selezionare il metodo **DeleteCustomers** nell'elenco **Personalizza**.  
  
18. Eseguire il mapping dell'argomento di metodo **Original\_CustomerID** alla proprietà di classe **CustomerID \(Original\)**.  
  
19. Scegliere **OK**.  
  
> [!NOTE]
>  Sebbene non sia un problema per questa procedura dettagliata, è opportuno notare che [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] gestisce i valori generati dal database automaticamente per le colonne identity \(incremento automatico\), rowguidcol \(GUID generato dal database\) e timestamp durante le operazioni di inserimento e aggiornamento.I valori degli altri tipi di colonne sono costituiti da valori null non previsti.Per restituire i valori generati dal database, è necessario impostare manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> su `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> su uno dei seguenti valori: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> o <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Test dell'applicazione  
 Eseguire nuovamente l'applicazione per verificare che la stored procedure **UpdateCustomers** aggiorni correttamente il record dei clienti nel database.  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere F5.  
  
2.  Modificare un record nella griglia per testare il comportamento di Update.  
  
3.  Aggiungere un nuovo record per testare il comportamento di Insert.  
  
4.  Fare clic sul pulsante Salva per salvare le modifiche nel database.  
  
5.  Chiudere il form.  
  
6.  Premere F5 e verificare che il record aggiornato e quello appena inserito siano stati salvati in modo permanente.  
  
7.  Eliminare il nuovo record creato nel passaggio 3 per testare il comportamento di Delete.  
  
8.  Fare clic sul pulsante Salva per inviare le modifiche e rimuovere il record eliminato dal database.  
  
9. Chiudere il form.  
  
10. Premere F5 e verificare che il record eliminato sia stato rimosso dal database.  
  
    > [!NOTE]
    >  Se l'applicazione utilizza SQL Server Express Edition, a seconda del valore della proprietà **Copia nella directory di output** del file di database, è possibile che le modifiche non vengano visualizzate quando si preme F5 nel passaggio 10.Per ulteriori informazioni, vedere [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo la creazione delle classi di entità [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].È possibile apportare alcuni miglioramenti a questa applicazione, tra cui:  
  
-   Implementazione del controllo della concorrenza durante gli aggiornamenti.Per informazioni, vedere [Cenni preliminari sulla concorrenza ottimistica](../Topic/Optimistic%20Concurrency:%20Overview.md).  
  
-   Aggiunta di query LINQ per filtrare i dati.Per informazioni, vedere [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Query LINQ to SQL](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: assegnare stored procedure per l'esecuzione dei comandi di aggiornamento, inserimento ed eliminazione \(Progettazione relazionale oggetti\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [PAVE What's New for Data Application Development in Visual Studio 2012](http://msdn.microsoft.com/it-it/3d50d68f-5f44-4915-842f-6d42fce793f1)