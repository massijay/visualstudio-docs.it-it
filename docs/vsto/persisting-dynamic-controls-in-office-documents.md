---
title: "Persistenza dei controlli dinamici nei documenti di Office"
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
  - "documenti di Office [sviluppo per Office in Visual Studio], controlli host"
  - "controlli [sviluppo per Office in Visual Studio], persistenza nel documento"
  - "controlli Windows Form [sviluppo per Office in Visual Studio], persistenza nel documento"
  - "documenti [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "documenti [sviluppo per Office in Visual Studio], controlli host"
  - "controlli host [sviluppo per Office in Visual Studio], persistenza nel documento"
ms.assetid: 200352d1-66aa-4156-9ecd-6fd8792974cd
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Persistenza dei controlli dinamici nei documenti di Office
  I controlli che vengono aggiunti in fase di esecuzione non vengono mantenuti al salvataggio e alla chiusura di un documento o di una cartella di lavoro. Il comportamento effettivo varia a seconda che il controllo sia host o Windows Form. In entrambi casi è possibile aggiungere codice alla soluzione per ricreare i controlli quando l'utente riapre il documento.  
  
 I controlli aggiunti ai documenti in fase di esecuzione sono noti come *controlli dinamici*. Per altre informazioni sui controlli dinamici, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Persistenza dei controlli host nel documento  
 Quando si salva e si chiude un documento, tutti i controlli host dinamici vengono rimossi dal documento. Soltanto gli oggetti nativi di Office sottostanti restano nel documento. Ad esempio, un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject> diviene <xref:Microsoft.Office.Interop.Excel.ListObject>. Gli oggetti nativi di Office non sono connessi agli eventi del controllo host e non dispongono della funzionalità di associazione dati del controllo host.  
  
 Nella tabella seguente viene indicato l'oggetto nativo di Office che resta in un documento per ogni tipo di controllo host.  
  
|Tipo di controllo host|Tipo di oggetto nativo di Office|  
|----------------------------|--------------------------------------|  
|<xref:Microsoft.Office.Tools.Excel.Chart>|<xref:Microsoft.Office.Interop.Excel.Chart>|  
|<xref:Microsoft.Office.Tools.Excel.ListObject>|<xref:Microsoft.Office.Interop.Excel.ListObject>|  
|<xref:Microsoft.Office.Tools.Excel.NamedRange>|<xref:Microsoft.Office.Interop.Excel.Range>|  
|<xref:Microsoft.Office.Tools.Word.Bookmark>|<xref:Microsoft.Office.Interop.Word.Bookmark>|  
|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DropDownListContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.GroupContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PictureContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|<xref:Microsoft.Office.Interop.Word.ContentControl>|  
  
### Ricreazione di controlli host dinamici all'apertura dei documenti  
 È possibile ricreare controlli host dinamici al posto dei controlli nativi esistenti ogni volta che un utente apre un documento. Questa modalità di creazione dei controlli host all'apertura di un documento simula l'esperienza d'uso prevista dagli utenti.  
  
 Per ricreare un controllo host per Word o un controllo host <xref:Microsoft.Office.Tools.Excel.NamedRange> o <xref:Microsoft.Office.Tools.Excel.ListObject> per Excel, usare un metodo `Add`\<*classe di controllo*\> di un oggetto <xref:Microsoft.Office.Tools.Excel.ControlCollection> o <xref:Microsoft.Office.Tools.Word.ControlCollection>. Usare un metodo che dispone di un parametro per l'oggetto nativo di Office.  
  
 Ad esempio, se si desidera creare un controllo host <xref:Microsoft.Office.Tools.Excel.ListObject> da un controllo nativo <xref:Microsoft.Office.Interop.Excel.ListObject> esistente quando il documento viene aperto, usare il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddListObject%2A> e passare il controllo <xref:Microsoft.Office.Interop.Excel.ListObject> esistente. Nell'esempio di codice seguente viene illustrata la stessa procedura in un progetto a livello di documento per Excel. Il codice ricrea un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> dinamico basato su un oggetto <xref:Microsoft.Office.Interop.Excel.ListObject> esistente denominato `MyListObject` nella classe `Sheet1`.  
  
 [!code-csharp[Trin_ExcelWorkbookDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/CS/Sheet1.cs#6)]
 [!code-vb[Trin_ExcelWorkbookDynamicControls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelWorkbookDynamicControls/VB/Sheet1.vb#6)]  
  
### Ricreazione di grafici  
 Per ricreare un controllo host <xref:Microsoft.Office.Tools.Excel.Chart>, è innanzitutto necessario eliminare l'oggetto nativo <xref:Microsoft.Office.Interop.Excel.Chart> e quindi ricreare <xref:Microsoft.Office.Tools.Excel.Chart> usando il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A> oppure il metodo <xref:Microsoft.Office.Tools.Excel.ControlCollection.AddChart%2A>. Non è disponibile alcun metodo `Add`\<*classe di controllo*\> che consenta di creare un nuovo <xref:Microsoft.Office.Tools.Excel.Chart> basato su un <xref:Microsoft.Office.Interop.Excel.Chart> esistente.  
  
 Se non si elimina innanzitutto l'oggetto <xref:Microsoft.Office.Interop.Excel.Chart> nativo, verrà creato un secondo grafico duplicato quando si ricrea <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
## Persistenza dei controlli Windows Form nei documenti  
 Quando si salva e si chiude un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuove automaticamente dal documento tutti i controlli Windows Form creati dinamicamente. Tuttavia, il comportamento varia a seconda che il progetto sia a livello di documento o a livello di componente aggiuntivo VSTO.  
  
 Nelle personalizzazioni a livello di documento, i controlli e i relativi wrapper ActiveX sottostanti \(usati per ospitare i controlli nel documento\) vengono rimossi alla successiva apertura del documento. Dopo la rimozione, dei controlli non resta alcuna traccia.  
  
 Anche nei componenti aggiuntivi VSTO i controlli vengono rimossi, tuttavia i wrapper ActiveX rimangono nel documento. Alla successiva apertura del documento da parte dell'utente, i wrapper ActiveX sono visibili. In Excel, i wrapper ActiveX visualizzano le immagini dei controlli nello stesso modo in cui erano visualizzati l'ultima volta che il documento è stato salvato. In Word, i wrapper ActiveX sono invisibili a meno che l'utente non faccia clic su di essi. In questo caso, viene visualizzata una linea punteggiata che delinea il bordo dei controlli. Esistono diversi modi per rimuovere i wrapper ActiveX. Per altre informazioni, vedere [Rimozione dei wrapper ActiveX contenuti in un componente aggiuntivo](#removingActiveX).  
  
### Ricreazione di controlli Windows Form all'apertura dei documenti  
 È possibile ricreare i controlli Windows Form eliminati quando l'utente riapre il documento. A questo scopo, la soluzione deve eseguire le attività seguenti:  
  
1.  Memorizzare le informazioni sulla dimensione, il percorso e lo stato dei controlli quando il documento viene salvato o chiuso. In una personalizzazione a livello di documento, questi dati possono essere salvati nella cache di dati del documento. In un componente aggiuntivo VSTO, questi dati possono essere salvati in una parte XML personalizzata del documento.  
  
2.  Ricreare i controlli in un evento generato all'apertura del documento. Nei progetti a livello di documento, questa attività può essere eseguita nei gestori eventi `Sheet`*n*`_Startup` o `ThisDocument_Startup`. Nei progetti di componenti aggiuntivi VSTO, questa attività può essere eseguita nei gestori degli eventi <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
###  <a name="removingActiveX"></a> Rimozione dei wrapper ActiveX contenuti in un componente aggiuntivo  
 Quando si usa un componente aggiuntivo VSTO per aggiungere controlli Windows Form dinamici ai documenti, è possibile impedire che i wrapper ActiveX dei controlli vengano visualizzati nel documento alla successiva apertura di quest'ultimo.  
  
#### Rimozione dei wrapper ActiveX all'apertura del documento  
 Per rimuovere tutti i wrapper ActiveX, chiamare il metodo GetVstoObject per generare un elemento host per l'oggetto <xref:Microsoft.Office.Interop.Word.Document> o <xref:Microsoft.Office.Interop.Excel.Workbook> che rappresenta il documento appena aperto. Ad esempio, per rimuovere tutti i wrapper ActiveX da un documento di Word, è possibile chiamare il metodo GetVstoObject per generare un elemento host per l'oggetto <xref:Microsoft.Office.Interop.Word.Document> passato al gestore dell'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
 Questa procedura è utile quando si sa che il documento verrà aperto solo su computer in cui è stato installato il componente aggiuntivo VSTO. Se esiste la possibilità che il documento venga passato ad altri utenti che non hanno installato il componente aggiuntivo VSTO, rimuovere i controlli prima di chiudere il documento.  
  
 Nell'esempio di codice seguente viene illustrato come chiamare il metodo GetVstoObject all'apertura del documento.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#11)]
 [!code-vb[Trin_WordAddInDynamicControls#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#11)]  
  
 Benché venga usato principalmente per generare un nuovo elemento host in fase di esecuzione, il metodo GetVstoObject cancella tutti i wrapper ActiveX dal documento la prima volta che viene chiamato per un documento specifico. Per altre informazioni su come usare il metodo GetVstoObject, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Si noti che, se il componente aggiuntivo VSTO crea controlli dinamici all'apertura del documento, chiamerà già il metodo GetVstoObject come parte del processo di creazione dei controlli. In questo caso, non occorre aggiungere alcuna chiamata a parte al metodo GetVstoObject per rimuovere i wrapper ActiveX.  
  
#### Rimozione dei controlli dinamici prima della chiusura del documento  
 Il componente aggiuntivo VSTO può rimuovere in modo esplicito ogni controllo dinamico dal documento prima che quest'ultimo venga chiuso. Questa procedura è utile per i documenti che possono essere passati a utenti che non hanno installato il componente aggiuntivo VSTO.  
  
 Nell'esempio di codice seguente viene illustrato come rimuovere tutti i controlli Windows Form da un documento di Word alla chiusura del documento.  
  
 [!code-csharp[Trin_WordAddInDynamicControls#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#10)]
 [!code-vb[Trin_WordAddInDynamicControls#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#10)]  
  
## Vedere anche  
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  