---
title: "Procedura dettagliata: modifica della formattazione dei fogli di lavoro mediante i controlli CheckBox | Microsoft Docs"
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
  - "controlli [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro"
  - "fogli di lavoro, modifica della formattazione mediante controlli gestiti"
  - "fogli di lavoro, controlli caselle di controllo"
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Procedura dettagliata: modifica della formattazione dei fogli di lavoro mediante i controlli CheckBox
  In questa procedura dettagliata vengono fornite le informazioni di base sull'utilizzo delle caselle di controllo in un foglio di lavoro di Microsoft Office Excel per la modifica della formattazione.  Vengono utilizzati strumenti di sviluppo di Office in Visual Studio per creare e aggiungere codice al progetto.  Per visualizzare il risultato come un esempio completo, vedere l'esempio relativo ai controlli di Excel in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In particolare, vengono illustrate le seguenti operazioni:  
  
-   Aggiunta di testo e di controlli a un foglio di lavoro.  
  
-   Formattazione del testo quando viene selezionata un'opzione.  
  
-   Test del progetto.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Creazione del progetto  
 In questo passaggio verrà creato un progetto Cartella di lavoro di Excel con Visual Studio.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Cartella di lavoro di Excel denominato Formattazione in Excel.  Verificare che l'opzione **Crea nuovo documento** sia selezionata.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto **Formattazione in Excel** viene aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di testo e di controlli al foglio di lavoro  
 Per questa procedura dettagliata, sono necessari tre controlli <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> e del testo in un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
#### Per aggiungere tre caselle di controllo  
  
1.  Verificare che la cartella di lavoro sia aperta nella finestra di progettazione di Visual Studio e che sia aperto `Sheet1`.  
  
2.  Dalla scheda **Controlli comuni** della **Casella degli strumenti**, trascinare un controllo <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> sulla cella o accanto alla cella **B2** in **Sheet1**.  
  
3.  Scegliere la finestra **Proprietà** dal menu **Visualizza**.  
  
4.  Accertarsi che **Checkbox1** sia riportato nella casella di elenco dei nomi degli oggetti della finestra **Proprietà** e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**applyBoldFont**|  
    |**Testo**|Grassetto|  
  
5.  Trascinare una seconda casella di controllo sulla cella o accanto alla cella **B4** e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**applyItalicFont**|  
    |**Testo**|Italic|  
  
6.  Trascinare una terza casella di controllo sulla cella o accanto alla cella **B6** e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**applyUnderlineFont**|  
    |**Testo**|Underline|  
  
7.  Selezionare tutti e tre i controlli casella di controllo tenendo premuto il tasto CTRL.  
  
8.  Nel gruppo della scheda di formato in Excel, fare clic **Allinea**quindi scegliere **Allinea a sinistra**.  
  
     I tre controlli casella di controllo sono allineati a sinistra, nella posizione del primo controllo selezionato.  
  
     In seguito, il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> verrà trascinato nel foglio di lavoro.  
  
    > [!NOTE]  
    >  È anche possibile aggiungere il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> digitando **textFont** nella casella **Nome**.  
  
#### Per aggiungere testo a un controllo NamedRange  
  
1.  Dalla scheda **Controlli Excel** della casella degli strumenti, trascinare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> nella cella **B9**.  
  
2.  Verificare che nella casella di controllo modificabile sia visualizzato **$B$9** e che la cella **B9** sia selezionata.  In caso contrario, fare clic sulla cella **B9** per selezionarla.  
  
3.  Fare clic su **OK**.  
  
4.  La cella **B9** diventerà un intervallo denominato `NamedRange1`.  
  
     All'interno del foglio di lavoro non sarà presente alcuna indicazione visibile, ma nella casella **Nome** \(al di sotto del foglio di lavoro sul lato sinistro\) verrà visualizzato `NamedRange1` quando la cella **B9** è selezionata.  
  
5.  Accertarsi che **NamedRange1** sia riportato nella casella di elenco dei nomi degli oggetti della finestra **Proprietà** e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**textFont**|  
    |**Value2**|Fare clic su una casella di controllo per modificare la formattazione di questo testo.|  
  
 Scrivere quindi il codice per la formattazione del testo alla selezione di un'opzione.  
  
## Formattazione del testo alla selezione di un'opzione  
 In questa sezione verrà creato il codice per consentire la modifica del formato del testo nel foglio di lavoro quando l'utente seleziona un'opzione di formattazione.  
  
#### Per modificare la formattazione quando una casella di controllo viene selezionata  
  
1.  Fare clic con il pulsante destro del mouse su **Sheet1**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> della casella di controllo `applyBoldFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> della casella di controllo `applyItalicFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> della casella di controllo `applyUnderlineFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  In C\#, è necessario aggiungere gestori eventi per le caselle di controllo all'evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> come mostrato di seguito.  Per informazioni sulla creazione dei gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## Verifica dell'applicazione  
 È ora possibile sottoporre a test la cartella di lavoro per assicurarsi che il testo sia formattato correttamente quando si seleziona o si deseleziona una casella di controllo.  
  
#### Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare o deselezionare una casella di controllo.  
  
3.  Verificare che la formattazione del testo sia corretta.  
  
## Passaggi successivi  
 In questa procedura dettagliata vengono fornite le informazioni di base sull'utilizzo delle caselle di controllo e sulla formattazione di testo nei fogli di lavoro di Excel.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Distribuzione del progetto.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Utilizzo di un pulsante per compilare una casella di testo.  Per ulteriori informazioni, vedere [Procedura dettagliata: visualizzazione di testo in una casella di testo di un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## Vedere anche  
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  