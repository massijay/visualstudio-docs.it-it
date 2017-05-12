---
title: "Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Word"
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
  - "riquadri azioni [sviluppo per Office in Visual Studio], associazione di controlli"
  - "riquadri azioni [sviluppo per Office in Visual Studio], associazione dati"
  - "controlli [sviluppo per Office in Visual Studio], associazione dati"
  - "associazione dati [sviluppo per Office in Visual Studio], riquadri azioni"
  - "associazione dati [sviluppo per Office in Visual Studio], Smart document"
  - "Smart document [sviluppo per Office in Visual Studio], associazione dati"
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Word
  In questa procedura dettagliata verrà illustrata l'associazione dati ai controlli in un riquadro azioni di Word.  I controlli mostrano una relazione Master\-Details tra le tabelle di un database SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un riquadro azioni con i controlli Windows Form associati a dati.  
  
-   Utilizzo di una relazione Master\-Details per la visualizzazione dei dati nei controlli.  
  
-   Visualizzazione del riquadro delle azioni all'apertura dell'applicazione.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Accesso a un server in cui sia presente il database di esempio di SQL Server Northwind.  
  
-   Autorizzazioni per leggere il database SQL Server o scrivere in esso.  
  
## Creazione del progetto  
 Il primo passaggio consiste nella creazione di un progetto Documento di Word.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Documento di Word denominato My Word Actions Pane.  Nella procedura guidata, scegliere **Crea un nuovo documento**.  
  
     Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Il nuovo documento di Word verrà aperto nella finestra di progettazione e il progetto **My Word Actions Pane** verrà aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di controlli al riquadro delle azioni  
 Per questa procedura dettagliata è necessario un controllo riquadro azioni contenente controlli Windows Form con associazione dati.  Aggiungere un'origine dati al progetto, quindi trascinare i controlli dalla finestra **Origini dati** sul controllo riquadro azioni.  
  
#### Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il progetto **My Word Actions Pane** in **Esplora soluzioni**.  
  
2.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
3.  Fare clic su **Controllo riquadro azioni** nella finestra di dialogo **Controllo riquadro azioni**, assegnare al controllo il nome **ActionsControl** e fare clic su **Aggiungi**.  
  
#### Per aggiungere un'origine dati al progetto  
  
1.  Se la finestra **Origini dati** non è visibile, vengono visualizzati da, sulla barra dei menu, scegliente **Visualizza**, **Altre finestre**, **Origini dati**.  
  
    > [!NOTE]  
    >  Se l'opzione **Mostra origini dati** non è visibile, fare clic nel documento di Word ed effettuare di nuovo la selezione.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e scegliere **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind oppure aggiungere una nuova connessione tramite il pulsante **Nuova connessione**.  
  
5.  Scegliere **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione, se selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella finestra **Oggetti di database**.  
  
8.  Selezionare la casella di controllo accanto alle tabelle **Suppliers** e **Products**.  
  
9. Fare clic su **Fine**.  
  
 Con la procedura guidata verranno aggiunte le tabelle **Suppliers** e **Products** alla finestra **Origini dati**.  Inoltre, aggiungerà un DataSet tipizzato al progetto visualizzato in **Esplora soluzioni**.  
  
#### Per aggiungere controlli Windows Form con associazione dati a un controllo riquadro azioni  
  
1.  Espandere la tabella **Suppliers** nella finestra **Origini dati**.  
  
2.  Fare clic sulla freccia a discesa sul nodo **Company Name** e selezionare **ComboBox**.  
  
3.  Trascinare **CompanyName** dalla finestra **Origini dati** sul controllo riquadro azioni.  
  
     Verrà creato un controllo <xref:System.Windows.Forms.ComboBox> sul controllo riquadro azioni.  Contemporaneamente, una classe <xref:System.Windows.Forms.BindingSource> denominata `SuppliersBindingSource`, un adattatore di tabelle e una classe <xref:System.Data.DataSet> verranno aggiunti al progetto sulla barra dei componenti.  
  
4.  Selezionare `SuppliersBindingNavigator` sulla **barra dei componenti** e premere CANC.  In questa procedura dettagliata il controllo `SuppliersBindingNavigator` non verrà utilizzato.  
  
    > [!NOTE]  
    >  L'eliminazione del controllo `SuppliersBindingNavigator` non implica la rimozione di tutto il codice appositamente generato.  Questo codice può essere rimosso.  
  
5.  Spostare la casella combinata in modo da posizionarla sotto l'etichetta e modificare la proprietà **Size** in 171, 21.  
  
6.  Nella finestra **Origini dati** espandere la tabella **Products** figlia della tabella **Suppliers**.  
  
7.  Fare clic sulla freccia a discesa sul nodo **ProductName** e selezionare **ListBox**.  
  
8.  Trascinare **ProductName** sul controllo riquadro azioni.  
  
     Verrà creato un controllo <xref:System.Windows.Forms.ListBox> sul controllo riquadro azioni.  Contemporaneamente, una classe <xref:System.Windows.Forms.BindingSource> denominata `ProductBindingSource` e un adattatore di tabelle verranno aggiunti al progetto sulla barra dei componenti.  
  
9. Spostare la casella di riepilogo in modo da posizionarla sotto l'etichetta e modificare la proprietà **Size** in 171, 95.  
  
10. Trascinare una classe <xref:System.Windows.Forms.Button> dalla **Casella degli strumenti** sul controllo riquadro azioni e posizionarla sotto la casella di riepilogo.  
  
11. Fare clic con il pulsante destro del mouse su <xref:System.Windows.Forms.Button>, scegliere **Proprietà** dal menu di scelta rapida e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**Insert**|  
    |**Testo**|**Insert**|  
  
12. Ridimensionare il controllo utente per adattarlo ai controlli.  
  
## Impostazione dell'origine dati  
 Per impostare l'origine dati, aggiungere il codice all'evento <xref:System.Windows.Forms.UserControl.Load> del controllo riquadro azioni per riempire il controllo con i dati di <xref:System.Data.DataTable> e impostare le proprietà <xref:System.Windows.Forms.Binding.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> per ciascun controllo.  
  
#### Per caricare il controllo con i dati  
  
1.  Aggiungere il codice riportato di seguito nel gestore eventi <xref:System.Windows.Forms.UserControl.Load> della classe `ActionsControl`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  In C\# è necessario collegare il gestore eventi all'evento <xref:System.Windows.Forms.UserControl.Load>.  È possibile inserire il codice nel costruttore `ActionsControl`, dopo la chiamata a `InitializeComponent`.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### Per impostare le proprietà di associazione dati dei controlli  
  
1.  Fare clic sul controllo `CompanyNameComboBox`.  
  
2.  Fare clic sul pulsante a destra della proprietà **DataSource** nella finestra **Proprietà** e scegliere **suppliersBindingSource**.  
  
3.  Fare clic sul pulsante a destra della proprietà **DisplayMember** e scegliere **CompanyName**.  
  
4.  Espandere la proprietà **DataBindings**, fare clic sul pulsante a destra della proprietà **Text** e selezionare **None**.  
  
5.  Fare clic sul controllo `ProductNameListBox`.  
  
6.  Fare clic sul pulsante a destra della proprietà **DataSource** nella finestra **Proprietà** e scegliere **productsBindingSource**.  
  
7.  Fare clic sul pulsante a destra della proprietà **DisplayMember** e scegliere **ProductName**.  
  
8.  Espandere la proprietà **DataBindings**, fare clic sul pulsante a destra della proprietà **SelectedValue** e selezionare **None**.  
  
## Aggiunta di un metodo per inserire dati in una tabella  
 In questa attività verranno letti i dati dei controlli associati e verrà compilata una tabella nel documento di Word.  Verrà creata innanzitutto una procedura per formattare le intestazioni della tabella, quindi verrà aggiunto il metodo `AddData` per creare e formattare una tabella di Word.  
  
#### Per formattare le intestazioni di tabella  
  
1.  Nella classe `ActionsControl` creare un metodo per formattare le intestazioni della tabella.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### Per creare la tabella  
  
1.  Nella classe `ActionsControl` scrivere un metodo per creare una tabella, se non ne esiste già una, e aggiungere i dati del riquadro delle azioni alla tabella.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### Per inserire testo in una tabella di Word  
  
1.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante **Insert**.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  Per C\#, è necessario creare un gestore eventi per l'evento <xref:System.Windows.Forms.Control.Click> del pulsante.  È possibile inserire il codice nel gestore eventi <xref:System.Windows.Forms.UserControl.Load> della classe `ActionsControl`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## Visualizzazione del riquadro delle azioni  
 Il riquadro diventa visibile una volta che vi sono stati aggiunti i controlli.  
  
#### Per mostrare il riquadro delle azioni  
  
1.  Fare clic con il pulsante destro del mouse su **ThisDocument.vb** o **ThisDocument.cs** in **Esplora soluzioni** e scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Creare una nuova istanza del controllo all'inizio della classe `ThisDocument` in modo che risulti simile all'esempio seguente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  Aggiungere il codice al gestore eventi <xref:Microsoft.Office.Tools.Word.Document.Startup> di `ThisDocument` in modo che risulti simile all'esempio seguente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## Verifica dell'applicazione  
 A questo punto, è possibile eseguire il test del documento per verificare che il riquadro delle azioni venga visualizzato quando viene aperto il documento.  Verificare la relazione master\-dettagli nei controlli del riquadro delle azioni e accertarsi che i dati vengano inseriti in una tabella di Word quando si fa clic sul pulsante **Insert**.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro delle azioni sia visibile.  
  
3.  Selezionare una società nella casella combinata e verificare che le voci nella casella di riepilogo **Products** cambino.  
  
4.  Selezionare un prodotto, fare clic su **Insert** nel riquadro delle azioni e verificare che i dettagli del prodotto vengano aggiunti alla tabella in Word.  
  
5.  Inserire ulteriori prodotti di altre società.  
  
## Passaggi successivi  
 In questa procedura dettagliata sono state fornite le nozioni di base per l'associazione di dati ai controlli di un riquadro delle azioni in Word.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Associazione di dati ai controlli in Excel.  Per ulteriori informazioni, vedere [Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Distribuzione del progetto.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Vedere anche  
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  