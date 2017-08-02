---
title: "Aggiunta di controlli ai documenti di Office in fase di esecuzione"
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
  - "documenti di Office [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "controlli host [sviluppo per Office in Visual Studio], aggiunta"
  - "controlli Windows Form [sviluppo per Office in Visual Studio], aggiunta"
  - "documenti di Office [sviluppo per Office in Visual Studio], controlli host"
  - "controlli utente [sviluppo per Office in Visual Studio], aggiunta in fase di esecuzione"
  - "documenti [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], controlli host"
  - "documenti [sviluppo per Office in Visual Studio], controlli host"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta in fase di esecuzione"
  - "metodi di supporto [sviluppo per Office in Visual Studio]"
ms.assetid: 4f43b3eb-f0ec-44e2-9885-6ede327c6913
caps.latest.revision: 102
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 101
---
# Aggiunta di controlli ai documenti di Office in fase di esecuzione
  È possibile aggiungere controlli a un documento di Microsoft Office Word e a una cartella di lavoro di Microsoft Office Excel in fase di esecuzione. È inoltre possibile rimuoverli in fase di esecuzione. I controlli aggiunti o rimossi in fase di esecuzione sono noti come *controlli dinamici*.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 In questo argomento viene illustrato quanto segue:  
  
-   [Gestione dei controlli in fase di esecuzione usando le raccolte di controlli](#ControlsCollection).  
  
-   [Aggiunta di controlli host ai documenti](#HostControls).  
  
-   [Aggiunta di controlli Windows Form ai documenti](#WindowsForms).  
  
 ![Collegamento a video](~/data-tools/media/playvideo.gif "Collegamento a video") Per una dimostrazione video correlata, vedere l'argomento relativo alla [procedura di aggiunta di controlli all'area di un documento in fase di esecuzione](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="ControlsCollection"></a> Gestione dei controlli in fase di esecuzione usando le raccolte di controlli  
 Per aggiungere, ottenere o rimuovere i controlli in fase di esecuzione, usare i metodi di supporto degli oggetti <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection>.  
  
 La modalità di accesso a questi oggetti dipende dal tipo di progetto che si sta sviluppando:  
  
-   In un progetto a livello di documento per Excel, usare la proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> delle classi `Sheet1`, `Sheet2` e `Sheet3`. Per altre informazioni su queste classi, vedere [Elemento host Worksheet](../vsto/worksheet-host-item.md).  
  
-   In un progetto a livello di documento per Word, usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument`. Per altre informazioni su questa classe, vedere [Elemento host Document](../vsto/document-host-item.md).  
  
-   In un progetto di componente aggiuntivo VSTO per Excel o Word, usare la proprietà Controls di un oggetto <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> generato in fase di esecuzione. Per altre informazioni sulla generazione di questi oggetti in fase di esecuzione, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### Aggiunta di controlli  
 I tipi <xref:Microsoft.Office.Tools.Excel.ControlCollection> e <xref:Microsoft.Office.Tools.Word.ControlCollection> includono metodi di supporto che è possibile usare per aggiungere controlli host e controlli Windows Form comuni a documenti e fogli di lavoro. Il nome di ciascun metodo presenta il formato `Add` *classe del controllo*, dove *classe del controllo* rappresenta il nome del controllo che si desidera aggiungere. Ad esempio, per aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> al documento, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddNamedRange%2A>.  
  
 Nell'esempio di codice seguente viene aggiunto un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un oggetto `Sheet1` di un progetto a livello di documento per Excel.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/ThisWorkbook.cs#3)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/ThisWorkbook.vb#3)]  
  
### Accesso ai controlli e relativa eliminazione  
 È possibile usare la proprietà Controls di un oggetto <xref:Microsoft.Office.Tools.Excel.Worksheet> o <xref:Microsoft.Office.Tools.Word.Document> per scorrere tutti i controlli nel documento, compresi i controlli aggiunti in fase di progettazione. Questi controlli sono anche noti come *controlli statici*.  
  
 Per rimuovere i controlli dinamici, è possibile chiamare il metodo Delete del controllo oppure il metodo Remove di ogni raccolta Controls. Nell'esempio di codice seguente, il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.Remove%2A> viene usato per rimuovere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> dall'oggetto `Sheet1` di un progetto a livello di documento per Excel.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/ThisWorkbook.cs#4)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/ThisWorkbook.vb#4)]  
  
 I controlli statici non possono essere rimossi in fase di esecuzione. Se si tenta di usare il metodo Delete o il metodo Remove per rimuovere un controllo statico, verrà generata un'eccezione <xref:Microsoft.Office.Tools.CannotRemoveControlException>.  
  
> [!NOTE]  
>  Non rimuovere a livello di codice i controlli nel gestore eventi `Shutdown` del documento. Gli elementi di interfaccia utente del documento non sono più disponibili quando viene generato l'evento `Shutdown`. Se si desidera rimuovere i controlli prima della chiusura del documento, aggiungere il codice al gestore eventi per un altro evento, ad esempio  <xref:Microsoft.Office.Tools.Word.Document.BeforeClose> o <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> per Word oppure <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeClose> o <xref:Microsoft.Office.Tools.Excel.Workbook.BeforeSave> per Excel.  
  
##  <a name="HostControls"></a> Aggiunta di controlli host ai documenti  
 Quando si aggiunge a livello di codice un controllo host a un documento, è necessario specificare un nome che identifichi il controllo in modo univoco, nonché la posizione del documento in cui aggiungere il controllo. Per istruzioni specifiche, vedere gli argomenti seguenti:  
  
-   [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)  
  
-   [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)  
  
-   [Procedura: aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)  
  
-   [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)  
  
-   [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)  
  
 Per altre informazioni sui controlli host, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
 Quando si salva e si chiude un documento, tutti i controlli host creati dinamicamente vengono disconnessi dai relativi eventi e perdono le proprie funzionalità di associazione dati. È possibile aggiungere codice alla soluzione per ricreare i controlli host quando il documento viene riaperto. Per altre informazioni, vedere [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
> [!NOTE]  
>  I controlli host <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, <xref:Microsoft.Office.Tools.Word.XMLNode> e <xref:Microsoft.Office.Tools.Word.XMLNodes> non possono essere aggiunti a livello di codice ai documenti. Di conseguenza, per tali controlli non viene fornito alcun metodo di supporto.  
  
##  <a name="WindowsForms"></a> Aggiunta di controlli Windows Form ai documenti  
 Quando si aggiunge a livello di codice un controllo Windows Form a un documento, è necessario fornire il percorso del controllo e un nome che lo identifichi in modo univoco. Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fornisce metodi di supporto per ogni controllo. Questi metodi sono sottoposti a overload per consentire il passaggio di un intervallo o le coordinate specifiche per la posizione del controllo.  
  
 Quando si salva e si chiude un documento, tutti i controlli Windows Form creati dinamicamente vengono rimossi dal documento. È possibile aggiungere codice alla soluzione per ricreare i controlli quando il documento viene riaperto. Se si creano controlli Windows Form dinamici tramite un componente aggiuntivo a livello di applicazione, i wrapper ActiveX dei controlli rimangono nel documento. Per altre informazioni, vedere [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
> [!NOTE]  
>  I controlli Windows Form non possono essere aggiunti a documenti protetti a livello di codice. Per rimuovere a livello di codice la protezione di un documento di Word o di un foglio di lavoro di Excel allo scopo di aggiungere un controllo, è necessario scrivere codice aggiuntivo per rimuovere il wrapper ActiveX del controllo alla chiusura del documento. Il wrapper ActiveX del controllo non viene eliminato automaticamente dai documenti protetti.  
  
### Aggiunta di controlli personalizzati  
 Se si desidera aggiungere un <xref:System.Windows.Forms.Control> non supportato dai metodi di supporto disponibili, ad esempio un controllo utente personalizzato, usare i metodi seguenti:  
  
-   Per Excel, usare uno dei metodi <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> di un oggetto <xref:Microsoft.Office.Tools.Excel.ControlCollection>.  
  
-   Per Word, usare uno dei metodi <xref:Microsoft.Office.Tools.Word.ControlCollection.AddControl%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.ControlCollection>.  
  
 Per aggiungere il controllo, passare il controllo <xref:System.Windows.Forms.Control>, la posizione del controllo e un nome che lo identifichi in modo univoco per il metodo AddControl. Il metodo AddControl restituisce un oggetto che definisce la modalità di interazione del controllo con il foglio di lavoro o il documento. Il metodo AddControl restituisce un oggetto <xref:Microsoft.Office.Tools.Excel.ControlSite> \(per Excel\) o <xref:Microsoft.Office.Tools.Word.ControlSite> \(per Word\).  
  
 Nell'esempio di codice seguente viene illustrato come usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddControl%2A> per aggiungere dinamicamente un controllo utente personalizzato a un foglio di lavoro in un progetto Excel a livello di documento. In questo esempio, il controllo utente è denominato `UserControl1` e <xref:Microsoft.Office.Interop.Excel.Range> è denominato `range1`. Per usare questo esempio, eseguirlo dalla classe `Sheet`*n* nel progetto.  
  
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#2)]
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#2)]  
  
### Uso dei membri di controlli personalizzati  
 Dopo aver usato uno dei metodi AddControl per aggiungere un controllo a un foglio di lavoro o a un documento, si dispone di due oggetti controllo diversi:  
  
-   Il controllo <xref:System.Windows.Forms.Control> che rappresenta il controllo personalizzato.  
  
-   Oggetto ControlSite, OLEObject o OLEControl che rappresenta il controllo dopo l'aggiunta al foglio di lavoro o al documento.  
  
 Questi controlli condividono molti metodi e proprietà. È importante accedere a questi membri mediante il controllo appropriato:  
  
-   Per accedere ai membri appartenenti esclusivamente al controllo personalizzato, usare <xref:System.Windows.Forms.Control>.  
  
-   Per accedere a membri condivisi dai controlli, usare l'oggetto ControlSite, OLEObject o OLEControl.  
  
 Se si accede a un membro condiviso da <xref:System.Windows.Forms.Control>, è possibile che vengano generati risultati non validi oppure che si verifichi un errore senza che vengano visualizzati avvisi o notifiche. Usare sempre i metodi o le proprietà dell'oggetto ControlSite, OLEObject o OLEControl, a meno che il metodo o la proprietà da usare non sia disponibile; solo in questo caso è opportuno fare riferimento a <xref:System.Windows.Forms.Control>.  
  
 Ad esempio, sia la classe <xref:Microsoft.Office.Tools.Excel.ControlSite> che la classe <xref:System.Windows.Forms.Control> dispongono di una proprietà Top. Per ottenere o impostare la distanza fra la parte superiore del controllo e quella del documento, usare la proprietà <xref:Microsoft.Office.Tools.Excel.ControlSite.Top%2A> del controllo <xref:Microsoft.Office.Tools.Excel.ControlSite> anziché la proprietà <xref:System.Windows.Forms.Control.Top%2A> del controllo <xref:System.Windows.Forms.Control>.  
  
 [!code-csharp[Trin_VstcoreProgrammingControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#3)]
 [!code-vb[Trin_VstcoreProgrammingControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#3)]  
  
## Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Procedura: Aggiungere controlli ListObject a fogli di lavoro](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Procedura: aggiungere controlli Chart a fogli di lavoro](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  