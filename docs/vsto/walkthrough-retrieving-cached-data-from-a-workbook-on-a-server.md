---
title: "Procedura dettagliata: recupero dei dati memorizzati nella cache di una cartella di lavoro contenuta in un server"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "dati [sviluppo per Office in Visual Studio], accesso su server"
  - "dataset [sviluppo per Office in Visual Studio], accesso su server"
  - "documenti [sviluppo per Office in Visual Studio], accesso ai dati sul lato server"
  - "accesso ai dati sul lato server [sviluppo per Office in Visual Studio]"
  - "cartelle di lavoro [sviluppo per Office in Visual Studio], recupero dei dati"
ms.assetid: ef6d61e5-a498-4b38-8e2e-2e80706d854b
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Procedura dettagliata: recupero dei dati memorizzati nella cache di una cartella di lavoro contenuta in un server
  Questa procedura dettagliata illustra come utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per recuperare dati da un dataset memorizzato nella cache di una cartella di lavoro di Microsoft Office Excel senza avviare Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Definizione di un dataset contenente dati ottenuti dal database AdventureWorksLT.  
  
-   Creazione di istanze del dataset in un progetto Cartella di lavoro di Excel e in un progetto di applicazione console.  
  
-   Creazione di un <xref:Microsoft.Office.Tools.Excel.ListObject> associato al dataset contenuto nella cartella di lavoro e popolazione di tale <xref:Microsoft.Office.Tools.Excel.ListObject> con dati all'apertura della cartella di lavoro.  
  
-   Aggiunta del dataset contenuto nella cartella di lavoro nella cache di dati  
  
-   Lettura di dati dal dataset memorizzato nella cache e inserimento degli stessi nel dataset contenuto nell'applicazione console, senza avviare Excel.  
  
 Anche se questa procedura dettagliata presuppone che si esegua il codice nel computer di sviluppo, il codice illustrato da questa procedura dettagliata può essere utilizzato in un server in cui non è stato installato Excel.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un'istanza in esecuzione di Microsoft SQL Server o Microsoft SQL Server Express a cui è collegato il database di esempio AdventureWorksLT.  Tale database può essere scaricato dal [sito Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843) \(informazioni in lingua inglese\).  Per ulteriori informazioni sul collegamento di un database, vedere gli argomenti seguenti:  
  
    -   Per collegare un database tramite SQL Server Management Studio o SQL Server Management Studio Express, vedere [Procedura: Collegamento di un database \(SQL Server Management Studio\)](http://msdn.microsoft.com/it-it/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Per collegare un database tramite la riga di comando, vedere [Procedura: Collegamento di un file di database a SQL Server Express](http://msdn.microsoft.com/it-it/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Creazione di un progetto Libreria di classi che definisce un dataset  
 Per utilizzare lo stesso dataset sia in un progetto Cartella di lavoro di Excel sia in un'applicazione console è necessario definire il dataset in un assembly a parte a cui entrambi questi progetti fanno riferimento.  Per questa procedura dettagliata, definire il dataset in un progetto Libreria di classi.  
  
#### Per creare il progetto Libreria di classi  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel riquadro dei modelli espandere **Visual C\#** o **Visual Basic**, quindi scegliere **Windows**.  
  
4.  Nell'elenco dei modelli di progetto selezionare **Libreria di classi**.  
  
5.  Nella casella **Nome** digitare **AdventureWorksDataSet**.  
  
6.  Fare clic su **Sfoglia**, passare alla cartella %UserProfile%\\Documenti \(per Windows XP e versioni precedenti e per Windows Vista\) e quindi fare clic su **Seleziona cartella**.  
  
7.  Assicurarsi che nella finestra di dialogo **Nuovo progetto** la casella di controllo **Crea directory per soluzione** non sia selezionata.  
  
8.  Scegliere **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **AdventureWorksDataSet** in **Esplora soluzioni** e apre il file di codice **Class1.cs** o **Class1.vb**.  
  
9. In **Esplora soluzioni**, fare clic con il pulsante destro del mouse su **Class1.cs** o **Class1.vb** e quindi fare clic su **Elimina**.  Per la presente procedura dettagliata, infatti, questo file non è necessario.  
  
## Definizione di un dataset nel progetto Libreria di classi  
 Definire un dataset tipizzato contenente dati ottenuti dal database AdventureWorksLT per SQL Server 2005.  Più avanti in questa procedura, verrà fatto riferimento a questo dataset da un progetto cartella di lavoro di Excel e da un progetto di applicazione console.  
  
 Il dataset è un *dataset tipizzato* che rappresenta i dati contenuti nella tabella Product del database AdventureWorksLT.  Per ulteriori informazioni sui dataset tipizzati, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Per definire un dataset tipizzato nel progetto Libreria di classi  
  
1.  Fare clic sul progetto **AdventureWorksDataSet** in **Esplora soluzioni**.  
  
2.  Se la finestra **Origini dati** non è visibile, vengono visualizzati da, sulla barra dei menu, scegliente **Visualizza**, **Altre finestre**, **Origini dati**.  
  
3.  Scegliere **Aggiungi nuova origine dati** per avviare **Configurazione guidata origine dati**.  
  
4.  Fare clic su **Database**, quindi scegliere **Avanti**.  
  
5.  Se già si dispone di una connessione al database AdventureWorksLT, scegliere questa connessione e fare clic su **Avanti**.  
  
     In caso contrario, fare clic su **Nuova connessione** e utilizzare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
6.  Nella pagina **Save the Connection String to the Application Configuration File** fare clic su **Next**.  
  
7.  Nella pagina **Seleziona oggetti di database**, espandere **Tabelle** e selezionare **Product \(SalesLT\)**.  
  
8.  Fare clic su **Fine**.  
  
     Il file AdventureWorksLTDataSet.xsd viene aggiunto al progetto **AdventureWorksDataSet**.  Tale file definisce gli elementi seguenti:  
  
    -   Un dataset tipizzato denominato `AdventureWorksLTDataSet`.  Questo dataset rappresenta il contenuto della tabella Product contenuta nel database AdventureWorksLT.  
  
    -   Un TableAdapter denominato `ProductTableAdapter`.  È possibile utilizzare questo oggetto TableAdapter per leggere e scrivere dati in `AdventureWorksLTDataSet`.  Per ulteriori informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Nei passaggi successivi della procedura dettagliata si utilizzeranno entrambi gli oggetti.  
  
9. In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **AdventureWorksDataSet**, quindi scegliere **Compila**.  
  
     Verificare che il progetto venga compilato senza errori.  
  
## Creazione di un progetto Cartella di lavoro di Excel  
 Creare un progetto Cartella di lavoro di Excel da utilizzare come interfaccia per i dati.  Più avanti in questa procedura si creerà un <xref:Microsoft.Office.Tools.Excel.ListObject> che visualizza i dati e si aggiungerà un'istanza del dataset alla cache di dati della cartella di lavoro.  
  
#### Per creare il progetto Cartella di lavoro di Excel  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione **AdventureWorksDataSet**, scegliere **Aggiungi** e quindi fare clic su **Nuovo progetto**.  
  
2.  Nel riquadro Modelli espandere, **Visual C\#** o **Visual Basic**, quindi espandere **Office\/SharePoint**.  
  
3.  Nel nodo espanso **Office\/SharePoint**, selezionare il nodo **Componenti aggiuntivi di Office**.  
  
4.  Nell'elenco di modelli di progetto, selezionare il progetto **Cartella di lavoro Excel 2013** o **Cartella di lavoro di Excel 2010**.  
  
5.  Nella casella **Nome**, digitare **AdventureWorksReport**.  Non modificare il percorso.  
  
6.  Scegliere **OK**.  
  
     Verrà avviata la **Creazione guidata progetto Visual Studio Tools per Office**.  
  
7.  Verificare che l'opzione **Crea nuovo documento** sia selezionata e fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre la cartella di lavoro **AdventureWorksReport** nella finestra di progettazione e aggiunge il progetto **AdventureWorksReport** in **Esplora soluzioni**.  
  
## Aggiunta del dataset a origini dati contenute nel progetto Cartella di lavoro di Excel  
 Prima che sia possibile visualizzare il dataset contenuto nella cartella di lavoro di Excel, è necessario aggiungere il dataset alle origini dati contenute nel progetto Cartella di lavoro di Excel.  
  
#### Per aggiungere il dataset alle origini dati contenute nel progetto Cartella di lavoro di Excel  
  
1.  In **Esplora soluzioni**, fare doppio clic su **Sheet1.cs** o **Sheet1.vb** sotto il progetto **AdventureWorksReport**.  
  
     La cartella di lavoro verrà aperta nella finestra di progettazione.  
  
2.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Verrà avviata la **Configurazione guidata origine dati**.  
  
3.  Fare clic su **Oggetto** e quindi su **Avanti**.  
  
4.  Nella pagina **Seleziona l'oggetto da associare**, fare clic su **Aggiungi riferimento**.  
  
5.  Nella scheda **Progetti**, fare clic su **AdventureWorksDataSet** e quindi su **OK**.  
  
6.  Sotto lo spazio dei nomi **AdventureWorksDataSet** dell'assembly **AdventureWorksDataSet**, fare clic su **AdventureWorksLTDataSet** e quindi su **Fine**.  
  
     Verrà aperta la finestra **Origini dati**. Inoltre, **AdventureWorksLTDataSet** verrà aggiunto all'elenco di origini dati.  
  
## Creazione di un oggetto ListObject associato a un'istanza del dataset  
 Per visualizzare il dataset contenuto nella cartella di lavoro, creare un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> associato a un'istanza del dataset.  Per ulteriori informazioni sull'associazione dei controlli ai dati, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Per creare un oggetto ListObject associato a un'istanza del dataset  
  
1.  Nella finestra **Origini dati** espandere il nodo **AdventureWorksLTDataSet** sotto **AdventureWorksDataSet**.  
  
2.  Selezionare il nodo **Product**, fare clic sulla freccia a discesa visualizzata e selezionare **ListObject** nell'elenco a discesa.  
  
     Se la freccia a discesa non viene visualizzata, verificare che la cartella di lavoro sia aperta nella finestra di progettazione.  
  
3.  Trascinare la tabella **Product** nella cella A1.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `productListObject` viene creato nel foglio di lavoro a partire dalla cella A1.  Contemporaneamente, al progetto vengono aggiunti un oggetto dataset denominato `adventureWorksLTDataSet` e un <xref:System.Windows.Forms.BindingSource> denominato `productBindingSource`.  <xref:Microsoft.Office.Tools.Excel.ListObject> viene associato all'oggetto <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto dataset.  
  
## Aggiunta del dataset nella cache di dati  
 Per consentire al codice esterno al progetto Cartella di lavoro di Excel di accedere al dataset contenuto nella cartella di lavoro, è necessario aggiungere il dataset nella cache di dati.  Per ulteriori informazioni sulla cache di dati, vedere [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md) e [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
#### Per aggiungere il dataset nella cache di dati  
  
1.  Nella finestra di progettazione, fare clic su **adventureWorksLTDataSet**.  
  
2.  Nella finestra **Proprietà**, impostare la proprietà **Modifiers** su **Public**.  
  
3.  Impostare la proprietà **CacheInDocument** su **True**.  
  
## Inizializzazione del dataset contenuto nella cartella di lavoro  
 Prima che sia possibile recuperare i dati dal dataset memorizzato nella cache tramite l'applicazione console, è necessario popolare con dati il dataset memorizzato nella cache.  
  
#### Per inizializzare il dataset contenuto nella cartella di lavoro  
  
1.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul file **Sheet1.cs** o **Sheet1.vb** e scegliere **Visualizza codice**.  
  
2.  Sostituire il gestore eventi `Sheet1_Startup` con il codice riportato di seguito.  Questo codice utilizza un'istanza della classe `ProductTableAdapter` definita nel progetto **AdventureWorksDataSet** per riempire con dati il dataset memorizzato nella cache, se attualmente è vuoto.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/AdventureWorksReport/Sheet1.cs#8)]
     [!code-vb[Trin_CachedDataWalkthroughs#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/AdventureWorksReport/Sheet1.vb#8)]  
  
## Verifica  
 Compilare ed eseguire il progetto Cartella di lavoro di Excel per assicurarsi che sia la compilazione sia l'esecuzione vengano completate senza errori.  Questa operazione comporta inoltre il riempimento del dataset memorizzato nella cache nonché il salvataggio dei dati nella cartella di lavoro.  
  
#### Per compilare ed eseguire il progetto  
  
1.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto **AdventureWorksReport**, scegliere **Debug** e quindi fare clic su **Avvia nuova istanza**.  
  
     Il progetto verrà compilato e la cartella di lavoro verrà aperta in Excel.  Verificare quanto segue:  
  
    -   <xref:Microsoft.Office.Tools.Excel.ListObject> è stato riempito con i dati.  
  
    -   Verificare che il valore indicato nella colonna **ListPrice** della prima riga di <xref:Microsoft.Office.Tools.Excel.ListObject> sia 1431.5.  Più avanti nella procedura dettagliata verrà utilizzata un'applicazione console per modificare i valori contenuti nella colonna **ListPrice**.  
  
2.  Salvare la cartella di lavoro.  Non modificare il nome o il percorso del file della cartella di lavoro.  
  
3.  Chiudere Excel.  
  
## Creazione di un progetto di applicazione console  
 Creare un progetto di applicazione console da utilizzare per modificare i dati contenuti nel dataset memorizzato nella cache della cartella di lavoro.  
  
#### Per creare un progetto di applicazione console  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione **AdventureWorksDataSet**, scegliere **Aggiungi** e quindi fare clic su **Nuovo progetto**.  
  
2.  Nel riquadro **Tipi progetto** espandere **Visual C\#** o **Visual Basic** e quindi fare clic su **Windows**.  
  
3.  Nel riquadro **Modelli** selezionare **Applicazione console**.  
  
4.  Nella casella **Nome**, digitare **DataReader**.  Non modificare il percorso.  
  
5.  Scegliere **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **DataReader** in **Esplora soluzioni** e apre il file di codice **Program.cs** o **Module1.vb**.  
  
## Recupero dei dati dal dataset memorizzato nella cache tramite l'applicazione console  
 Utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> contenuta nell'applicazione console per leggere i dati in un oggetto `AdventureWorksLTDataSet` locale.  Per verificare che il dataset locale sia stato inizializzato con i dati ottenuti dal dataset memorizzato nella cache, l'applicazione visualizza il numero di righe del dataset locale.  
  
#### Per recuperare i dati dal dataset memorizzato nella cache  
  
1.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto **DataReader**. Quindi, scegliere **Aggiungi riferimento al servizio**.  
  
2.  Nella scheda **.NET**, selezionare Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
3.  Scegliere **OK**.  
  
4.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto **DataReader**. Quindi, scegliere **Aggiungi riferimento al servizio**.  
  
5.  Nella scheda **Progetti**, selezionare **AdventureWorksDataSet** e fare clic su **OK**.  
  
6.  Aprire il file Program.cs o Module1.vb nell'editor di codice.  
  
7.  Aggiungere l'istruzione **using** \(per C\#\) o **Imports** \(per Visual Basic\) seguente all'inizio del file di codice.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  Aggiungere al metodo `Main` il seguente codice.  Questo codice dichiara gli oggetti seguenti:  
  
    -   Un'istanza di tipo `AdventureWorksLTDataSet` definita nel progetto **AdventureWorksDataSet**.  
  
    -   Il percorso della cartella di lavoro AdventureWorksReport contenuta nella cartella di compilazione del progetto **AdventureWorksReport**.  
  
    -   Un oggetto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> da utilizzare per accedere alla cache di dati nella cartella di lavoro.  
  
        > [!NOTE]  
        >  Il codice seguente presuppone che la cartella di lavoro venga salvata con l'estensione XLSX.  Se la cartella di lavoro contenuta nel progetto presenta un'estensione diversa, modificare il percorso di conseguenza.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#10)]
     [!code-vb[Trin_CachedDataWalkthroughs#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#10)]  
  
9. Aggiungere il codice seguente nel metodo `Main` dopo il codice aggiunto nel passaggio precedente.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> viene utilizzata per accedere al dataset memorizzato nella cache della cartella di lavoro.  
  
    -   I dati vengono letti dal dataset memorizzato nella cache e inseriti nel dataset locale.  
  
    -   Il numero di righe del dataset locale viene visualizzato. Ciò consente di verificare che il dataset contenga dati.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#11)]
     [!code-vb[Trin_CachedDataWalkthroughs#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#11)]  
  
10. Scegliere **Compila DataReader** dal menu **Compila**.  
  
## Verifica del progetto  
 Quando viene eseguita, l'applicazione console visualizza il numero di righe del dataset locale.  
  
#### Per eseguire il test della cartella di lavoro  
  
1.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse sul progetto **DataReader**, scegliere **Debug** e quindi fare clic su **Avvia nuova istanza**.  
  
     Verificare mediante l'applicazione che il dataset locale contenga 295 righe.  
  
2.  Premere INVIO per chiudere l'applicazione.  
  
## Passaggi successivi  
 Gli argomenti elencati di seguito offrono ulteriori informazioni sull'utilizzo di dati memorizzati nella cache:  
  
-   Modifica dei dati contenuti in un dataset memorizzato nella cache senza avviare Excel.  Per ulteriori informazioni, vedere [Procedura dettagliata: modifica dei dati memorizzati nella cache di una cartella di lavoro contenuta in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## Vedere anche  
 [Procedura dettagliata: inserimento di dati in una cartella di lavoro contenuta in un server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Procedura dettagliata: modifica dei dati memorizzati nella cache di una cartella di lavoro contenuta in un server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Connessione ai dati nelle applicazioni Windows Form](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  