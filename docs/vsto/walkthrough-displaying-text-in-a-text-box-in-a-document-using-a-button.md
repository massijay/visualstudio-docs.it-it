---
title: "Procedura dettagliata: visualizzazione di testo in una casella di testo di un documento tramite un pulsante"
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
  - "caselle di testo, visualizzazione di testo nei documenti"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Procedura dettagliata: visualizzazione di testo in una casella di testo di un documento tramite un pulsante
  Questa procedura dettagliata illustra come usare i pulsanti e le caselle di testo in una personalizzazione a livello di documento per Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di controlli al documento di Word in un progetto a livello di documento in fase di progettazione.  
  
-   Popolamento di una casella di testo quando si fa clic su un pulsante.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Documento di Word con il nome My Word Button.  Nella procedura guidata selezionare **Crea un nuovo documento**.  
  
     Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Il nuovo documento di Word verrà aperto nella finestra di progettazione di Visual Studio e il progetto **My Word Button** verrà aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di controlli al documento di Word  
 I controlli dell'interfaccia utente sono costituiti da un pulsante e da una casella di testo nel documento di Word.  
  
#### Per aggiungere un pulsante e una casella di testo  
  
1.  Verificare che il documento sia aperto nella finestra di progettazione di Visual Studio.  
  
2.  Dalla scheda **Controlli comuni** della **Casella degli strumenti** trascinare un controllo <xref:Microsoft.Office.Tools.Word.Controls.TextBox> nel documento.  
  
    > [!NOTE]  
    >  In Word i controlli vengono rilasciati in linea con il testo per impostazione predefinita.  È possibile modificare le modalità di inserimento di controlli e oggetti forma modificando l'impostazione predefinita nella scheda **Modifica** della finestra di dialogo **Opzioni** in Word.  
  
3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
4.  Cercare **TextBox1** nella casella di riepilogo a discesa della finestra **Proprietà** e modificare la proprietà **Name** della casella di testo in **displayText**.  
  
5.  Trascinare un controllo **Button** nel documento e modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**insertText**|  
    |**Testo**|Inserisci testo|  
  
 È ora possibile scrivere il codice che verrà eseguito quando si fa clic sul pulsante.  
  
## Popolamento della casella di testo quando si fa clic sul pulsante  
 Ogni volta che l'utente fa clic sul pulsante, nella casella di testo viene aggiunto **Hello World\!**.  
  
#### Per scrivere nella casella di testo quando si fa clic sul pulsante  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Aggiungere il codice seguente al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  In C\# è necessario aggiungere un gestore eventi per il pulsante all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Per altre informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## Verifica dell'applicazione  
 È ora possibile testare il documento per verificare che il messaggio **Hello World\!** venga visualizzato nella casella di testo quando si fa clic sul pulsante.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic sul pulsante.  
  
3.  Verificare che nella casella di testo venga visualizzato **Hello World\!**.  
  
## Passaggi successivi  
 Questa procedura dettagliata illustra i concetti di base relativi all'uso di pulsanti e caselle di testo nei documenti di Word.  Ecco alcune possibili attività successive:  
  
-   Uso di una casella combinata per modificare la formattazione.  Per altre informazioni, vedere [Procedura dettagliata: modifica della formattazione dei documenti mediante i controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Uso di pulsanti di opzione per selezionare gli stili del grafico.  Per altre informazioni, vedere [Procedura dettagliata: aggiornamento di un grafico in un documento mediante pulsanti di opzione](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## Vedere anche  
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  