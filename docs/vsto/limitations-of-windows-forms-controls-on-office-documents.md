---
title: "Limitazioni dei controlli Windows Form nei documenti di Office | Microsoft Docs"
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
  - "controlli ActiveX [sviluppo per Office in Visual Studio]"
  - "controlli [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "documenti Office [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "Casella degli strumenti [sviluppo per Office in Visual Studio], controlli non supportati"
  - "controlli utente [sviluppo per Office in Visual Studio], raggruppamento di controlli"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], ActiveX legacy"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], limiti"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], Casella degli strumenti"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], proprietà e metodi non supportati"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Limitazioni dei controlli Windows Form nei documenti di Office
  Esistono alcune differenze tra i controlli Windows Form che vengono aggiunti ai documenti di Microsoft Office Word o ai fogli di lavoro di Microsoft Office Excel e i controlli Windows Form che vengono aggiunti a Windows Form.  Ad esempio, quando si aggiunge un controllo <xref:Microsoft.Office.Tools.Word.Controls.Button> a un documento, si denota un comportamento diverso dal previsto delle proprietà <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A> e <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A>.  
  
 Molte di queste differenze dipendono dal modo in cui i controlli Windows Form vengono ospitati nei documenti.  Quando si aggiunge un controllo Windows Form a un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] consente di incorporare un controllo ActiveX che a sua volta include il controllo Windows Form nel documento.  Il controllo Windows Form non è incorporato direttamente nel documento.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Limiti di metodi e proprietà dei controlli Windows Form  
 Esistono numerosi metodi e proprietà di controlli Windows Form la cui funzionalità in un documento non è identica a quella in un Windows Form, pertanto si consiglia di non utilizzarli.  Ad esempio, l'impostazione di proprietà quali `Dock` e `Anchor` influisce solo sulla posizione del controllo rispetto al controllo contenitore ActiveX invece che sul documento.  Di seguito sono elencati i metodi e le proprietà non supportati di controlli Windows Form per Word ed Excel:  
  
-   Metodi e proprietà non supportati di controlli per Excel:  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Metodi e proprietà non supportati di controlli per Word:  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Inoltre, non è possibile impostare la proprietà `Left` o `Top` dei controlli Windows Form che sono in linea con il testo di un documento di Word.  I controlli Windows Form vengono aggiunti in linea con il testo nei casi seguenti:  
  
-   Quando si aggiunge a livello di codice un controllo a un documento di Word e si utilizza un metodo che specifica un intervallo per il percorso.  
  
-   Quando si aggiunge un controllo Windows Form a un documento di Word in fase di progettazione.  Tale condizione può essere cambiata modificando il controllo nella finestra di progettazione.  
  
## Differenze tra controlli Windows Form nei documenti di Office  
 In generale, i controlli Windows Form presentano lo stesso comportamento in un documento di Office e in un Windows Form, tuttavia esistono alcune differenze.  Nella tabella seguente vengono descritte le differenze dei controlli Windows Form nei documenti di Office:  
  
|Funzionalità|Difference|  
|------------------|----------------|  
|Ordine di tabulazione dei controlli|Non è possibile spostarsi tra i controlli posizionati in un foglio di lavoro di Excel o un documento di Word con il tasto di tabulazione.|  
|Raggruppamento dei controlli|Non è possibile utilizzare un controllo <xref:System.Windows.Forms.GroupBox> per contenere altri controlli in un documento di Office.  Quando si aggiungono più pulsanti di opzione direttamente nel documento, tali pulsanti non si escludono reciprocamente.  È possibile scrivere codice per far sì che i pulsanti di opzione si escludano a vicenda, tuttavia l'approccio consigliato consiste nell'aggiungere i pulsanti di opzione a un controllo utente e aggiungere quest'ultimo al documento.  Per ulteriori informazioni, vedere Esempio di controlli di Word ed Esempio di controlli di Excel in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).|  
|Tipo di controllo|I controlli Windows Form utilizzati nei documenti sono sottoposti al wrapping in una classe fornita da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] che conferisce ai controlli funzionalità aggiuntive specifiche del foglio di lavoro di Excel o del documento di Word.  Se ad esempio si dispone di un controllo `Button` in un foglio di lavoro di Excel, assicurarsi di specificare il tipo come <xref:Microsoft.Office.Tools.Excel.Controls.Button> piuttosto che come <xref:System.Windows.Forms.Button> quando si fa riferimento o si effettua il cast dell'oggetto.|  
|Posizione e dimensioni dei controlli|La posizione e le dimensioni del controllo sono determinate da proprietà che fanno parte del controllo contenitore ActiveX.  Le proprietà dei controlli ActiveX accettano valori diversi da quelli delle proprietà equivalenti di un controllo Windows Form.  Quando si impostano le proprietà `Top`, `Left`, `Height` o `Width` di un controllo, le dimensioni sono misurate in punti invece che in pixel.|  
|Posizione del controllo nei documenti di Word|Se si aggiungono controlli a un layout basato su flussi, occorre ricordare che i controlli scorreranno con il contenuto al variare di quest'ultimo.  Non è possibile ancorare il controllo a un paragrafo quando lo si trascina dalla **Casella degli strumenti**, poiché il controllo viene aggiunto al documento di Word in linea con il testo.  Se si utilizza un altro metodo per aggiungere il controllo, facendo ad esempio doppio clic sul controllo, il controllo verrà inserito in base all'opzione di Word impostata per l'inserimento di immagini.<br /><br /> Non è possibile impostare la proprietà `Left` o `Top` di un controllo che è in linea con il testo.<br /><br /> Non è possibile posizionare i controlli in un'intestazione o in un piè di pagina oppure all'interno di un documento secondario.|  
|Eventi dei controlli|Quando si seleziona il controllo, gli eventi vengono generati nell'ordine seguente:<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Quando si deseleziona il controllo, gli eventi vengono generati nell'ordine seguente:<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Proporzioni dei controlli|Quando si modifica l'impostazione di zoom di un documento su un valore diverso da 100%, i controlli vengono disabilitati anche se sembrano essere in scala con il documento.  Se ad esempio si fa clic su un pulsante quando il fattore di zoom di un documento è impostato sul 130%, un messaggio indicherà che il controllo resterà disabilitato fino a quando lo zoom non sarà riportato al 100%.  I controlli riprenderanno a funzionare correttamente quando si riporta lo zoom al fattore del 100%.|  
|Valori di proprietà dei controlli|Sebbene le proprietà dei controlli in un Windows Form siano impostate su un Integer, esse risultano impostate su un valore single per i controlli in un documento di Word.  In Excel, i valori di proprietà dei controlli sono impostati su un valore double.  Se le proprietà `Height` e `Width` di un controllo in un foglio di lavoro superano le dimensioni del foglio di lavoro o dello schermo, il valore verrà troncato.|  
|Ridimensionamento dei controlli|Se si ridimensiona un controllo nel documento utilizzando uno degli otto quadratini di ridimensionamento, le dimensioni del nuovo controllo non saranno riflesse nella finestra **Proprietà** finché non si seleziona di nuovo il controllo.|  
|Comportamento dei controlli|I controlli in un foglio di lavoro di Excel possono comportarsi in modo imprevisto quando si suddivide la finestra del foglio di lavoro.  L'accesso a un controllo <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> nel foglio di lavoro, ad esempio, potrebbe essere disponibile solo in una delle finestre.|  
|Denominazione dei controlli|Non è possibile utilizzare parole riservate per i nomi dei controlli.  Se ad esempio si aggiunge un controllo <xref:Microsoft.Office.Tools.Excel.Controls.Button> a un foglio di lavoro e si modifica il nome in **System**, si verificheranno degli errori durante la compilazione del progetto.|  
|Aggiunta di controlli a livello di codice|Non utilizzare il costruttore del controllo per aggiungere un controllo al documento in fase di esecuzione.  È necessario utilizzare invece i metodi di supporto forniti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Per aggiungere un pulsante a un foglio di lavoro, ad esempio, utilizzare il metodo <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A>.  Se si desidera aggiungere un controllo non supportato da questi metodi di supporto, è possibile utilizzare il metodo AddControl.  Per ulteriori informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Copia dei controlli|Se si copia e inserisce un controllo Windows Form in un documento in fase di esecuzione, nel documento verrà inserito un controllo contenitore ActiveX vuoto.  Il controllo Windows Form non viene visualizzato nella nuova posizione e il codice sul quale si basa il controllo originale non viene copiato nel controllo contenitore ActiveX.|  
  
## Limitazioni nei progetti a livello di documento  
 Alcune limitazioni relative all'utilizzo dei controlli Windows Form nei documenti sono univoche per i progetti a livello di documento.  
  
### Supporto del controllo in fase di progettazione  
 Determinati controlli Windows Form vengono rimossi dalla **Casella degli strumenti** nel momento in cui un foglio di lavoro di Excel o un documento di Word viene aperto nella finestra di progettazione di Visual Studio.  Ciò è dovuto a limitazioni tecniche o al fatto che la funzionalità sia già disponibile in Word o Excel.  I progetti Excel e Word supportano tutti i controlli Windows Form e gli altri componenti disponibili nella **Casella degli strumenti** quando lo stato del documento è attivo; è inoltre possibile aggiungere i controlli di terze parti a un foglio di lavoro o a un documento.  
  
> [!NOTE]  
>  Tutti i controlli vengono rimossi dalla **Casella degli strumenti** nel momento in cui un documento viene protetto.  Per informazioni sulla protezione dei documenti, vedere [Sicurezza dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  I controlli di terze parti devono avere l'attributo <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su **true** affinché possano essere utilizzati in una soluzione Office.  
  
 Nella **Casella degli strumenti** non sono disponibili i controlli e i componenti seguenti:  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### Supporto per i controlli ActiveX legacy  
 Se si crea un progetto Office a livello di documento utilizzando un documento di Word o una cartella di lavoro di Excel esistente che contiene controlli ActiveX, la funzionalità dei controlli ActiveX non andrà persa. Tuttavia, non sarà disponibile alcun supporto per l'aggiunta di nuovi controlli ActiveX ai documenti all'interno di Visual Studio.  Se, ad esempio, il documento di Word dispone di un pulsante della casella degli strumenti **Controllo** che consente di eseguire una macro VBA \(Visual Basic, Applications Edition\), la macro continuerà a essere eseguita anche dopo aver utilizzato il documento in un progetto di Office.  Si consiglia tuttavia di rimuovere i controlli ActiveX e le macro VBA e sostituirli con controlli Windows Form e codice gestito.  
  
## Vedere anche  
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  