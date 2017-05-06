---
title: "Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Excel"
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
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Excel
  In questa procedura dettagliata verrà illustrata l'associazione dati ai controlli in un riquadro azioni in Microsoft Office Excel.  I controlli mostrano una relazione Master\-Details tra le tabelle di un database SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di controlli a un foglio di lavoro.  
  
-   Creazione di un controllo riquadro azioni.  
  
-   Aggiunta dei controlli Windows Form con associazione dati a un controllo riquadro azioni.  
  
-   Visualizzazione del riquadro azioni all'apertura dell'applicazione.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un server in cui sia presente il database di esempio di SQL Server Northwind.  
  
-   Autorizzazioni per leggere il database SQL Server o scrivere in esso.  
  
## Creazione del progetto  
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto cartella di lavoro di Excel denominato My Excel Actions Pane.  Nella procedura guidata, scegliere **Crea un nuovo documento**.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto **My Excel Actions Pane** viene aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di una nuova origine dati al progetto  
  
#### Per aggiungere una nuova origine dati al progetto  
  
1.  Se la finestra **Origini dati** non è visibile, vengono visualizzati da, sulla barra dei menu, scegliente **Visualizza**, **Altre finestre**, **Origini dati**.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e scegliere **Avanti**.  
  
4.  Selezionare una connessione dati al database di SQL Server di esempio Northwind oppure aggiungere una nuova connessione tramite il pulsante **Nuova connessione**.  
  
5.  Scegliere **Avanti**.  
  
6.  Deselezionare l'opzione per salvare la connessione, se selezionata, quindi scegliere **Avanti**.  
  
7.  Espandere il nodo **Tabelle** nella finestra **Oggetti di database**.  
  
8.  Selezionare la casella di controllo accanto alla tabella **Suppliers**.  
  
9. Espandere la tabella **Products** e selezionare **ProductName**, **SupplierID**, **QuantityPerUnit** e **UnitPrice**.  
  
10. Fare clic su **Fine**.  
  
 Con la procedura guidata verranno aggiunte le tabelle **Suppliers** e **Products** alla finestra **Origini dati**.  Inoltre, aggiungerà un DataSet tipizzato al progetto visualizzato in **Esplora soluzioni**.  
  
## Aggiunta di controlli al foglio di lavoro  
 Aggiungere quindi un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> al primo foglio di lavoro.  
  
#### Per aggiungere un controllo NamedRange e un controllo ListObject  
  
1.  Verificare che la cartella di lavoro **My Excel Actions Pane.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzare.  
  
2.  Espandere la tabella **Suppliers** nella finestra **Origini dati**.  
  
3.  Fare clic sulla freccia a discesa sul nodo **Company Name** e selezionare **NamedRange**.  
  
4.  Trascinare **Company Name** dalla finestra **Origini dati** sulla cella **A2** in `Sheet1`.  
  
     Viene creato un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `CompanyNameNamedRange` e il testo \<CompanyName\> viene visualizzato nella cella **A2**.  Contemporaneamente, al progetto sono aggiunti un oggetto <xref:System.Windows.Forms.BindingSource> denominato `suppliersBindingSource`, un adattatore per la tabella e un oggetto <xref:System.Data.DataSet>.  Il controllo è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associata all'istanza di <xref:System.Data.DataSet>.  
  
5.  Nella finestra **Origini dati**, eseguire lo scorrimento verso il basso oltre le colonne della tabella **Suppliers**.  Alla fine dell'elenco è presente la tabella **Products**; la tabella è posizionata in questo punto in quanto elemento figlio della tabella **Suppliers**.  Selezionare questa tabella **Products**, non quella situata allo stesso livello della tabella **Suppliers** e fare clic sulla freccia a discesa visualizzata.  
  
6.  Scegliere **ListObject** nell'elenco a discesa, quindi trascinare la tabella **Products** sulla cella **A6** in `Sheet1`.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `ProductNameListObject` viene creato nella cella **A6**.  Contemporaneamente, al progetto sono aggiunti un oggetto <xref:System.Windows.Forms.BindingSource> denominato `productsBindingSource` e un adattatore per la tabella.  Il controllo è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associata all'istanza di <xref:System.Data.DataSet>.  
  
7.  Solo per C\# selezionare **suppliersBindingSource** nella barra dei componenti e modificare la proprietà **Modifiers** su Internal nella finestra **Proprietà**.  
  
## Aggiunta di controlli al riquadro delle azioni  
 A questo punto, è necessario disporre di un riquadro delle azioni che contenga una casella combinata.  
  
#### Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il progetto **My Excel Actions Pane** in **Esplora soluzioni**.  
  
2.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento**, selezionare **Controllo riquadro azioni**, specificare il nome **ActionsControl** e scegliere **Aggiungi**.  
  
#### Per aggiungere controlli Windows Form con associazione dati a un controllo riquadro azioni  
  
1.  Dalla scheda **Controlli comuni** della **Casella degli strumenti**, trascinare un controllo <xref:System.Windows.Forms.ComboBox> sul controllo del riquadro delle azioni.  
  
2.  Modificare la proprietà **Size** su 171, 21.  
  
3.  Ridimensionare il controllo utente per adattarlo alla casella combinata.  
  
## Associazione del controllo del riquadro delle azioni ai dati  
 In questa sezione, verrà impostata l'origine dati dell'oggetto <xref:System.Windows.Forms.ComboBox> sulla stessa origine dati del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nel foglio di lavoro.  
  
#### Per impostare le proprietà di associazione dati del controllo  
  
1.  Fare clic con il pulsante destro del mouse sul controllo riquadro azioni, quindi fare clic su **Visualizza codice**.  
  
2.  Aggiungere il codice riportato di seguito all'evento <xref:System.Windows.Forms.UserControl.Load> del controllo del riquadro delle azioni.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  Per C\#, è necessario creare un gestore eventi per l'evento `ActionsControl`.  Questo codice può essere inserito nel costruttore di `ActionsControl`.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## Visualizzazione del riquadro delle azioni  
 Il riquadro azioni non è visibile finché il controllo non viene aggiunto in fase di esecuzione.  
  
#### Per mostrare il riquadro delle azioni  
  
1.  Fare clic con il pulsante destro del mouse su ThisWorkbook.vb o ThisWorkbook.cs in **Esplora soluzioni** e selezionare **Visualizza codice**.  
  
2.  Creare una nuova istanza del controllo utente nella classe `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  Nel gestore eventi <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> di `ThisWorkbook` aggiungere il controllo al riquadro azioni.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## Verifica dell'applicazione  
 A questo punto, è possibile eseguire il test del documento per verificare che il riquadro delle azioni si apra quando viene aperto il documento e che i controlli abbiano una relazione Master\-Details.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro delle azioni sia visibile.  
  
3.  Selezionare un'azienda nella casella di riepilogo.  Verificare che il nome dell'azienda sia elencato nel controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e che i dettagli del prodotto siano elencati nel controllo <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
4.  Selezionare varie aziende per verificare che i dettagli relativi al nome e ai prodotti dell'azienda siano modificati in maniera appropriata.  
  
## Passaggi successivi  
 Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Associazione di dati ai controlli in Word.  Per ulteriori informazioni, vedere [Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Distribuzione del progetto.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Vedere anche  
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Procedura: gestire il layout di controllo dei riquadri delle azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  