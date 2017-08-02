---
title: "Procedura: Aggiornare un&#39;origine dati con i dati inviati da un controllo host"
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
  - "documenti [sviluppo per Office in Visual Studio], aggiornamenti dell'origine dati"
  - "dati [sviluppo per Office in Visual Studio], aggiornamento di un'origine dati da un documento"
  - "controlli host [sviluppo per Office in Visual Studio], aggiornamenti dell'origine dati"
  - "documenti di Office [sviluppo per Office in Visual Studio], origini dati"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Procedura: Aggiornare un&#39;origine dati con i dati inviati da un controllo host
  È possibile associare un controllo host a un'origine dati e aggiornare l'origine dati con le modifiche apportate ai dati nel controllo. Questo processo prevede due passaggi principali:  
  
1.  Aggiornare l'origine dati in memoria con i dati modificati nel controllo. In genere, l'origine dati in memoria è un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o un altro oggetto dati.  
  
2.  Aggiornare il database con i dati modificati nell'origine dati in memoria. Ciò è possibile solo se l'origine dati è connessa a un database back\-end, ad esempio un database SQL Server o Microsoft Office Access.  
  
 Per altre informazioni sui controlli host e il data binding, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md) e [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Aggiornamento dell'origine dati in memoria  
 Per impostazione predefinita, i controlli host che consentono il data binding semplice \(ad esempio i controlli contenuto in un documento di Word o un controllo di intervallo denominato in un foglio di lavoro di Excel\) non salvano le modifiche all'origine dati in memoria. In altre parole, quando un utente finale modifica un valore in un controllo host e successivamente si sposta dal controllo, il nuovo valore del controllo non viene salvato nell'origine dati.  
  
 Per salvare i dati nell'origine dati, è possibile scrivere codice che consenta di aggiornare l'origine dati in risposta a un evento specifico in fase di esecuzione oppure configurare il controllo in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore nel controllo.  
  
 Non è necessario salvare le modifiche apportate a <xref:Microsoft.Office.Tools.Excel.ListObject> nell'origine dati in memoria. Quando si associa un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> ai dati, il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> salva automaticamente le modifiche nell'origine dati in memoria senza che sia richiesto codice aggiuntivo.  
  
#### Per aggiornare l'origine dati in memoria in fase di esecuzione  
  
-   Chiamare il metodo <xref:System.Windows.Forms.Binding.WriteValue%2A> dell'oggetto <xref:System.Windows.Forms.Binding> che associa il controllo all'origine dati.  
  
     Nell'esempio seguente le modifiche apportate a un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in un foglio di lavoro di Excel vengono salvate nell'origine dati. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### Aggiornamento automatico dell'origine dati in memoria  
 È anche possibile configurare un controllo in modo da aggiornare automaticamente l'origine dati in memoria. In un progetto a livello di documento, questa operazione può essere eseguita tramite codice o tramite la finestra di progettazione. In un progetto di componente aggiuntivo VSTO è necessario usare il codice.  
  
##### Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite codice  
  
1.  Usare la modalità System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  dell'oggetto <xref:System.Windows.Forms.Binding> che associa il controllo all'origine dati. Per aggiornare l'origine dati è possibile procedere in due modi:  
  
    -   Per aggiornare l'origine dati quando il controllo viene convalidato, impostare questa proprietà su System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Per aggiornare l'origine dati quando si modifica il valore della proprietà del controllo associata ai dati, impostare questa proprietà su System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  L'opzione System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged non si applica ai controlli host di Word perché Word non fornisce notifiche relative alle modifiche al documento o al controllo, ma può essere usata per i controlli Windows Form nei documenti di Word.  
  
     L'esempio seguente configura un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in modo che l'origine dati venga aggiornata automaticamente quando si modifica il valore del controllo. Questo esempio presuppone che sia presente un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `namedRange1` la cui proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> è associata a un campo in un'origine dati.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### Per impostare un controllo in modo che l'origine dati in memoria venga aggiornata automaticamente tramite la finestra di progettazione  
  
1.  In Visual Studio, aprire il documento di Word o la cartella di lavoro di Excel nella finestra di progettazione.  
  
2.  Fare clic sul controllo desiderato per aggiornare automaticamente l'origine dati.  
  
3.  Nella finestra **Proprietà** espandere la proprietà **\(DataBindings\)**.  
  
4.  Accanto alla proprietà **\(Avanzate\)** fare clic sul pulsante con i puntini di sospensione \(![Schermata VisualStudioEllipsesButton](~/docs/vsto/media/vbellipsesbutton.png "Schermata VisualStudioEllipsesButton")\).  
  
5.  Nella finestra di dialogo **Formattazione e associazione avanzata** fare clic nell'elenco a discesa **Modalità aggiornamento origine dati** e selezionare uno dei valori seguenti:  
  
    -   Per aggiornare l'origine dati quando il controllo viene convalidato, selezionare **OnValidation**.  
  
    -   Per aggiornare l'origine dati quando si modifica il valore della proprietà del controllo associata ai dati, selezionare **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  L'opzione **OnPropertyChanged** non si applica ai controlli host di Word perché Word non fornisce notifiche relative alle modifiche al documento o al controllo, ma può essere usata per i controlli Windows Form nei documenti di Word.  
  
6.  Chiudere la finestra di dialogo **Formattazione e associazione avanzata**.  
  
## Aggiornamento del database  
 Se l'origine dati in memoria è associata a un database, è necessario aggiornare il database in base alle modifiche apportate all'origine dati. Per altre informazioni sull'aggiornamento di un database, vedere [Salvataggio dei dati nei dataset](../Topic/Saving%20data%20back%20to%20the%20database.md) e [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
#### Per aggiornare il database  
  
1.  Chiamare il metodo <xref:System.Windows.Forms.BindingSource.EndEdit%2A> per il controllo <xref:System.Windows.Forms.BindingSource>.  
  
     L'oggetto <xref:System.Windows.Forms.BindingSource> viene generato automaticamente quando un controllo associato a dati viene aggiunto a un documento o a una cartella di lavoro in fase di progettazione. L'oggetto <xref:System.Windows.Forms.BindingSource> connette il controllo al set di dati tipizzato nel progetto. Per altre informazioni, vedere [Cenni preliminari sul componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
     L'esempio di codice seguente presuppone che il progetto contenga un oggetto <xref:System.Windows.Forms.BindingSource> denominato `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  Chiamare il metodo `Update` dell'oggetto TableAdapter generato nel progetto.  
  
     L'oggetto TableAdapter viene generato automaticamente quando un controllo associato a dati viene aggiunto a un documento o a una cartella di lavoro in fase di progettazione. L'oggetto TableAdapter connette il set di dati tipizzato nel progetto al database. Per altre informazioni, vedere [Cenni preliminari sugli oggetti TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     L'esempio di codice seguente presuppone che sia disponibile una connessione alla tabella Customers nel database Northwind e che il progetto contenga un oggetto TableAdapter denominato `customersTableAdapter` e un set di dati tipizzato denominato `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Salvataggio dei dati nei dataset](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [Procedura: aggiornare i dati mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Procedura: scorrere i record di un database in un foglio di lavoro](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Procedura: popolare fogli di lavoro con dati da un database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Compilare documenti con dati forniti da servizi](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  