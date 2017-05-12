---
title: "Procedura: aggiungere controlli del contenuto ai documenti di Word"
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
  - "autorizzazioni limitate [sviluppo per Office in Visual Studio]"
  - "DropDownListContentControl, aggiunta ai documenti"
  - "BuildingBlockGalleryContentControl, aggiunta ai documenti"
  - "protezione parziale di documenti [sviluppo per Office in Visual Studio]"
  - "RichTextContentControl, aggiunta ai documenti"
  - "Word [sviluppo per Office in Visual Studio], protezione parziale di documenti"
  - "controlli del contenuto [sviluppo per Office in Visual Studio], protezione"
  - "PictureContentControl, aggiunta ai documenti"
  - "GroupContentControl, aggiunta ai documenti"
  - "protezione di documenti [sviluppo per Office in Visual Studio]"
  - "PlainTextContentControl, aggiunta ai documenti"
  - "controlli contenuto [sviluppo per Office in Visual Studio], aggiunta"
  - "ComboBoxContentControl, aggiunta ai documenti"
  - "DatePickerContentControl, aggiunta ai documenti"
  - "Word [sviluppo per Office in Visual Studio], autorizzazioni limitate"
ms.assetid: 68ddb24e-71c6-46f7-8e11-c9899d7814df
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Procedura: aggiungere controlli del contenuto ai documenti di Word
  Nei progetti di Word a livello di documento è possibile aggiungere controlli contenuto al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO di Word è possibile aggiungere controlli contenuto a qualsiasi documento aperto in fase di esecuzione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli contenuto in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli contenuto in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli contenuto in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per informazioni sui controlli contenuto, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Aggiunta di controlli contenuto in fase di progettazione  
 Sono disponibili varie modalità di aggiunta di controlli contenuto al documento in un progetto a livello di documento in fase di progettazione:  
  
-   Aggiungere un controllo contenuto dalla scheda **Controlli Word** della **Casella degli strumenti**.  
  
-   Aggiungere un controllo contenuto al documento nello stesso modo in cui si aggiunge un controllo contenuto nativo in Word.  
  
-   Trascinare un controllo contenuto nel documento dalla finestra **Origini dati**. Questa modalità è utile quando si vuole associare il controllo ai dati al momento della creazione del controllo. Per altre informazioni, vedere [Procedura: Popolare documenti con i dati di oggetti](../vsto/how-to-populate-documents-with-data-from-objects.md) e [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Per aggiungere un controllo contenuto a un documento tramite la casella degli strumenti  
  
1.  Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il controllo contenuto o selezionare il testo che deve essere sostituito dal controllo contenuto.  
  
2.  Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Word**.  
  
3.  Aggiungere il controllo in uno dei modi seguenti:  
  
    -   Fare doppio clic su un controllo contenuto nella **Casella degli strumenti**.  
  
         oppure  
  
    -   Fare clic su un controllo contenuto nella **Casella degli strumenti** e quindi premere INVIO.  
  
         oppure  
  
    -   Trascinare un controllo contenuto dalla **Casella degli strumenti** nel documento. Il controllo contenuto viene aggiunto in corrispondenza della selezione corrente nel documento, non in corrispondenza della posizione del puntatore del mouse.  
  
> [!NOTE]  
>  Non è possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> usando la **Casella degli strumenti**. È possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> solo in Word o in fase di esecuzione.  
  
> [!NOTE]  
>  Visual Studio non fornisce un controllo contenuto casella di controllo nella casella degli strumenti. Per aggiungere un controllo contenuto casella di controllo al documento, è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> a livello di codice. Per altre informazioni, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
#### Per aggiungere un controllo contenuto a un documento in Word  
  
1.  Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il controllo contenuto o selezionare il testo che deve essere sostituito dal controllo contenuto.  
  
2.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Nel gruppo **Controlli** fare clic sull'icona del controllo contenuto che si desidera aggiungere.  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli contenuto in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere controlli contenuto a livello di codice al documento in fase di esecuzione usando i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument` nel progetto. Ogni metodo ha tre overload che è possibile usare per aggiungere un controllo contenuto nei modi seguenti:  
  
-   Aggiungere un controllo in corrispondenza della selezione corrente.  
  
-   Aggiungere un controllo in corrispondenza di un intervallo specificato.  
  
-   Aggiungere un controllo basato su un controllo contenuto nativo nel documento.  
  
 I controlli contenuto creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un controllo contenuto nativo rimane nel documento. È possibile ricreare un controllo contenuto basato su un controllo contenuto nativo alla successiva apertura del documento. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Per aggiungere un controllo contenuto casella di controllo a un documento in un progetto di Word 2010, è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl>. Per altre informazioni, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
#### Per aggiungere un controllo contenuto in corrispondenza della selezione corrente  
  
1.  Usare un metodo <xref:Microsoft.Office.Tools.Word.ControlCollection> con nome `Add`\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) e con un singolo parametro per il nome del nuovo controllo.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddRichTextControlAtSelection` dal gestore eventi `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#700](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#700)]  
  
#### Per aggiungere un controllo contenuto in corrispondenza di un intervallo specificato  
  
1.  Usare un metodo <xref:Microsoft.Office.Tools.Word.ControlCollection> con nome `Add`\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) e con un parametro <xref:Microsoft.Office.Interop.Word.Range>.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddRichTextControlAtRange` dal gestore eventi `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#701](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#701)]  
  
#### Per aggiungere un controllo contenuto basato su un controllo contenuto nativo  
  
1.  Usare un metodo <xref:Microsoft.Office.Tools.Word.ControlCollection> con nome `Add`\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) e con un parametro Microsoft.Office.Interop.Word.ContentControl.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per creare un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per ogni controllo in formato RTF nativo nel documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `CreateRichTextControlsFromNativeControls` dal gestore eventi `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#702](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli contenuto in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere controlli contenuto a livello di codice a qualsiasi documento aperto in fase di esecuzione usando un componente aggiuntivo VSTO. A tale scopo, generare un elemento host <xref:Microsoft.Office.Tools.Word.Document> basato su un documento aperto e quindi usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> di tale elemento host. Ogni metodo ha tre overload che è possibile usare per aggiungere un controllo contenuto nei modi seguenti:  
  
-   Aggiungere un controllo in corrispondenza della selezione corrente.  
  
-   Aggiungere un controllo in corrispondenza di un intervallo specificato.  
  
-   Aggiungere un controllo basato su un controllo contenuto nativo nel documento.  
  
 I controlli contenuto creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un controllo contenuto nativo rimane nel documento. È possibile ricreare un controllo contenuto basato su un controllo contenuto nativo alla successiva apertura del documento. Per altre informazioni, vedere [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Per altre informazioni sulla generazione di elementi host in progetti di componenti aggiuntivi VSTO, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Per aggiungere un controllo contenuto casella di controllo a un documento è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl>. Per altre informazioni, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
#### Per aggiungere un controllo contenuto in corrispondenza della selezione corrente  
  
1.  Usare un metodo <xref:Microsoft.Office.Tools.Word.ControlCollection> con nome `Add`\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) e con un singolo parametro per il nome del nuovo controllo.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento attivo. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddRichTextControlAtSelection` dal gestore eventi `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
#### Per aggiungere un controllo contenuto in corrispondenza di un intervallo specificato  
  
1.  Usare un metodo <xref:Microsoft.Office.Tools.Word.ControlCollection> con nome `Add`\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) e con un parametro <xref:Microsoft.Office.Interop.Word.Range>.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento attivo. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddRichTextControlAtRange` dal gestore eventi `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
#### Per aggiungere un controllo contenuto basato su un controllo contenuto nativo  
  
1.  Usare un metodo <xref:Microsoft.Office.Tools.Word.ControlCollection> con nome `Add`\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) e con un parametro Microsoft.Office.Interop.Word.ContentControl.  
  
     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per creare un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per ogni controllo in formato RTF nativo in un documento, dopo l'apertura del documento. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
     Per C\#, è anche necessario collegare il gestore eventi `Application_DocumentOpen` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#6)]  
  
## Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)  
  
  