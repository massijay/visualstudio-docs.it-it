---
title: "Procedura: aggiungere controlli Windows Form a documenti di Office | Microsoft Docs"
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
  - "controlli [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "documenti [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "documenti Office [sviluppo per Office in Visual Studio], controlli Windows Form"
  - "Windows Form (controlli) [sviluppo per Office in Visual Studio], aggiunta"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura: aggiungere controlli Windows Form a documenti di Office
  È possibile aggiungere controlli Windows Form a documenti di Microsoft Office Excel e Microsoft Office Word in fase di progettazione in progetti a livello di documento.  È possibile aggiungere controlli nelle personalizzazioni a livello di documento e nei componenti aggiuntivi VSTO in fase di esecuzione.  È possibile, ad esempio, aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> al foglio di lavoro in modo che l'utente possa effettuare una selezione da un elenco di opzioni.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Questo argomento descrive le attività seguenti:  
  
-   [Aggiunta di controlli in fase di progettazione](#designtime)  
  
-   [Aggiunta di controlli in fase di esecuzione in progetti a livello di documento](#runtimedoclevel)  
  
-   [Aggiunta di controlli in fase di esecuzione in componenti aggiuntivi VSTO](#runtimeaddin)  
  
 ![Collegamento a video](../vsto/media/playvideo.png "Collegamento a video") Per una dimostrazione video correlata, vedere l'argomento relativo alla [procedura di aggiunta di controlli all'area di un documento in fase di esecuzione](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Aggiunta di controlli in fase di progettazione  
 Sono disponibili varie modalità di aggiunta di controlli Windows Form al documento in un progetto a livello di documento in fase di progettazione.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Per trascinare un controllo Windows sul documento  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione.  Per informazioni sulla creazione di progetti vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nella scheda **Controlli comuni** della **Casella degli strumenti** fare clic sul controllo che si vuole aggiungere e trascinarlo nel documento.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **\=EMBED\("WinForms.Control.Host",""\)**  nella **Barra della formula**.  Questo testo è necessario e non deve essere eliminato.  
  
#### Per trascinare un controllo Windows Form sul documento  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione.  Per informazioni sulla creazione di progetti vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nella scheda **Controlli comuni** della **Casella degli strumenti** fare clic sul controllo da aggiungere.  
  
3.  Nel documento fare clic sul punto in cui si vuole posizionare l'angolo superiore sinistro del controllo e trascinare fino al punto in cui si vuole posizionare l'angolo inferiore destro.  
  
     Il controllo viene aggiunto al documento con la dimensione e la posizione specificate.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **\=EMBED\("WinForms.Control.Host",""\)**  nella **Barra della formula**.  Questo testo è necessario e non deve essere eliminato.  
  
#### Per aggiungere un controllo Windows al documento facendo un singolo clic sul controllo  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione.  Per informazioni sulla creazione di progetti vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nella scheda **Controlli comuni** della **Casella degli strumenti** fare clic sul controllo da aggiungere  
  
3.  Nel documento fare clic nel punto in cui si vuole aggiungere il controllo.  
  
     Il controllo viene aggiunto al documento con la dimensione predefinita.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **\=EMBED\("WinForms.Control.Host",""\)** nella **Barra della formula**.  Questo testo è necessario e non deve essere eliminato.  
  
#### Per aggiungere un controllo Windows al documento facendo un doppio clic sul controllo  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione.  Per informazioni sulla creazione di progetti vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nella scheda **Controlli comuni** della **Casella degli strumenti** fare doppio clic sul controllo da aggiungere.  
  
     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **\=EMBED\("WinForms.Control.Host",""\)** nella **Barra della formula**.  Questo testo è necessario e non deve essere eliminato.  
  
#### Per aggiungere un controllo Windows Form al documento premendo INVIO  
  
1.  Creare o aprire un progetto di una cartella di lavoro Excel o un progetto di documento di Word in Visual Studio per visualizzare il documento nella finestra di progettazione.  Per informazioni sulla creazione di progetti vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Nella scheda **Controlli comuni** della **Casella degli strumenti** fare clic sul controllo che si vuole aggiungere e premere INVIO.  
  
     Il controllo viene aggiunto al documento al centro del documento o del riquadro attivo.  
  
    > [!NOTE]  
    >  Quando si seleziona un controllo in Excel, verrà visualizzato **\=EMBED\("WinForms.Control.Host",""\)** nella **Barra della formula**.  Questo testo è necessario e non deve essere eliminato.  
  
##  <a name="runtimedoclevel"></a> Aggiunta di controlli in fase di esecuzione in progetti a livello di documento  
 È possibile aggiungere controlli Windows Form a livello di codice a un documento in fase di esecuzione.  In Word usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> della classe `ThisDocument`.  In Excel usare i metodi della proprietà <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> di una classe `Sheet`*n*.  Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.  
  
 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso.  È possibile ricreare il controllo alla prossima apertura del documento.  Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Per aggiungere un controllo Windows Form in fase di esecuzione  
  
1.  Usare un metodo che presenta il nome Add\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo Windows Form che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
     L'esempio di codice seguente illustra come aggiungere un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.Button> alla cella **C5** dell'oggetto `Sheet1` in un progetto a livello di documento per Excel.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> Aggiunta di controlli in fase di esecuzione in componenti aggiuntivi VSTO  
 È possibile aggiungere controlli Windows Form a livello di codice a qualsiasi documento aperto in fase di esecuzione.  Generare innanzitutto un elemento host basato su un foglio di lavoro o un documento aperto.  In Word usare quindi i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuovo elemento host.  In Excel usare i metodi della proprietà <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuovo elemento host.  Ogni metodo dispone di diversi overload per specificare in modi diversi il percorso del controllo.  
  
 Quando si aggiunge un controllo Windows Form a un documento in fase di esecuzione, il controllo non viene reso persistente nel documento quando quest'ultimo viene chiuso.  È possibile ricreare il controllo alla prossima apertura del documento.  Per altre informazioni, vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Per altre informazioni sulla generazione di elementi host in progetti di componenti aggiuntivi VSTO, vedere [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Per aggiungere un controllo Windows Form in fase di esecuzione  
  
1.  Usare un metodo che presenta il nome Add\<*classe controllo*\> \(dove *classe controllo* è il nome della classe del controllo Windows Form che si vuole aggiungere, ad esempio <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
    > [!NOTE]  
    >  Nei progetti di componenti aggiuntivi VSTO destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario aggiungere un riferimento all'assembly Microsoft.Office.Tools.Excel.v4.0.Utilities.dll o Microsoft.Office.Tools.Word.v4.0.Utilities.dll prima di poter accedere ai metodi di Add\<*classe del controllo*\>.  
  
     L'esempio di codice seguente illustra come aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> al primo paragrafo del documento attivo mediante un componente aggiuntivo VSTO per Word.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## Vedere anche  
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Procedura: ridimensionare i controlli nelle celle di un foglio di lavoro](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  