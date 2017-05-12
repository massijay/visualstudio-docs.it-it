---
title: "Procedura dettagliata: modifica della formattazione dei documenti mediante i controlli CheckBox"
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
  - "caselle di controllo, documenti di Word"
  - "controlli [sviluppo per Office in Visual Studio], aggiunta a documenti"
  - "documenti [sviluppo per Office in Visual Studio], controlli caselle di controllo"
  - "documenti [sviluppo per Office in Visual Studio], formattazione"
  - "documenti di Word, modifica della formattazione mediante controlli"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Procedura dettagliata: modifica della formattazione dei documenti mediante i controlli CheckBox
  In questa procedura dettagliata viene illustrato come utilizzare i controlli Windows Form in una personalizzazione a livello di documento per Microsoft Office Word al fine di modificare la formattazione del testo.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di testo e di un controllo al documento contenuto in un progetto a livello di documento in fase di progettazione.  
  
-   Formattazione del testo alla selezione di un'opzione.  
  
 Per visualizzare il risultato come esempio completo, vedere l'esempio relativo ai controlli di Word in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Creazione del progetto  
 Il primo passaggio consiste nella creazione di un progetto Documento di Word.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto documento di Word con il nome My Word Formatting.  Nella procedura guidata, scegliere **Crea un nuovo documento**.  
  
     Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Il nuovo documento di Word viene aperto nella finestra di progettazione di Visual Studio e il progetto **My Word Formatting** viene aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di testo e controlli al documento di Word  
 Per questa procedura dettagliata, aggiungere tre caselle di controllo e il testo in un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al documento di Word.  Le caselle di controllo presenteranno opzioni per formattare il testo.  
  
#### Per aggiungere tre caselle di controllo  
  
1.  Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.  
  
2.  Dalla scheda **Controlli comuni** della **Casella degli strumenti**, trascinare il primo controllo <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> nel documento.  
  
3.  Nella finestra **Proprietà** modificare le proprietà riportate di seguito.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**applyBoldFont**|  
    |**Testo**|Grassetto|  
  
4.  Premere **Invio** per spostare il punto di inserimento al di sotto della prima casella di controllo.  
  
5.  Aggiungere una seconda casella di controllo al documento al di sotto della casella di controllo `ApplyBoldFont` e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**applyItalicFont**|  
    |**Testo**|Italic|  
  
6.  Premere **Invio** per spostare il punto di inserimento al di sotto della seconda casella di controllo.  
  
7.  Aggiungere una terza casella di controllo al documento al di sotto della casella di controllo `ApplyItalicFont` e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**applyUnderlineFont**|  
    |**Testo**|Underline|  
  
#### Per aggiungere il testo e un controllo Bookmark  
  
1.  Spostare il punto di inserimento al di sotto dei controlli della casella di controllo e digitare il seguente testo:  
  
     Fare clic su una casella di controllo per modificare la formattazione di questo testo.  
  
2.  Dalla scheda **Controlli Word** della **Casella degli strumenti**, trascinare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> nel documento.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark**.  
  
3.  Selezionare il testo aggiunto al documento e scegliere **OK**.  
  
     Al testo selezionato nel documento viene aggiunto un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> denominato **Bookmark1**.  
  
4.  Nella finestra **Proprietà** modificare il valore della proprietà **\(Name\)** su **fontText.**  
  
 Creare il codice per la formattazione del testo quando una casella di controllo viene selezionata o deselezionata.  
  
## Formattazione del testo quando una casella di controllo viene selezionata o deselezionata  
 Quando l'utente seleziona un'opzione di formattazione, modificare il formato del testo nel documento.  
  
#### Per modificare la formattazione quando una casella di controllo viene selezionata  
  
1.  Fare clic con il pulsante destro del mouse su `ThisDocument` in **Esplora soluzioni**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Solo per C\#, aggiungere le seguenti costanti alla classe **ThisDocument**.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> della casella di controllo `applyBoldFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> della casella di controllo `applyItalicFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> della casella di controllo `applyUnderlineFont`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  In C\# è necessario aggiungere gestori eventi per le caselle di testo all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## Verifica dell'applicazione  
 È ora possibile sottoporre a test il documento per verificare che il testo sia formattato correttamente quando si seleziona o si deseleziona una casella di controllo.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare o deselezionare una casella di controllo.  
  
3.  Verificare che la formattazione del testo sia corretta.  
  
## Passaggi successivi  
 Nella procedura dettagliata vengono fornite le informazioni di base sull'utilizzo delle caselle di controllo e sulla modifica a livello di codice della formattazione nei documenti di Word.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Utilizzare un pulsante per popolare una casella di testo.  Per ulteriori informazioni, vedere [Procedura dettagliata: visualizzazione di testo in una casella di testo di un documento tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Utilizzo dei pulsanti di opzione per selezionare gli stili del grafico.  Per ulteriori informazioni, vedere [Procedura dettagliata: aggiornamento di un grafico in un documento mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Vedere anche  
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  