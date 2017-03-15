---
title: "Procedura dettagliata: salvataggio di dati con i metodi DBDirect di TableAdapter | Microsoft Docs"
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
  - "dati [Visual Studio], TableAdapter"
  - "salvataggio di dati, procedure dettagliate"
  - "TableAdapters, procedure dettagliate"
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: salvataggio di dati con i metodi DBDirect di TableAdapter
Questa procedura dettagliata fornisce istruzioni dettagliate per eseguire le istruzioni SQL direttamente su un database usando i metodi DBDirect di un oggetto TableAdapter.  I metodi DBDirect di un oggetto TableAdapter forniscono un elevato livello di controllo degli aggiornamenti del database.  Mediante questi metodi è possibile eseguire istruzioni SQL specifiche e stored procedure chiamando i singoli metodi `Insert`, `Update` e `Delete`, come richiesto dall'applicazione \(a differenza del metodo in overload `Update` che consente di eseguire le istruzioni UPDATE, INSERT e DELETE in un'unica chiamata\).  
  
 Durante questa procedura dettagliata, si apprenderà come:  
  
-   Creare una nuova **applicazione Windows**.  
  
-   Creare e configurare un set di dati con la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Selezionare il controllo da creare sul form mediante il trascinamento degli elementi dalla finestra **Origini dati**.  Per altre informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creare il controllo associato a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.  
  
-   Aggiungere metodi per accedere direttamente al database ed eseguire operazioni di inserimento, aggiornamento ed eliminazione direttamente sul database.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  Per altre informazioni, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## Creazione di un'applicazione Windows  
 Il primo passaggio consiste nella creazione di un'**applicazione Windows**.  
  
#### Per creare il nuovo progetto Windows  
  
1.  In Visual Studio creare un nuovo **Progetto** dal menu **File**.  
  
2.  Denominare il progetto TableAdapterDbDirectMethodsWalkthrough.  
  
3.  Selezionare **Applicazione Windows** e fare clic su **OK**.  Per altre informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **TableAdapterDbDirectMethodsWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## Creazione di un'origine dati dal database  
 Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulla tabella `Region` contenuta nel database di esempio Northwind.  Per creare la connessione, è necessario avere accesso al database di esempio Northwind.  Per informazioni sull'impostazione del database di esempio Northwind, vedere [Procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
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
  
8.  Selezionare la tabella `Region`, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella `Region` viene visualizzata nella finestra **Origini dati**.  
  
## Aggiunta di controlli al form per visualizzare i dati  
 Creare i controlli associati a dati mediante il trascinamento degli elementi dalla finestra **Origini dati** nel form.  
  
#### Per creare controlli associati a dati nel Windows Form  
  
-   Trascinare il nodo **Region** principale dalla finestra **Origini dati** al form.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip \(<xref:System.Windows.Forms.BindingNavigator>\) per lo spostamento all'interno dei record.  Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
#### Per aggiungere pulsanti da usare per la chiamata ai singoli metodi DbDirect di TableAdapter  
  
1.  Trascinare tre controlli <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti** a **Form1** \(sotto l'oggetto **RegionDataGridView**\).  
  
2.  Impostare le seguenti proprietà **Name** e **Text** su ciascun pulsante.  
  
    |Name|Text|  
    |----------|----------|  
    |`InsertButton`|Insert|  
    |`UpdateButton`|Update|  
    |`DeleteButton`|Delete|  
  
#### Per aggiungere il codice per l'inserimento dei nuovi record nel database  
  
1.  Fare doppio clic su **InsertButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.  
  
2.  Sostituire il gestore eventi `InsertButton_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-cs[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### Per aggiungere il codice per l'aggiornamento dei record nel database  
  
1.  Fare doppio clic su **UpdateButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.  
  
2.  Sostituire il gestore eventi `UpdateButton_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-cs[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### Per aggiungere i record di eliminazione del codice dal database  
  
1.  Fare doppio clic su **DeleteButton** per creare un gestore eventi per l'evento clic e aprire il form nell'editor di codice.  
  
2.  Sostituire il gestore eventi `DeleteButton_Click` con il codice seguente:  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-cs[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## Esecuzione dell'applicazione  
  
#### Per eseguire l'applicazione  
  
-   Premere F5 per eseguire l'applicazione.  
  
-   Fare clic sul pulsante **Inserisci** e verificare che il nuovo record venga visualizzato nella griglia.  
  
-   Fare clic sul pulsante **Aggiorna** e verificare che il nuovo record venga aggiornato nella griglia.  
  
-   Fare clic sul pulsante **Elimina** e verificare che il nuovo record venga rimosso dalla griglia.  
  
## Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form associato a dati.  È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form.  Per altre informazioni, vedere [Procedura: aggiungere una query con parametri a un'applicazione Windows Form](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Aggiunta di altre tabelle al set di dati selezionando **Configura il Dataset con la procedura guidata** nella finestra **Origini dati**.  È possibile aggiungere controlli che consentono di visualizzare dati correlati mediante il trascinamento dei nodi correlati nel form.  Per altre informazioni, vedere [Procedura: visualizzare dati correlati in un'applicazione Windows Form](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## Vedere anche  
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: accedere direttamente al database mediante un oggetto TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Procedura: salvare dati da un oggetto in un database](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)