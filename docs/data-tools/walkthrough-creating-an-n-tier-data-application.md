---
title: "Procedura dettagliata: creazione di un&#39;applicazione dati a pi&#249; livelli | Microsoft Docs"
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
  - "applicazioni a più livelli, creazione"
  - "applicazioni a più livelli, procedure dettagliate"
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 48
caps.handback.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: creazione di un&#39;applicazione dati a pi&#249; livelli
Le applicazioni dati *a più livelli* sono applicazioni con accesso ai dati e sono separate in più livelli logici.  La separazione dei componenti dell'applicazione in livelli discreti aumenta la manutenibilità e la scalabilità dell'applicazione  mediante l'adozione semplificata di nuove tecnologie che possono essere applicate a un singolo livello senza la necessità di riprogettare l'intera soluzione.  L'architettura a più livelli include un livello di presentazione, un livello intermedio e un livello dati.  Il livello intermedio include in genere un livello di accesso ai dati, un livello di logica di business e componenti condivisi quali l'autenticazione e la convalida.  Il livello dati include un database relazionale.  Le applicazioni a più livelli in genere archiviano le informazioni riservate nel livello di accesso ai dati del livello intermedio per mantenere l'isolamento dagli utenti finali che accedono al livello di presentazione.  Per altre informazioni, vedere [Cenni preliminari sull'applicazione dati a più livelli](../data-tools/n-tier-data-applications-overview.md).  
  
 Per separare i vari livelli in un'applicazione a più livelli, è possibile creare progetti discreti per ogni livello da includere nell'applicazione.  I dataset tipizzati contengono una proprietà `DataSet Project` che determina in quali progetti deve essere inserito il codice generato del dataset e di `TableAdapter`.  
  
 In questa procedura dettagliata è illustrato come separare il codice del dataset e di `TableAdapter` in progetti di librerie di classi discreti usando **Progettazione DataSet**.  Dopo aver separato il codice del dataset e di TableAdapter, si creerà un servizio [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) per effettuare le chiamate nel livello di accesso ai dati.  Infine, si creerà un'applicazione Windows Form come livello di presentazione.  Questo livello accede ai dati dal servizio dati.  
  
 Durante questa procedura dettagliata, verranno eseguiti i passaggi seguenti:  
  
-   Creare una nuova soluzione a più livelli che contiene più progetti.  
  
-   Aggiungere due progetti di libreria di classi alla soluzione a più livelli.  
  
-   Creare un dataset tipizzato con la **Configurazione guidata origine dati**.  
  
-   Separare il codice del dataset e di [TableAdapters](../Topic/TableAdapters.md) generato in progetti discreti.  
  
-   Creare un servizio Windows Communication Foundation \(WCF\) per effettuare chiamate nel livello di accesso ai dati.  
  
-   Creare funzioni nel servizio per recuperare i dati dal livello di accesso ai dati.  
  
-   Creare un'applicazione Windows Form come livello di presentazione.  
  
-   Creare i controlli Windows Form associati all'origine dati.  
  
-   Scrivere il codice per popolare le tabelle dati.  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "PlayVideo") Per una versione video di questo argomento, vedere [Procedura: creazione di un'applicazione dati a più livelli](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione della soluzione a più livelli e della libreria di classi per contenere il dataset \(DataEntityTier\)  
 Il primo passaggio di questa procedura dettagliata prevede la creazione di una soluzione e di due progetti di libreria di classi.  La prima libreria di classi conterrà il dataset \(la classe DataSet tipizzato e gli oggetti DataTable generati che conterranno i dati dell'applicazione\).  Il progetto viene usato come livello di entità di dati dell'applicazione e di norma si trova nel livello intermedio.  [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) consente di creare il dataset iniziale e di separare automaticamente il codice in due librerie di classi.  
  
> [!NOTE]
>  Assicurarsi di assegnare il nome corretto al progetto e alla soluzione prima di fare clic su **OK**.  In tal modo sarà più semplice completare questa procedura dettagliata.  
  
#### Per creare la soluzione a più livelli e la libreria di classi DataEntityTier  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
    > [!NOTE]
    >  **Progettazione DataSet** è supportato nei progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e C\#.  Creare il nuovo progetto in uno di questi linguaggi  
  
2.  Nel riquadro **Tipi di progetto** della finestra di dialogo **Nuovo progetto** scegliere **Windows**.  
  
3.  Scegliere il modello **Libreria di classi**.  
  
4.  Assegnare il nome DataEntityTier al progetto.  
  
5.  Assegnare il nome NTierWalkthrough alla soluzione.  
  
6.  Fare clic su **OK**.  
  
     Una soluzione NTierWalkthrough che contiene il progetto DataEntityTier viene creata e aggiunta a **Esplora soluzioni**.  
  
## Creazione della libreria di classi per contenere gli oggetti TableAdapter \(DataAccessTier\)  
 Il passaggio successivo alla creazione del progetto DataEntityTier prevede la creazione di un altro progetto di libreria di classi.  Questo progetto conterrà gli oggetti `TableAdapter` generati ed è definito come il *livello di accesso ai dati* dell'applicazione.  Tale livello contiene le informazioni richieste per la connessione al database e in genere si trova nel livello intermedio.  
  
#### Per creare la nuova libreria di classi per gli oggetti TableAdapter  
  
1.  Aggiungere un nuovo progetto alla soluzione NTierWalkthrough dal menu **File**.  
  
2.  Nel riquadro **Modelli** della finestra di dialogo **Nuovo progetto** scegliere **Libreria di classi**.  
  
3.  Assegnare al progetto il nome DataAccessTier e fare clic su **OK**.  
  
     Il progetto DataAccessTier viene creato e aggiunto alla soluzione NTierWalkthrough.  
  
## Creazione del set di dati  
 Il passaggio successivo consiste nella creazione di un dataset tipizzato.  I dataset tipizzati sono creati con la classe DataSet \(comprese le classi DataTable\) e le classi `TableAdapter`, in un singolo progetto.  Tutte le classi vengono generate in un unico file. Quando il dataset e gli oggetti `TableAdapter` vengono separati in progetti diversi, è la classe DataSet che viene spostata nell'altro progetto, mentre le classi `TableAdapter` restano nel progetto originale.  Di conseguenza, è necessario creare il dataset nel progetto che alla fine conterrà gli oggetti `TableAdapter` \(il progetto DataAccessTier\).  Il dataset viene creato con la **Configurazione guidata origine dati**.  
  
> [!NOTE]
>  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni su come impostare il database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### Per creare il dataset  
  
1.  Fare clic su DataAccessTier in **Esplora soluzioni**.  
  
2.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
3.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
4.  Nella pagina **Seleziona un tipo di origine dati** fare clic su **Database**, quindi su **Avanti**.  
  
5.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
     Se disponibile nell'elenco a discesa, scegliere la connessione dati al database di esempio Northwind.  
  
     \-oppure\-  
  
     Scegliere **Nuova connessione** per aprire la finestra di dialogo **Aggiungi connessione**.  
  
6.  Se il database richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi fare clic su **Avanti**.  
  
    > [!NOTE]
    >  Se è stato selezionato un file di database locale al posto della connessione a SQL Server, potrebbe venire richiesto di aggiungere il file al progetto.  Fare clic su **Sì** per aggiungere il file di database al progetto.  
  
7.  Scegliere **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione**.  
  
8.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
9. Selezionare le caselle di controllo per le tabelle **Customers** e **Orders**, quindi fare clic su **Fine**.  
  
     NorthwindDataSet viene aggiunto al progetto DataAccessTier e viene visualizzato nella finestra **Origini dati**.  
  
## Separazione degli oggetti TableAdapter dal dataset  
 Dopo avere creato il dataset, separare la classe DataSet generata dagli oggetti TableAdapter.  Questa operazione può essere eseguita impostando la proprietà **Progetto DataSet** sul nome del progetto nel quale archiviare la classe DataSet separata.  
  
#### Per separare gli oggetti TableAdapter dal dataset  
  
1.  Fare doppio clic su **NorthwindDataSet.xsd** in **Esplora soluzioni** per aprire il dataset in **Progettazione DataSet**.  
  
2.  Fare clic su un'area vuota della finestra di progettazione.  
  
3.  Trovare il nodo **Progetto DataSet** nella finestra **Proprietà**.  
  
4.  Nell'elenco **Progetto DataSet** scegliere **DataEntityTier**.  
  
5.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
 Il dataset e gli oggetti TableAdapter sono separati nei due progetti di libreria di classi.  Il progetto che originalmente conteneva l'intero dataset \(DataAccessTier\) ora contiene solo gli oggetti TableAdapter.  Il progetto definito nella proprietà **Progetto DataSet** \(DataEntityTier\) contiene il dataset tipizzato NorthwindDataSet.Dataset.Designer.vb \(o NorthwindDataSet.Dataset.Designer.cs\).  
  
> [!NOTE]
>  Quando si separano i dataset e gli oggetti TableAdapter \(impostando la proprietà **Progetto DataSet**\), le classi parziali del dataset presenti nel progetto non vengono spostate automaticamente.  Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
## Creazione di una nuova applicazione di servizio  
 Dal momento che questa procedura dettagliata spiega come accedere al livello di accesso ai dati con un servizio WCF, è necessario creare una nuova applicazione del servizio WCF.  
  
#### Per creare una nuova applicazione del servizio WCF  
  
1.  Aggiungere un nuovo progetto alla soluzione NTierWalkthrough dal menu **File**.  
  
2.  Nel riquadro **Tipi di progetto** della finestra di dialogo **Nuovo progetto** scegliere **WCF**.  Nel riquadro **Modelli** scegliere **Libreria del servizio WCF**.  
  
3.  Assegnare al progetto il nome DataService e fare clic su **OK**.  
  
     Il progetto DataService viene creato e aggiunto alla soluzione NTierWalkthrough.  
  
## Creazione di metodi nel livello di accesso ai dati per restituire i dati dei clienti e degli ordini  
 Il servizio dati deve chiamare due metodi nel livello di accesso ai dati: GetCustomers e GetOrders.  Questi metodi restituiscono le tabelle Customers e Orders di Northwind.  Creare i metodi GetCustomers e GetOrders nel progetto DataAccessTier.  
  
#### Per creare un metodo nel livello di accesso ai dati per restituire la tabella Customers  
  
1.  Fare doppio clic su NorthwindDataSet.xsd in **Esplora soluzioni** per aprire il dataset in [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
2.  Fare clic con il pulsante destro del mouse su CustomersTableAdapter e scegliere **Aggiungi query** per aprire l'oggetto [TableAdapter \(query, configurazione guidata\)](../data-tools/editing-tableadapters.md).  
  
3.  Nella pagina **Seleziona un tipo di comando** lasciare il valore predefinito **Usa istruzioni SQL** e fare clic su **Avanti**.  
  
4.  Nella pagina **Seleziona un tipo di query** lasciare il valore predefinito **SELECT che restituisce righe** e fare clic su **Avanti**.  
  
5.  Nella pagina **Specifica un'istruzione SQL SELECT** lasciare la query predefinita e fare clic su **Avanti**.  
  
6.  Nella sezione **Restituisci un DataTable** della pagina **Scegliere i metodi per generare** digitare GetCustomers in **Nome metodo**.  
  
7.  Scegliere **Fine**.  
  
#### Per creare un metodo nel livello di accesso ai dati per restituire la tabella Orders  
  
1.  Fare clic con il pulsante destro del mouse su OrdersTableAdapter e scegliere **Aggiungi query**.  
  
2.  Nella pagina **Seleziona un tipo di comando** lasciare il valore predefinito **Usa istruzioni SQL** e fare clic su **Avanti**.  
  
3.  Nella pagina **Seleziona un tipo di query** lasciare il valore predefinito **SELECT che restituisce righe** e fare clic su **Avanti**.  
  
4.  Nella pagina **Specifica un'istruzione SQL SELECT** lasciare la query predefinita e fare clic su **Avanti**.  
  
5.  Nella sezione **Restituisci un DataTable** della pagina **Scegliere i metodi per generare** digitare GetOrders in **Nome metodo**.  
  
6.  Scegliere **Fine**.  
  
7.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## Aggiunta di un riferimento ai livelli di entità di dati e di accesso ai dati nel servizio dati  
 Dal momento che il servizio dati richiede le informazioni dal dataset e dagli oggetti TableAdapter, è necessario aggiungere riferimenti ai progetti DataEntityTier e DataAccessTier.  
  
#### Per aggiungere riferimenti al servizio dati  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro su DataService e scegliere **Aggiungi riferimento**.  
  
2.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti**.  
  
3.  Selezionare entrambi i progetti **DataAccessTier** e **DataEntityTier**.  
  
4.  Fare clic su **OK**.  
  
## Aggiunta di funzioni al servizio per chiamare i metodi GetCustomers e GetOrders nel livello di accesso ai dati  
 Ora che il livello di accesso ai dati contiene i metodi per restituire i dati, creare i metodi nel servizio dati per chiamare i metodi nel livello di accesso ai dati.  
  
> [!NOTE]
>  Per i progetti C\# è necessario aggiungere un riferimento all'assemby `System.Data.DataSetExtensions` per eseguire la compilazione del codice seguente.  
  
#### Per creare le funzioni GetCustomers e GetOrders nel servizio dati  
  
1.  Nel progetto **DataService** fare doppio clic su IService1.vb o IService1.cs.  
  
2.  Aggiungere il codice seguente sotto il commento **Aggiungere qui le operazioni del servizio**:  
  
    ```vb#  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```c#  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  Nel progetto DataService fare doppio clic su Service1.vb o Service1.cs.  
  
4.  Aggiungere il codice seguente alla classe Service1:  
  
    ```vb#  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```c#  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
  
    }  
    ```  
  
5.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
## Creazione di un livello di presentazione per visualizzare i dati dal servizio dati  
 Ora che la soluzione contiene il servizio dati con i metodi che effettuano chiamate nel livello di accesso ai dati, creare un altro progetto che effettuerà le chiamate nel servizio dati e presenterà i dati agli utenti.  In questa procedura dettagliata, creare un'applicazione Windows Form; si tratta del livello di presentazione dell'applicazione a più livelli.  
  
#### Per creare il progetto livello di presentazione  
  
1.  Aggiungere un nuovo progetto alla soluzione NTierWalkthrough dal menu **File**.  
  
2.  Nel riquadro **Tipi di progetto** della finestra di dialogo **Nuovo progetto** scegliere **Windows**.  Nel riquadro **Modelli** scegliere **Applicazione Windows Form**.  
  
3.  Assegnare al progetto il nome PresentationTier e fare clic su **OK**.  
  
4.  Il progetto PresentationTier viene creato e aggiunto alla soluzione NTierWalkthrough.  
  
## Impostazione del progetto PresentationTier come progetto di avvio  
 Dal momento che il livello di presentazione è in realtà l'applicazione client usata per presentare i dati e interagire con essi, è necessario impostare il progetto PresentationTier come progetto di avvio.  
  
#### Impostazione del nuovo livello del progetto come progetto di avvio  
  
-   In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **PresentationTier** e scegliere **Imposta come progetto di avvio**.  
  
## Aggiunta di riferimenti al livello di presentazione  
 Per accedere ai metodi nel servizio, l'applicazione client PresentationTier richiede un riferimento al servizio dati.  È richiesto inoltre un riferimento al dataset per abilitare la condivisione dei tipi da parte del servizio WCF.  Se non si abilita la condivisione dei tipi con il servizio dati, il codice aggiunto alla classe DataSet parziale non sarà disponibile per il livello di presentazione.  Dal momento che di norma si aggiunge codice, ad esempio il codice per la convalida, agli eventi di modifica di righe e colonne di una tabella dati, probabilmente sarà necessario accedere al codice dal client.  
  
#### Per aggiungere un riferimento al livello di presentazione  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su PresentationTier e scegliere **Aggiungi riferimento**.  
  
2.  Nella finestra di dialogo **Aggiungi riferimento** fare clic sulla scheda **Progetti**.  
  
3.  Selezionare **DataEntityTier** e fare clic su **OK**.  
  
#### Per aggiungere il riferimento a un servizio al livello di presentazione  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su PresentationTier e scegliere **Aggiungi riferimento al servizio**.  
  
2.  Nella finestra di dialogo **Aggiungi riferimento al servizio** fare clic su **Individua**.  
  
3.  Selezionare **Service1** e fare clic su **OK**.  
  
    > [!NOTE]
    >  Se sono presenti più servizi nel computer in uso, selezionare il servizio creato in precedenza in questa procedura dettagliata, ossia quello contenente i metodi GetCustomers e GetOrders.  
  
## Aggiunta di DataGridView al form per visualizzare i dati restituiti dal servizio dati  
 Dopo aver aggiunto il riferimento a un servizio dati, i dati restituiti dal servizio vengono popolati automaticamente nella finestra **Origini dati**.  
  
#### Per aggiungere due DataGridView associati a dati al form  
  
1.  Selezionare il progetto PresentationTier in **Esplora soluzioni**.  
  
2.  Nella finestra **Origini dati**, espandere **NorthwindDataSet** e trovare il nodo **Customers**.  
  
3.  Trascinare il nodo **Customers** in Form1.  
  
4.  Nella finestra **Origini dati** espandere il nodo **Customers** e trovare il nodo **Orders** correlato, cioè il nodo **Orders** annidato nel nodo **Customers**.  
  
5.  Trascinare il nodo **Orders** correlato in Form1.  
  
6.  Fare doppio clic su un'area vuota del form per creare un gestore eventi `Form1_Load`.  
  
7.  Aggiungere il codice seguente al gestore eventi `Form1_Load`.  
  
    ```vb#  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```c#  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## Aumento della dimensione massima dei messaggi consentita dal servizio  
 Dal momento che il servizio restituisce i dati dalle tabelle Customers e Orders, il valore predefinito per maxReceivedMessageSize non è sufficiente per contenere i dati e deve essere aumentato.  Per questa procedura dettagliata si imposterà il valore su 6553600.  Il valore verrà cambiato nel client e il riferimento al servizio verrà aggiornato automaticamente.  
  
> [!NOTE]
>  La dimensione predefinita più bassa è usata per limitare l'esposizione ad attacchi Denial of Service \(DoS\).  Per altre informazioni, vedere <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### Per aumentare il valore di maxReceivedMessageSize  
  
1.  In **Esplora soluzioni** fare doppio clic sul file app.config nel progetto PresentationTier.  
  
2.  Trovare l'attributo di dimensione **maxReceivedMessage** e impostare il valore su `6553600`.  
  
## Verifica dell'applicazione  
 Eseguire l'applicazione.  I dati vengono recuperati dal servizio dati e visualizzati nel form.  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere F5.  
  
2.  I dati delle tabelle Customers e Orders vengono recuperati dal servizio dati e visualizzati nel form.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, è possibile eseguire diverse operazioni dopo il salvataggio dei dati correlati nell'applicazione basata su Windows.  È possibile ad esempio apportare i seguenti miglioramenti a questa applicazione:  
  
-   Aggiungere la convalida al dataset.  Per informazioni, vedere [Procedura dettagliata: aggiunta della convalida a un'applicazione dati a più livelli](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md).  
  
-   Aggiungere al servizio altri metodi per l'aggiornamento dei dati nel database.  
  
## Vedere anche  
 [Utilizzo dei dataset nelle applicazioni a più livelli](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)