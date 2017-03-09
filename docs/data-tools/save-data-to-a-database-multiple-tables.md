---
title: "Procedura dettagliata: salvataggio di dati in un database (a pi&#249; tabelle) | Microsoft Docs"
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
  - "dati [Visual Studio], salvataggio"
  - "dati [Visual Studio], aggiornamento"
  - "salvataggio di dati, procedure dettagliate"
  - "aggiornamento di dataset, procedure dettagliate"
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: salvataggio di dati in un database (a pi&#249; tabelle)
Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database.  In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database.  Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
 È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter.  Quando si trascinano elementi dalla finestra **Origini dati**, il codice per salvare i dati viene automaticamente aggiunto per la prima tabella rilasciata in un form.  Eventuali altre tabelle aggiunte a un form richiedono l'aggiunta manuale del codice necessario per salvare i dati.  In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per altre informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto **Applicazione Windows**.  
  
-   Creazione e configurazione di un'origine dati nell'applicazione con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Impostazione dei controlli degli elementi nella [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di controlli associati a dati con il trascinamento di elementi dalla finestra **Origini dati** nel form.  
  
-   Modifica di alcuni record in ogni tabella nel set di dati.  
  
-   Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione dell'applicazione Windows  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  L'assegnazione di un nome al progetto è facoltativa in questo passaggio, ma al progetto verrà ugualmente assegnato un nome per poterlo salvare in seguito.  
  
#### Per creare il nuovo progetto Applicazione Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnare al progetto il nome `UpdateMultipleTablesWalkthrough`.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **UpdateMultipleTablesWalkthrough** viene creato e aggiunto in **Esplora soluzioni**.  
  
## Creazione dell'origine dati  
 Questo passaggio consente di creare un'origine dati dal database Northwind usando la **Configurazione guidata origine dati**.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
#### Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         \-oppure\-  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi\/Modifica connessione**.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati riservati, quindi scegliere **Avanti**.  
  
6.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** fare clic su **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare le tabelle **Customers** e **Orders**, quindi scegliere **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nella finestra **Origini dati**.  
  
## Impostazione dei controlli da creare  
 Per questa procedura guidata i dati nella tabella `Customers` verranno visualizzati in singoli controlli nel layout **Dettagli**.  I dati della tabella `Orders` verranno visualizzati in un controllo <xref:System.Windows.Forms.DataGridView> nel layout **Griglia**.  
  
#### Per impostare il tipo di visualizzazione degli elementi della finestra Origini dati  
  
1.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
2.  Impostare il controllo della tabella **Customers** sui singoli controlli selezionando **Dettagli** nell'elenco dei controlli del nodo **Customers**.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Creazione del form associato a dati  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### Per creare controlli associati a dati nel form  
  
1.  Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
2.  Trascinare il nodo **Orders** correlato dalla finestra **Origini dati** in **Form1**.  
  
    > [!NOTE]
    >  Il nodo **Orders** correlato si trova sotto la colonna **Fax** ed è un nodo figlio del nodo **Customers**.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [OrdersTableAdapter](../data-tools/tableadapter-overview.md) e <xref:System.Windows.Forms.BindingSource>.  
  
## Aggiunta di codice per aggiornare il database  
 È possibile aggiornare il database chiamando i metodi `Update` degli oggetti TableAdapter **Customers** e **Orders**.  Per impostazione predefinita, un gestore eventi per il pulsante **Salva** di <xref:System.Windows.Forms.BindingNavigator> viene aggiunto al codice del form per inviare gli aggiornamenti al database.  Questa procedura modifica tale codice per inviare gli aggiornamenti nell'ordine corretto ed eliminare così la possibilità di errori di integrità referenziale.  Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try\-catch.  È possibile modificare il codice per soddisfare le esigenze dell'applicazione.  
  
> [!NOTE]
>  Per motivi di chiarezza, questa procedura guidata non usa una transazione, ma, se si devono aggiornare due o più tabelle correlate, è consigliabile includere tutta la logica di aggiornamento in un transazione.  Una transazione è un processo che garantisce che tutte le modifiche correlate apportate a un database vengano completate prima di eseguire il commit delle modifiche.  Per altre informazioni, vedere [Transazioni e concorrenza](../Topic/Transactions%20and%20Concurrency.md).  
  
#### Per aggiungere la logica di aggiornamento all'applicazione  
  
1.  Fare doppio clic sul pulsante **Salva** in <xref:System.Windows.Forms.BindingNavigator> per aprire l'editor del codice per il gestore eventi `bindingNavigatorSaveItem_Click`.  
  
2.  Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati.  Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> \(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState>\).  Gli aggiornamenti vengono quindi eseguiti nell'ordine corretto.  Il codice dovrebbe essere simile al seguente:  
  
     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-cs[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]  
  
## Verifica dell'applicazione  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere F5.  
  
2.  Apportare alcune modifiche ai dati di uno o più record di ogni tabella.  
  
3.  Fare clic sul pulsante **Salva**.  
  
4.  Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form associato a dati nell'applicazione Windows.  È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form.  Per altre informazioni, vedere [Procedura: aggiungere una query con parametri a un'applicazione Windows Form](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Modifica dell'origine dati per aggiungere o rimuovere oggetti di database.  Per altre informazioni, vedere [Procedura: modificare un dataset](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)