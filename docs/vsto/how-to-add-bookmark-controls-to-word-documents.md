---
title: "Procedura: aggiungere controlli segnalibro ai documenti di Word"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Bookmark.Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controllo Bookmark, aggiunta ai documenti"
  - "Crea controllo Bookmark (finestra di dialogo)"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta ai documenti"
ms.assetid: 2940704e-31f5-4486-854e-76298a9e2ee4
caps.latest.revision: 52
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Procedura: aggiungere controlli segnalibro ai documenti di Word
  Nei progetti a livello di documento è possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a qualsiasi documento aperto in fase di esecuzione.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli Bookmark in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli Bookmark in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli Bookmark in fase di esecuzione in un progetto di componente aggiuntivo VSTO](#runtimeaddin)  
  
 Per altre informazioni sui controlli <xref:Microsoft.Office.Tools.Word.Bookmark>, vedere [Controllo Bookmark](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Aggiunta di controlli Bookmark in fase di progettazione  
 Sono disponibili varie modalità di aggiunta di controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento in un progetto a livello di documento in fase di progettazione:  
  
-   Dalla **Casella degli strumenti** di Visual Studio.  
  
     È possibile trascinare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> dalla **Casella degli strumenti** al documento. Scegliere questa modalità se si sta già usando la **Casella degli strumenti** per aggiungere controlli Windows Form al documento.  
  
-   Da Word.  
  
     È possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nello stesso modo in cui si aggiunge un segnalibro nativo. Il vantaggio di questa modalità è la possibilità di assegnare un nome al controllo al momento della creazione.  
  
-   Dalla finestra **Origini dati**.  
  
     È possibile trascinare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento dalla finestra **Origini dati**. Questa modalità è utile quando si vuole contemporaneamente associare il controllo ai dati. È possibile aggiungere il controllo host nello stesso modo in cui si aggiunge un controllo Windows Form dalla finestra **Origini dati**. Per altre informazioni, vedere [Associazione dati e Windows Form](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Per aggiungere un controllo Bookmark a un documento dalla casella degli strumenti  
  
1.  Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Word**.  
  
2.  Trascinare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark**.  
  
3.  Selezionare il testo o altri elementi che si desidera includere nel segnalibro.  
  
4.  Fare clic su **OK**.  
  
     Se non si vuole mantenere il nome del segnalibro predefinito, è possibile modificarlo nella finestra **Proprietà**.  
  
#### Per aggiungere un controllo Bookmark a un documento in Word  
  
1.  Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il segnalibro o selezionare il testo che deve essere racchiuso nel segnalibro.  
  
2.  Nella scheda **Inserisci** della barra multifunzione fare clic sul pulsante **Segnalibro** nel gruppo **Collegamenti**.  
  
3.  Nella finestra di dialogo **Segnalibro** digitare il nome del nuovo segnalibro e fare clic su **Aggiungi**.  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli Bookmark in fase di esecuzione in un progetto a livello di documento  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a livello di codice al documento in fase di esecuzione usando i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument` nel progetto. Ci sono due overload di metodo che è possibile usare per aggiungere un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nei modi seguenti:  
  
-   Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> in corrispondenza di un intervallo specificato.  
  
-   Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo nel documento \(ovvero un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>\).  
  
 I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo rimane nel documento. È possibile ricreare un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo alla successiva apertura del documento. Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Per aggiungere un controllo Bookmark a un documento a livello di codice  
  
1.  Nel gestore eventi `ThisDocument_Startup` nel progetto inserire il codice seguente per aggiungere il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al primo paragrafo nel documento.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsWord/VB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Se si vuole creare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> da un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> esistente, usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> e passare l'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> esistente.  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli Bookmark in fase di esecuzione in un progetto di componente aggiuntivo VSTO  
 È possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a livello di codice a qualsiasi documento aperto in fase di esecuzione usando un componente aggiuntivo VSTO. A tale scopo, generare un elemento host <xref:Microsoft.Office.Tools.Word.Document> basato su un documento aperto e quindi usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> di tale elemento host. Ci sono due overload di metodo che è possibile usare per aggiungere un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nei modi seguenti:  
  
-   Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> in corrispondenza di un intervallo specificato.  
  
-   Aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo nel documento \(ovvero un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark>\).  
  
 I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo rimane nel documento. È possibile ricreare un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato su un segnalibro nativo alla successiva apertura del documento. Per altre informazioni, vedere [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Per altre informazioni sulla generazione di elementi host in progetti di componenti aggiuntivi VSTO, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Per aggiungere un controllo Bookmark in corrispondenza di un intervallo specificato  
  
1.  Usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> e passare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> dove si vuole aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     L'esempio di codice seguente aggiunge un nuovo oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> all'inizio del documento attivo. Per usare questo esempio, eseguire il codice dal gestore eventi `ThisAddIn_Startup` in un progetto di componente aggiuntivo VSTO di Word.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#4)]  
  
#### Per aggiungere un controllo Bookmark basato su un controllo Bookmark nativo  
  
1.  Usare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> e passare l'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> esistente che si vuole usare come base per il nuovo oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     L'esempio di codice seguente crea un nuovo oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> basato sul primo oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nel documento attivo. Per usare questo esempio, eseguire il codice dal gestore eventi `ThisAddIn_Startup` in un progetto di componente aggiuntivo VSTO di Word.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDynamicControls#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#5)]  
  
## Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedura: Ridimensionare i controlli Bookmark](../vsto/how-to-resize-bookmark-controls.md)  
  
  