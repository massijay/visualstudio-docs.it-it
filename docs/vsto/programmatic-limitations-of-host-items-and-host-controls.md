---
title: "Limitazioni a livello di codice degli elementi e dei controlli host | Microsoft Docs"
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
  - "documenti di Office [sviluppo per Office in Visual Studio], controlli host"
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], elementi host"
  - "applicazioni di Office [sviluppo per Office in Visual Studio], elementi host"
  - "elementi host [sviluppo per Office in Visual Studio], limitazioni a livello di codice"
  - "Excel [sviluppo per Office in Visual Studio], elementi host"
  - "controlli host [sviluppo per Office in Visual Studio], creazione"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], controlli host"
  - "applicazioni di Office [sviluppo per Office in Visual Studio], controlli host"
  - "documenti [sviluppo per Office in Visual Studio], controlli host"
  - "controlli [sviluppo per Office in Visual Studio], controlli host"
  - "controlli host [sviluppo per Office in Visual Studio], passaggio a metodi e proprietà"
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], controlli host"
  - "Excel [sviluppo per Office in Visual Studio], controlli host"
  - "controlli host [sviluppo per Office in Visual Studio], limitazioni a livello di codice"
  - "documenti [sviluppo per Office in Visual Studio], elementi host"
  - "documenti di Office [sviluppo per Office in Visual Studio], elementi host"
  - "Word [sviluppo per Office in Visual Studio], elementi host"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], elementi host"
  - "Word [sviluppo per Office in Visual Studio], controlli host"
ms.assetid: 88487946-6f3d-4ea6-8de0-dd219b8002df
caps.latest.revision: 67
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Limitazioni a livello di codice degli elementi e dei controlli host
  Ogni elemento host e controllo host viene progettato per comportarsi come un oggetto nativo corrispondente di Microsoft Office Word o Microsoft Office Excel, con funzionalità aggiuntive. Tuttavia, esistono alcune differenze fondamentali tra il comportamento degli elementi host e dei controlli host e gli oggetti nativi di Office in fase di esecuzione.  
  
 Per informazioni generali sugli elementi host e sui controlli host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Creazione a livello di codice di elementi host  
 Quando si crea o si apre a livello di codice un documento, una cartella di lavoro o un foglio di lavoro in fase di esecuzione mediante il modello a oggetti di Word o Excel, l'elemento non è un elemento host. Al contrario, si tratta di un nuovo oggetto nativo di Office. Ad esempio, se si usa il metodo <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> per creare un nuovo documento di Word in fase di esecuzione, si tratterà di un oggetto <xref:Microsoft.Office.Interop.Word.Document> nativo piuttosto che di un elemento host <xref:Microsoft.Office.Tools.Word.Document>. Analogamente, quando si crea un nuovo foglio di lavoro in fase di esecuzione usando il metodo <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A>, si ottiene un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo piuttosto che un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>.  
  
 Nei progetti a livello di documento non è possibile creare elementi host in fase di esecuzione. Gli elementi host possono essere creati solo in fase di progettazione nei progetti a livello di documento. Per altre informazioni, vedere [Elemento host Document](../vsto/document-host-item.md), [Elemento host Workbook](../vsto/workbook-host-item.md) e [Elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
 Nei progetti di componente aggiuntivo VSTO è possibile creare elementi host <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> o <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione. Per altre informazioni, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## Creazione a livello di codice di controlli host  
 È possibile aggiungere a livello di codice controlli host a un elemento host <xref:Microsoft.Office.Tools.Word.Document> o <xref:Microsoft.Office.Tools.Excel.Worksheet> in fase di esecuzione. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Non è possibile aggiungere controlli host a un oggetto <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo.  
  
> [!NOTE]  
>  I controlli host seguenti non possono essere aggiunti a livello di codice a fogli di lavoro o documenti: <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> e <xref:Microsoft.Office.Tools.Word.XMLNodes>.  
  
## Informazioni sulle differenze di tipo tra elementi host, controlli host e oggetti nativi di Office  
 Per ogni elemento host e controllo host esiste un oggetto nativo di Microsoft Office Word o Microsoft Office Excel sottostante. È possibile accedere all'oggetto sottostante usando la proprietà InnerObject dell'elemento host o del controllo host. Non esiste tuttavia alcun modo per eseguire il cast di un oggetto nativo di Office nel corrispondente elemento host o controllo host. Se si prova a eseguire il cast di un oggetto nativo di Office nel tipo di un elemento host o di un controllo host, verrà generata un'eccezione <xref:System.InvalidCastException>.  
  
 Esistono diversi scenari in cui le differenze tra i tipi di elementi host e controlli host e gli oggetti nativi di Office sottostanti possono influire sul codice.  
  
### Passaggio di controlli host a metodi e proprietà  
 In Word non è possibile passare un controllo host a un metodo o a una proprietà che richiede un oggetto nativo di Word come parametro. È necessario usare la proprietà InnerObject del controllo host per restituire l'oggetto nativo di Word sottostante. Ad esempio, è possibile passare un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> a un metodo passando la proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.InnerObject%2A> del controllo host <xref:Microsoft.Office.Tools.Word.Bookmark> al metodo.  
  
 In Excel, è necessario usare la proprietà InnerObject del controllo host per passare il controllo host a un metodo o una proprietà quando il metodo o la proprietà prevede l'oggetto di Excel sottostante.  
  
 L'esempio seguente crea un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> e lo passa al metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>. Il codice usa la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.InnerObject%2A> dell'intervallo denominato per restituire l'oggetto <xref:Microsoft.Office.Interop.Excel.Range> di Office sottostante richiesto dal metodo <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>.  
  
 [!code-csharp[Trin_VstcoreHostControlsExcel#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#28)]
 [!code-vb[Trin_VstcoreHostControlsExcel#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#28)]  
  
### Tipi restituiti delle proprietà e dei metodi nativi di Office  
 La maggior parte dei metodi e delle proprietà degli elementi host restituisce l'oggetto nativo di Office sottostante sul quale si basa l'elemento host. Ad esempio, la proprietà <xref:Microsoft.Office.Tools.Excel.NamedRange.Parent%2A> di un controllo host <xref:Microsoft.Office.Tools.Excel.NamedRange> in Excel restituisce un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> piuttosto che un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet>. Analogamente, la proprietà <xref:Microsoft.Office.Tools.Word.RichTextContentControl.Parent%2A> di un controllo host <xref:Microsoft.Office.Tools.Word.RichTextContentControl> in Word restituisce un oggetto <xref:Microsoft.Office.Interop.Word.Document> piuttosto che un elemento host <xref:Microsoft.Office.Tools.Word.Document>.  
  
### Accesso alle raccolte di controlli host  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] non fornisce raccolte specifiche per ogni tipo di controllo host. Usare invece la proprietà Controls di un elemento host per scorrere tutti i controlli gestiti \(controlli host e controlli Windows Form\) nel documento o nel foglio di lavoro, quindi cercare gli elementi che corrispondono al tipo di controllo host a cui si è interessati. L'esempio di codice seguente esamina ogni controllo in un documento di Word e determina se il controllo è di tipo <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
 [!code-csharp[Trin_VstcoreHostControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#10)]
 [!code-vb[Trin_VstcoreHostControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#10)]  
  
 Per altre informazioni sulla proprietà Controls degli elementi host, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 I modelli a oggetti di Word ed Excel includono proprietà che espongono raccolte di controlli nativi in documenti e fogli di lavoro. Non è possibile accedere ai controlli gestiti tramite queste proprietà. Ad esempio, non è possibile enumerare ogni controllo host <xref:Microsoft.Office.Tools.Word.Bookmark> in un documento tramite la proprietà <xref:Microsoft.Office.Interop.Word._Document.Bookmarks%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Document> o la proprietà <xref:Microsoft.Office.Tools.Word.Document.Bookmarks%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Document>. Queste proprietà includono solo i controlli <xref:Microsoft.Office.Interop.Word.Bookmark> nel documento; non contengono i controlli host <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.  
  
## Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Elemento host Document](../vsto/document-host-item.md)  
  
  