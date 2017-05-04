---
title: "Procedura dettagliata: Aggiunta di controlli a un documento in fase di esecuzione in un componente aggiuntivo VSTO | Microsoft Docs"
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
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], aggiunta di controlli"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], aggiunta di controlli"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta ai documenti in fase di esecuzione"
  - "documenti [sviluppo per Office in Visual Studio], aggiunta di controlli in fase di esecuzione"
ms.assetid: ab6dff40-9964-468a-938c-a71a3ac23718
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Procedura dettagliata: Aggiunta di controlli a un documento in fase di esecuzione in un componente aggiuntivo VSTO
  È possibile aggiungere controlli a qualsiasi documento di Microsoft Office Word aperto usando un componente aggiuntivo VSTO. Questa procedura dettagliata illustra come usare la barra multifunzione per consentire agli utenti di aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento.  
  
 **Si applica a:** le informazioni contenute in questo argomento si applicano ai progetti di componente aggiuntivo VSTO per Word 2010. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Creazione di un nuovo progetto di componente aggiuntivo VSTO per Word.  
  
-   Creazione di un'interfaccia utente per l'aggiunta di controlli al documento.  
  
-   Aggiunta di controlli ai documenti in fase di esecuzione.  
  
-   Rimozione di controlli dal documento.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Creazione di un nuovo progetto di componente aggiuntivo per Word.  
 Creare innanzitutto un progetto di componente aggiuntivo VSTO per Word.  
  
#### Per creare un nuovo progetto di componente aggiuntivo VSTO per Word.  
  
1.  Creare un progetto di componente aggiuntivo VSTO per Word con il nome **WordDynamicControls**. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Aggiungere un riferimento all'assembly **Microsoft.Office.Tools.Word.v4.0.Utilities.dll**. Tale riferimento è necessario per aggiungere un controllo Windows Form a livello di codice al documento più avanti in questa procedura dettagliata.  
  
## Creazione di un'interfaccia utente per l'aggiunta di controlli a un documento  
 Aggiungere una scheda personalizzata alla barra multifunzione di Word. Gli utenti possono selezionare caselle di controllo nella scheda per aggiungere i controlli a un documento.  
  
#### Per creare un'interfaccia utente per l'aggiunta di controlli a un documento  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione \(finestra di progettazione visiva\)**.  
  
3.  Modificare il nome della nuova barra multifunzione in **MyRibbon** e quindi scegliere **Aggiungi**.  
  
     Nella finestra di progettazione della barra multifunzione viene aperto un file **MyRibbon.cs** o **MyRibbon.vb**, che visualizza una scheda e un gruppo predefiniti.  
  
4.  Nella finestra di progettazione della barra multifunzione fare clic sul gruppo **group1**.  
  
5.  Nella finestra **Proprietà** impostare la proprietà **Etichetta** per **group1** su **Add Controls**.  
  
6.  Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare un controllo **ToggleButton** in **group1**.  
  
7.  Fare clic su **CheckBox1** per selezionarlo.  
  
8.  Nella finestra **Proprietà** modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**addButtonCheckBox**|  
    |**Etichetta**|**Pulsante Aggiungi**|  
  
9. Aggiungere una seconda casella di controllo a **group1** e quindi modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**addRichTextCheckBox**|  
    |**Etichetta**|**Add Rich Text Control**|  
  
10. Nella finestra di progettazione della barra multifunzione fare doppio clic su **Aggiungi pulsante**.  
  
     Il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> della casella di controllo **Aggiungi pulsante** viene aperto nell'editor di codice.  
  
11. Tornare alla finestra di progettazione della barra multifunzione e fare doppio clic su **Add Rich Text Control**.  
  
     Il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> della casella di controllo **Add Rich Text Control** viene aperto nell'editor di codice.  
  
 Più avanti in questa procedura dettagliata si aggiungerà codice a questi gestori eventi per aggiungere e rimuovere i controlli nel documento attivo.  
  
## Aggiunta e rimozione di controlli nel documento attivo  
 Nel codice del componente aggiuntivo VSTO è necessario convertire il documento attivo in un <xref:Microsoft.Office.Tools.Word.Document> *elemento host* prima di poter aggiungere un controllo. Nelle soluzioni Office si possono aggiungere controlli gestiti solo agli elementi host, che agiscono da contenitori per i controlli. Nei progetti di componente aggiuntivo VSTO è possono creare elementi host in fase di esecuzione usando il metodo GetVstoObject.  
  
 Aggiungere metodi alla classe `ThisAddIn` che possono essere chiamati per aggiungere o rimuovere un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> nel documento attivo. Più avanti in questa procedura dettagliata si chiameranno tali metodi dai gestori eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> delle caselle di controllo sulla barra multifunzione.  
  
#### Per aggiungere e rimuovere controlli nel documento attivo  
  
1.  In **Esplora soluzioni** fare doppio clic su ThisAddIn.cs o ThisAddIn.vb per aprire il file nell'editor di codice.  
  
2.  Aggiungere il codice seguente alla classe `ThisAddIn`. Questo codice dichiara gli oggetti <xref:Microsoft.Office.Tools.Word.Controls.Button> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl> che rappresentano i controlli che verranno aggiunti al documento.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `ThisAddIn`. Quando l'utente fa clic sulla casella di controllo **Aggiungi pulsante** sulla barra multifunzione, questo metodo aggiunge un oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> alla selezione corrente nel documento se la casella di controllo è selezionata oppure rimuove l'oggetto <xref:Microsoft.Office.Tools.Word.Controls.Button> se la casella di controllo è deselezionata.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#2)]  
  
4.  Aggiungere il metodo seguente alla classe `ThisAddIn`. Quando l'utente fa clic sulla casella di controllo **Add Rich Text Control** sulla barra multifunzione, questo metodo aggiunge un oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> alla selezione corrente nel documento se la casella di controllo è selezionata oppure rimuove l'oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> se la casella di controllo è deselezionata.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#3)]  
  
## Rimozione del controllo Button quando il documento viene salvato  
 I controlli Windows Form non vengono mantenuti quando il documento viene salvato e quindi chiuso. Nel documento, però, rimane un wrapper ActiveX per ogni controllo e il bordo di questo wrapper è visibile agli utenti finali quando il documento viene riaperto. Esistono diversi modi per pulire i controlli Windows Form creati dinamicamente nei componenti aggiuntivi VSTO. In questa procedura dettagliata, il controllo <xref:Microsoft.Office.Tools.Word.Controls.Button> viene rimosso a livello di codice quando viene salvato il documento.  
  
#### Per rimuovere il controllo Button quando il documento viene salvato  
  
1.  Nel file di codice ThisAddIn.cs o ThisAddIn.vb aggiungere il metodo seguente alla classe `ThisAddIn`. Questo metodo è un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>. Se al documento salvato è associato un elemento host <xref:Microsoft.Office.Tools.Word.Document>, il gestore eventi ottiene l'elemento host e rimuove il controllo <xref:Microsoft.Office.Tools.Word.Controls.Button>, se esistente.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#4)]  
  
2.  In C\# aggiungere il codice seguente al gestore eventi `ThisAddIn_Startup`. Questo codice è necessario in C\# per connettere il gestore eventi `Application_DocumentBeforeSave` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#5)]  
  
## Aggiungere e rimuovere controlli quando l'utente fa clic sulle caselle di controllo sulla barra multifunzione  
 Infine, modificare i gestori eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> delle caselle di controllo aggiunte alla barra multifunzione per aggiungere o rimuovere controlli nel documento.  
  
#### Per aggiungere o rimuovere controlli quando l'utente fa clic sulle caselle di controllo sulla barra multifunzione  
  
1.  Nel file di codice MyRibbon.cs o MyRibbon.vb sostituire i gestori eventi `addButtonCheckBox_Click` e `addRichTextCheckBox_Click` generati con il codice seguente. Questo codice ridefinisce i gestori eventi per chiamare i metodi `ToggleButtonOnDocument` e `ToggleRichTextControlOnDocument` che sono stati aggiunti alla classe `ThisAddIn` più indietro in questa procedura dettagliata.  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/MyRibbon.cs#6)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/MyRibbon.vb#6)]  
  
## Test della soluzione  
 Aggiungere controlli a un documento selezionandoli dalla scheda personalizzata sulla barra multifunzione. Quando si salva il documento, il controllo <xref:Microsoft.Office.Tools.Word.Controls.Button> viene rimosso.  
  
#### Per testare la soluzione.  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Nel documento attivo premere INVIO ripetutamente per aggiungere nuovi paragrafi vuoti nel documento.  
  
3.  Selezionare il primo paragrafo.  
  
4.  Fare clic sulla scheda **Componenti aggiuntivi**.  
  
5.  Nel gruppo **Add Controls** fare clic su **Aggiungi pulsante**.  
  
     Nel primo paragrafo viene visualizzato un pulsante.  
  
6.  Selezionare l'ultimo paragrafo.  
  
7.  Nel gruppo **Add Controls** fare clic su **Add Rich Text Control**.  
  
     All'ultimo paragrafo viene aggiunto un controllo contenuto RTF.  
  
8.  Salvare il documento.  
  
     Il pulsante viene rimosso dal documento.  
  
## Passaggi successivi  
 Per altre informazioni sui controlli nei componenti aggiuntivi VSTO, vedere questi argomenti:  
  
-   Per un esempio che illustra come aggiungere molti altri tipi di controlli a un documento in fase di esecuzione e ricreare i controlli quando il documento viene riaperto, vedere l'esempio di controlli dinamici del componente aggiuntivo per Word all'indirizzo [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
-   Per una procedura dettagliata che illustra come aggiungere controlli a un foglio di lavoro tramite un componente aggiuntivo VSTO per Excel, vedere [Procedura dettagliata: Aggiunta di controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  
  
## Vedere anche  
 [Soluzioni Word](../vsto/word-solutions.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Estensione in fase di esecuzione di documenti di Word e di cartelle di lavoro di Excel in componenti aggiuntivi VSTO](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  