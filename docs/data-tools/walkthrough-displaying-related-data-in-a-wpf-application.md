---
title: "Procedura dettagliata: visualizzazione dei dati correlati in un&#39;applicazione WPF | Microsoft Docs"
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
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura dettagliata: visualizzazione dei dati correlati in un&#39;applicazione WPF
In questa procedura dettagliata, verrà creata un'applicazione WPF che visualizza dati da tabelle di database che dispongono di una relazione padre\/figlio.  I dati vengono incapsulati nelle entità in un modello Entity Data Model.  L'entità padre contiene informazioni generali per un set di ordini.  Ogni proprietà di questa entità viene associata a un controllo diverso nell'applicazione.  L'entità figlio contiene dettagli per ogni ordine.  Questo set di dati viene associato a un controllo <xref:System.Windows.Controls.DataGrid>.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'applicazione WPF e di un modello Entity Data Model generato dai dati nel database di esempio AdventureWorksLT.  
  
-   Creazione di un set di controlli associati a dati che visualizzano informazioni generali per un set di ordini.  I controlli vengono creati trascinando un'entità padre dalla finestra **Origini dati** a **Progettazione WPF**.  
  
-   Creazione di un controllo <xref:System.Windows.Controls.DataGrid> che visualizza dettagli correlati per ogni ordine selezionato.  I controlli vengono creati trascinando un'entità figlio dalla finestra **Origini dati** a una finestra in **Progettazione WPF**.  
  
     [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Istanza in esecuzione di SQL Server o SQL Server Express a cui è collegato il database di esempio AdventureWorksLT e cui è possibile accedere.  Tale database può essere scaricato dal [sito Web CodePlex](http://go.microsoft.com/fwlink/?linkid=87843) \(informazioni in lingua inglese\).  
  
 Per completare la procedura dettagliata è inoltre consigliabile conoscere già i concetti seguenti:  
  
-   Entity Data Model e ADO.NET Entity Framework.  Per ulteriori informazioni, vedere [Panoramica su Entity Framework](../Topic/Entity%20Framework%20Overview.md).  
  
-   Utilizzo di Progettazione WPF.  Per ulteriori informazioni, vedere [Cenni preliminari su WPF e Silverlight Designer](http://msdn.microsoft.com/it-it/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
-   Associazione dati WPF.  Per ulteriori informazioni, vedere [Cenni preliminari sull'associazione dati](../Topic/Data%20Binding%20Overview.md).  
  
## Creazione del progetto  
 Creare un nuovo progetto WPF per visualizzare i record di ordini.  
  
#### Per creare un nuovo progetto WPF  
  
1.  Avviare Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Espandere **Visual C\#** o **Visual Basic**, quindi selezionare **Finestre**.  
  
4.  Assicurarsi che sia selezionata l'opzione **.NET Framework 4** nella casella combinata nella parte superiore della finestra di dialogo.  Il controllo <xref:System.Windows.Controls.DataGrid> utilizzato in questa procedura dettagliata è disponibile solo in .NET Framework 4.  
  
5.  Selezionare il modello di progetto **Applicazione WPF**.  
  
6.  Nella casella **Nome** digitare `AdventureWorksOrdersViewer`.  
  
7.  Scegliere **OK**.  
  
     Visual Studio crea il progetto `AdventureWorksOrdersViewer`.  
  
## Creazione di un modello Entity Data Model per l'applicazione  
 Prima di poter creare i controlli associati a dati, è necessario definire un modello di dati per l'applicazione e aggiungerlo alla finestra **Origini dati**.  In questa procedura dettagliata, il modello di dati è un modello Entity Data Model.  
  
#### Per creare un Entity Data Model  
  
1.  Dal menu **Dati** scegliere **Aggiungi nuova origine dati** per aprire la **Configurazione guidata origine dati**.  
  
2.  Nella pagina **Seleziona un tipo di origine dati** fare clic su **Database**, quindi su **Avanti**.  
  
3.  Nella pagina **Scegli modello database** fare clic su **Entity Data Model** e scegliere **Avanti**.  
  
4.  Nella pagina **Scegli contenuto Model** fare clic su **Genera da database**, quindi su **Avanti**.  
  
5.  Nella pagina **Seleziona connessione dati** effettuare una delle seguenti operazioni:  
  
    -   Selezionare la connessione dati al database di esempio AdventureWorksLT nell'elenco a discesa, se presente.  
  
         In alternativa  
  
    -   Fare clic su **Nuova connessione** e creare una connessione al database AdventureWorksLT.  
  
     Verificare che l'opzione **Salva impostazioni di connessione dell'entità in App.Config come** sia selezionata, quindi scegliere **Avanti**.  
  
6.  Nella pagina **Seleziona oggetti di database** espandere il nodo **Tabelle**, quindi selezionare le tabelle seguenti:  
  
    -   **SalesOrderDetail**  
  
    -   **SalesOrderHeader**  
  
7.  Fare clic su **Fine**.  
  
8.  Compilare il progetto.  
  
## Creazione di controlli associati a dati per la visualizzazione degli ordini  
 Creare controlli che consentono di visualizzare i record di ordini tramite trascinamento dell'entità `SalesOrderHeaders` dalla finestra **Origini dati** a Progettazione WPF.  
  
#### Per creare controlli associati a dati per la visualizzazione dei record di ordini  
  
1.  In **Esplora soluzioni** fare doppio clic su MainWindow.xaml.  
  
     La finestra verrà aperta in Progettazione WPF.  
  
2.  Modificare il file XAML in modo che le proprietà **Altezza** e **Larghezza** siano impostate su 800  
  
3.  Nella finestra **Origini dati** fare clic sul menu a discesa relativo al nodo **SalesOrderHeaders**, quindi selezionare **Dettagli**.  
  
4.  Espandere il nodo **SalesOrderHeaders**.  
  
5.  Fare clic sul menu a discesa accanto a **SalesOrderID** e selezionare **ComboBox**.  
  
6.  Per ognuno dei seguenti nodi figlio del nodo **SalesOrderHeaders**, fare clic sul menu a discesa accanto al nodo e selezionare **Nessuno**:  
  
    -   **RevisionNumber**  
  
    -   **OnlineOrderFlag**  
  
    -   **ShipToAddressID**  
  
    -   **BillToAddressID**  
  
    -   **CreditCardApprovalCode**  
  
    -   **SubTotal**  
  
    -   **TaxAmt**  
  
    -   **Freight**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Questa azione impedisce a Visual Studio di creare controlli associati a dati per questi nodi nel passaggio successivo.  Per questa procedura dettagliata, si presume che l'utente finale non debba visualizzare questi dati.  
  
7.  Dalla finestra **Origini dati** trascinare il nodo **SalesOrderHeaders** nella finestra in **Progettazione WPF**.  
  
     Visual Studio genera XAML che crea un set di controlli associati a dati nell'entità **SalesOrderHeaders** e il codice che carica i dati.  Per ulteriori informazioni sul linguaggio XAML e sul codice generati, vedere [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
8.  Nella finestra di progettazione fare clic sulla casella combinata accanto all'etichetta **SalesOrderID**.  
  
9. Nella finestra **Proprietà** selezionare la casella di controllo accanto alla proprietà **IsReadOnly**.  
  
## Creazione di un DataGrid che visualizza i dettagli sugli ordini  
 Creare un controllo <xref:System.Windows.Controls.DataGrid> che consente di visualizzare i dettagli degli ordini tramite trascinamento dell'entità `SalesOrderDetails` dalla finestra **Origini dati** a Progettazione WPF.  
  
#### Per creare un DataGrid che visualizza i dettagli sugli ordini  
  
1.  Nella finestra **Origini dati** individuare il nodo **SalesOrderDetails** figlio del nodo **SalesOrderHeaders**.  
  
    > [!NOTE]
    >  Esiste anche un nodo **SalesOrderDetails** peer del nodo **SalesOrderHeaders**.  Assicurarsi di selezionare il nodo figlio del nodo **SalesOrderHeaders**.  
  
2.  Espandere il nodo **SalesOrderDetails** figlio.  
  
3.  Per ognuno dei seguenti nodi figlio del nodo **SalesOrderDetails**, fare clic sul menu a discesa accanto al nodo e selezionare **Nessuno**:  
  
    -   **SalesOrderID**  
  
    -   **SalesOrderDetailID**  
  
    -   **rowguid**  
  
    -   **ModifiedDate**  
  
     Questa azione impedisce a Visual Studio di includere questi dati nel controllo <xref:System.Windows.Controls.DataGrid> creato nel passaggio successivo.  Per questa procedura dettagliata, si presume che l'utente finale non debba visualizzare questi dati.  
  
4.  Dalla finestra **Origini dati** trascinare il nodo **SalesOrderDetails** figlio nella finestra in **Progettazione WPF**.  
  
     Visual Studio genera XAML per definire un nuovo controllo <xref:System.Windows.Controls.DataGrid> associato a dati e il controllo viene visualizzato nella finestra di progettazione.  Visual Studio aggiorna inoltre il metodo `GetSalesOrderHeadersQuery` generato nel file code\-behind per includere i dati nell'entità **SalesOrderDetails**.  
  
## Verifica dell'applicazione  
 Compilare ed eseguire l'applicazione per verificare che i record di ordini vengano visualizzati.  
  
#### Per eseguire il test dell'applicazione  
  
1.  Premere **F5**.  
  
     L'applicazione viene compilata ed eseguita.  Verificare quanto segue:  
  
    -   Nella casella combinata **Sales Order ID** viene visualizzato **71774**.  Si tratta del primo ID ordine nell'entità.  
  
    -   Per ogni ordine selezionato nella casella combinata **SalesOrderID**, vengono visualizzate informazioni dettagliate sull'ordine nel controllo <xref:System.Windows.Controls.DataGrid>.  
  
2.  Chiudere l'applicazione.  
  
## Passaggi successivi  
 Al termine di questa procedura dettagliata, imparare a utilizzare la finestra **Origini dati** in Visual Studio per associare i controlli WPF ad altri tipi di origini dati.  Per ulteriori informazioni, vedere [Procedura dettagliata: associazione di controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) e [Procedura dettagliata: associazione di controlli WPF a un dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## Vedere anche  
 [Associazione di controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Procedura: visualizzare dati correlati nelle applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)