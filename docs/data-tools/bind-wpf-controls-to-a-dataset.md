---
title: "Procedura dettagliata: associazione di controlli WPF a un dataset | Microsoft Docs"
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
  - "associazione dati WPF [Visual Studio], procedure dettagliate"
  - "WPF (finestra di progettazione), associazione dati"
  - "WPF, associazione dati in Visual Studio"
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: associazione di controlli WPF a un dataset
In questa procedura dettagliata, verrà creata un'applicazione WPF contenente i controlli associati a dati.  I controlli vengono associati a record di prodotto incapsulati in un set di dati.  Si aggiungeranno inoltre i pulsanti per scorrere i prodotti e salvare le modifiche ai record di prodotto.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'applicazione WPF e di un set di dati generato dai dati nel database di esempio AdventureWorksLT.  
  
-   Creazione di un set di controlli associati a dati mediante il trascinamento di una tabella dati dalla finestra **Origini dati** a una finestra di WPF Designer.  
  
-   Creazione di pulsanti per spostarsi avanti e indietro tra i record di prodotto.  
  
-   Creazione di un pulsante che consente di salvare le modifiche apportate dagli utenti ai record di prodotto nella tabella dati e nell'origine dati sottostante.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
-   Accesso a un'istanza in esecuzione di SQL Server o SQL Server Express con il database di esempio AdventureWorksLT associato.  È possibile scaricare il database AdventureWorksLT dal [sito Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
 Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:  
  
-   Set di dati e oggetti TableAdapter.  Per altre informazioni, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) e [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md).  
  
-   Uso di WPF Designer.  Per altre informazioni, vedere [Cenni preliminari su WPF e Silverlight Designer](http://msdn.microsoft.com/it-it/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Data binding WPF.  Per altre informazioni, vedere [Cenni preliminari sull'associazione dati](../Topic/Data%20Binding%20Overview.md).  
  
## Creazione del progetto  
 Creare un nuovo progetto WPF.  Il progetto visualizzerà i record di prodotto.  
  
#### Per creare il progetto  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Espandere **Visual Basic** o **Visual C\#**, quindi selezionare **Finestre**.  
  
4.  Selezionare il modello di progetto **Applicazione WPF**.  
  
5.  Nella casella **Nome** digitare `AdventureWorksProductsEditor` e fare clic su **OK**.  
  
     Visual Studio crea il progetto `AdventureWorksProductsEditor`.  
  
## Creazione di un set di dati per l'applicazione  
 Prima di poter creare i controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo alla finestra **Origini dati**.  In questa procedura dettagliata viene creato un set di dati da usare come modello di dati.  
  
#### Per creare un set di dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
     Verrà visualizzata la finestra **Origini dati**.  
  
2.  Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
     Verrà avviata la **Configurazione guidata origine dati**.  
  
3.  Nella pagina **Seleziona un tipo di origine dati** selezionare **Database**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina **Scegli modello database** selezionare **DataSet** e scegliere **Avanti**.  
  
5.  Nella pagina **Seleziona connessione dati** selezionare una delle opzioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente, quindi scegliere **Avanti**.  
  
         \-oppure\-  
  
    -   Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.  
  
6.  Nella pagina **Salva la stringa di connessione nel file di configurazione applicazione** selezionare la casella di controllo **Sì, salva la connessione con nome**, quindi fare clic su **Avanti**.  
  
7.  Nella pagina **Seleziona oggetti di database** espandere **Tabelle**, quindi selezionare la tabella **Product \(SalesLT\)**.  
  
8.  Scegliere **Fine**.  
  
     Visual Studio aggiunge un nuovo file AdventureWorksLTDataSet.xsd al progetto e un elemento **AdventureWorksLTDataSet** corrispondente alla finestra **Origini dati**.  Il file AdventureWorksLTDataSet.xsd definisce un set di dati tipizzato denominato `AdventureWorksLTDataSet` e un oggetto TableAdapter denominato `ProductTableAdapter`.  Più avanti in questa procedura dettagliata, l'oggetto `ProductTableAdapter` verrà usato per riempire il set di dati con i dati e salvare nuovamente le modifiche nel database.  
  
9. Compilare il progetto.  
  
## Modifica del metodo Fill predefinito dell'oggetto TableAdapter  
 Per riempire il set di dati con i dati, usare il metodo `Fill` dell'oggetto `ProductTableAdapter`.  Per impostazione predefinita, il metodo `Fill` riempie `ProductDataTable` in `AdventureWorksLTDataSet` con tutte le righe di dati della tabella Product.  È possibile modificare questo metodo in modo da restituire solo un subset di righe.  Per questa procedura dettagliata, modificare il metodo `Fill` in modo da restituire solo di prodotti con foto.  
  
#### Per caricare le righe di prodotti con foto  
  
1.  In **Esplora soluzioni** fare doppio clic sul file AdventureWorksLTDataSet.xsd.  
  
     Viene aperto Progettazione DataSet.  
  
2.  Nella finestra di progettazione fare clic con il pulsante destro del mouse sulla query **Fill,GetData\(\)** e scegliere **Configura**.  
  
     Verrà avviata la **Configurazione guidata TableAdapter**.  
  
3.  Nella pagina **Immettere un'istruzione SQL** aggiungere la clausola WHERE seguente dopo l'istruzione `SELECT` nella casella di testo.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  Scegliere **Fine**.  
  
## Definizione dell'interfaccia utente  
 Aggiungere alcuni pulsanti alla finestra modificando il codice XAML in WPF Designer.  Più avanti in questa procedura dettagliata, verrà aggiunto il codice che consente agli utenti di scorrere e salvare le modifiche ai record di prodotti con questi pulsanti.  
  
#### Per definire l'interfaccia utente della finestra  
  
1.  In **Esplora soluzioni** fare doppio clic su MainWindow.xaml.  
  
     La finestra verrà aperta in WPF Designer.  
  
2.  Nella visualizzazione [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] della finestra di progettazione aggiungere il codice seguente tra i tag `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compilare il progetto.  
  
## Creazione di controlli associati a dati  
 Creare i controlli che consentono di visualizzare i record cliente trascinando la tabella `Product` dalla finestra **Origini dati** a WPF Designer.  
  
#### Per creare i controlli associati a dati  
  
1.  Nella finestra **Origini dati** fare clic sul menu a discesa del nodo **Product** e selezionare **Dettagli**.  
  
2.  Espandere il nodo **Product**.  
  
3.  Poiché per questo esempio alcuni campi non verranno visualizzati, fare clic sul menu a discesa accanto ai nodi seguenti e selezionare **Nessuno**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  Fare clic sul menu a discesa accanto al nodo **ThumbNailPhoto** e selezionare **Image**.  
  
    > [!NOTE]
    >  Per impostazione predefinita, il controllo predefinito degli elementi nella finestra **Origini dati** che rappresentano immagini è impostato su **Nessuno**,  dal momento che le immagini vengono archiviate come matrici di byte nei database e le matrici di byte possono contenere qualsiasi elemento, da una matrice semplice di byte al file eseguibile di un'applicazione di grandi dimensioni.  
  
5.  Dalla finestra **Origini dati** trascinare il nodo **Product** nella riga della griglia sotto la riga contenente i pulsanti.  
  
     Visual Studio genera il codice XAML che definisce un set di controlli associati a dati nella tabella **Products**.  Genera inoltre il codice che carica i dati.  Per altre informazioni sull'XAML e il codice generati, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Nella finestra di progettazione fare clic sulla casella di testo accanto all'etichetta **Product ID**.  
  
7.  Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.  
  
## Esplorazione dei record di prodotto  
 Aggiungere il codice che consente agli utenti di scorrere i record di prodotto usando i pulsanti **\<** e **\>**.  
  
#### Per consentire agli utenti di esplorare i record di prodotto  
  
1.  Nella finestra di progettazione fare doppio clic sul pulsante **\<** nell'area della finestra.  
  
     Visual Studio apre il file code\-behind e crea un nuovo gestore eventi `backButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Modificare il gestore eventi `Window_Loaded` in modo che `ProductViewSource`, `AdventureWorksLTDataSet` e `AdventureWorksLTDataSetProductTableAdapter` siano esterni al metodo e accessibili all'intero form.  Dichiararli come globali per il form e assegnarli all'interno del gestore eventi `Window_Loaded` analogo al seguente:  
  
     [!CODE [Data_WPFDATASET#1](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#1)]  
  
3.  Aggiungere il codice seguente al gestore eventi `backButton_Click`:  
  
     [!CODE [Data_WPFDATASET#2](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#2)]  
  
4.  Tornare alla finestra di progettazione e fare doppio clic sul pulsante **\>**.  
  
5.  Aggiungere il codice seguente al gestore eventi `nextButton_Click`:  
  
     [!CODE [Data_WPFDATASET#3](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#3)]  
  
## Salvataggio delle modifiche ai record di prodotto  
 Aggiungere il codice che consente agli utenti di salvare le modifiche ai record di prodotto usando il pulsante **Salva modifiche**.  
  
#### Per aggiungere la possibilità di salvare le modifiche ai record di prodotto  
  
1.  Nella finestra di progettazione fare doppio clic sul pulsante **Salva modifiche**.  
  
     Visual Studio apre il file code\-behind e crea un nuovo gestore eventi `saveButton_Click` per l'evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Aggiungere il codice seguente al gestore eventi `saveButton_Click`:  
  
     [!CODE [Data_WPFDATASET#4](../CodeSnippet/VS_Snippets_ProTools/data_wpfdataset#4)]  
  
    > [!NOTE]
    >  Questo esempio usa il metodo `Save` di `TableAdapter` per salvare le modifiche.  Tale approccio è appropriato a questa procedura dettagliata, in quanto viene modificata una sola tabella dati.  Se è necessario salvare modifiche a più tabelle dati, è possibile usare in alternativa il metodo `UpdateAll` di `TableAdapterManager` generato da Visual Studio con il set di dati.  Per altre informazioni, vedere [Panoramica di TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
## Verifica dell'applicazione  
 Compilare ed eseguire l'applicazione.  Verificare che sia possibile visualizzare e aggiornare i record di prodotto.  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere **F5**.  
  
     L'applicazione verrà compilata ed eseguita.  Verificare quanto segue:  
  
    -   Nelle caselle di testo vengono visualizzati i dati del primo record di prodotto contenente una foto.  L'ID prodotto è 713, mentre il nome è **Long\-Sleeve Logo Jersey, S**.  
  
    -   È possibile fare clic sui pulsanti **\>** o **\<** per spostarsi tra gli altri record di prodotto.  
  
2.  In uno dei record di prodotto modificare il valore **Dimensione**, quindi fare clic su **Salva modifiche**.  
  
3.  Chiudere l'applicazione, quindi riavviarla premendo **F5** in Visual Studio.  
  
4.  Passare al record di prodotto modificato e verificare che la modifica sia presente.  
  
5.  Chiudere l'applicazione.  
  
## Passaggi successivi  
 Dopo avere completato questa procedura dettagliata, è possibile eseguire le attività correlate seguenti:  
  
-   Imparare a usare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati.  Per altre informazioni, vedere [Procedura dettagliata: associazione di controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
-   Imparare a usare la finestra **Origini dati** in Visual Studio per visualizzare i dati correlati, ovvero i dati in una relazione padre\-figlio, nei controlli WPF.  Per altre informazioni, vedere [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## Vedere anche  
 [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Procedura: associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Cenni preliminari su WPF e Silverlight Designer](http://msdn.microsoft.com/it-it/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Cenni preliminari sull'associazione dati](../Topic/Data%20Binding%20Overview.md)