---
title: "Procedura dettagliata: Data binding complesso in un progetto di componente aggiuntivo VSTO"
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
  - "data binding [sviluppo per Office in Visual Studio], Excel"
  - "dati [sviluppo per Office in Visual Studio], data binding"
  - "dati complessi [sviluppo per Office in Visual Studio]"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura dettagliata: Data binding complesso in un progetto di componente aggiuntivo VSTO
  È possibile associare dati a controlli host e Windows Form in progetti di componente aggiuntivo VSTO. Questa procedura dettagliata illustra come aggiungere controlli a un foglio di lavoro di Microsoft Office Excel e associare i controlli ai dati in fase di esecuzione.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro in fase di esecuzione.  
  
-   Creazione di un <xref:System.Windows.Forms.BindingSource> che connette il controllo a un'istanza di un set di dati.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Accesso a un'istanza in esecuzione di SQL Server 2005 o SQL Server 2005 Express con il database di esempio `AdventureWorksLT` collegato. È possibile scaricare il database `AdventureWorksLT` dal [sito Web di CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Per altre informazioni sul collegamento di un database, vedere gli argomenti seguenti:  
  
    -   Per collegare un database con SQL Server Management Studio o SQL Server Management Studio Express, vedere [Procedura: Collegamento di un database \(SQL Server Management Studio\)](http://msdn.microsoft.com/it-it/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Per collegare un database usando la riga di comando, vedere [Procedura: Collegamento di un file di database a SQL Server Express](http://msdn.microsoft.com/it-it/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Creazione di un nuovo progetto  
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto di componente aggiuntivo VSTO di Excel denominato **Popolamento di fogli di lavoro da un database**, usando Visual Basic o C\#.  
  
     Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il file `ThisAddIn.vb` o `ThisAddIn.cs` e aggiunge il progetto **Popolamento di fogli di lavoro da un database** a **Esplora soluzioni**.  
  
## Creazione di un'origine dati  
 Usare la finestra **Origini dati** per aggiungere un DataSet tipizzato al progetto.  
  
#### Per aggiungere un set di dati tipizzato al progetto  
  
1.  Se la finestra **Origini dati** non è visibile, visualizzarla scegliendo **Visualizza**, **Altre finestre** e **Origini dati** dalla barra dei menu.  
  
2.  Scegliere **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** e quindi scegliere **Avanti**.  
  
4.  Se esiste già una connessione al database `AdventureWorksLT`, selezionarla e quindi scegliere **Avanti**.  
  
     In caso contrario, scegliere **Nuova connessione** e usare la finestra di dialogo **Aggiungi connessione** per creare la nuova connessione. Per altre informazioni, vedere [Procedura: connettersi ai dati di un database](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.  
  
6.  Nella pagina **Seleziona oggetti di database** espandere **Tabelle** e quindi selezionare la tabella **Address \(SalesLT\)**.  
  
7.  Scegliere **Fine**.  
  
     Il file AdventureWorksLTDataSet.xsd viene aggiunto a **Esplora soluzioni**. Questo file definisce gli elementi seguenti:  
  
    -   Un set di dati tipizzato denominato `AdventureWorksLTDataSet`. Questo set di dati rappresenta i contenuti della tabella **Address \(SalesLT\)** nel database AdventureWorksLT.  
  
    -   Un oggetto TableAdapter denominato `AddressTableAdapter`.TableAdapter può essere usato per leggere e scrivere dati in `AdventureWorksLTDataSet`. Per altre informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Si useranno entrambi gli oggetti più avanti in questa procedura dettagliata.  
  
## Creazione di controlli e associazione dei controlli ai dati  
 Per questa procedura dettagliata il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> visualizza tutti i dati nella tabella selezionata non appena l'utente apre la cartella di lavoro. L'oggetto elenco usa un <xref:System.Windows.Forms.BindingSource> per connettere il controllo al database.  
  
 Per altre informazioni sull'associazione dei controlli ai dati, vedere [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Per aggiungere l'oggetto elenco, il set di dati e l'adattatore tabella  
  
1.  Nella classe `ThisAddIn` dichiarare i controlli seguenti per visualizzare la tabella `Address` del set di dati `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  Nel metodo `ThisAddIn_Startup` aggiungere il codice seguente per inizializzare il set di dati e compilare il set di dati con le informazioni del set di dati `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Aggiungere al metodo `ThisAddIn_Startup` il seguente codice. Viene generato un elemento host che estende il foglio di lavoro. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Creare un intervallo e aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Per associare l'oggetto elenco a `AdventureWorksLTDataSet`, usare <xref:System.Windows.Forms.BindingSource>. Passare i nomi delle colonne da associare all'oggetto elenco.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## Test del componente aggiuntivo  
 Quando si apre Excel, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> visualizza i dati della tabella `Address` del set di dati `AdventureWorksLTDataSet`.  
  
#### Per testare il componente aggiuntivo VSTO  
  
-   Premere **F5**.  
  
     Nel foglio di lavoro viene creato un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> denominato `addressListObject`. Allo stesso tempo vengono aggiunti al progetto un oggetto del set di dati denominato `adventureWorksLTDataSet` e un oggetto <xref:System.Windows.Forms.BindingSource> denominato `addressBindingSource`.<xref:Microsoft.Office.Tools.Excel.ListObject> è associato a <xref:System.Windows.Forms.BindingSource>, che a sua volta è associato all'oggetto del set di dati.  
  
## Vedere anche  
 [Dati nelle soluzioni Office](../vsto/data-in-office-solutions.md)   
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: popolare fogli di lavoro con dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Compilare documenti con dati forniti da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: scorrere i record di un database in un foglio di lavoro](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Procedura dettagliata: associazione dati semplice in un progetto a livello di documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Procedura dettagliata: associazione dati complessa in un progetto a livello di documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Cenni preliminari sull'utilizzo di file di un database locale nelle soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Cenni preliminari sull'utilizzo di file di un database locale nelle soluzioni Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Connessione ai dati nelle applicazioni Windows Form](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Cenni preliminari sul componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  