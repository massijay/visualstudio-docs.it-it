---
title: "Procedura dettagliata: visualizzazione di testo in una casella di testo di un foglio di lavoro tramite un pulsante"
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
  - "testo [sviluppo per Office in Visual Studio], visualizzazione di fogli di lavoro"
  - "testo [sviluppo per Office in Visual Studio], caselle di testo"
  - "caselle di testo, visualizzazione di testo nei fogli di lavoro"
  - "fogli di lavoro, visualizzazione di testo"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Procedura dettagliata: visualizzazione di testo in una casella di testo di un foglio di lavoro tramite un pulsante
  In questa procedura dettagliata sono illustrate nozioni di base sull'utilizzo di pulsanti e caselle di testo nei fogli di lavoro di Microsoft Office Excel e sulla creazione di progetti di Excel tramite gli strumenti di sviluppo di Office in Visual Studio.  Per visualizzare il risultato come un esempio completo, vedere l'esempio relativo ai controlli di Excel in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In particolare, vengono illustrate le seguenti operazioni:  
  
-   Aggiunta di controlli a un foglio di lavoro.  
  
-   Inserimento di dati in una casella di testo quando si fa clic su un pulsante.  
  
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
  
1.  Creare un progetto Cartella di lavoro di Excel denominato My Excel Button.  Verificare che l'opzione **Crea nuovo documento** sia selezionata.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto **My Excel Button** viene aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di controlli al foglio di lavoro  
 Per questa procedura dettagliata è necessario che nel primo foglio di lavoro siano disponibili un pulsante e una casella di testo.  
  
#### Per aggiungere un pulsante e una casella di testo  
  
1.  Verificare che la cartella di lavoro **My Excel Button.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzare.  
  
2.  Dalla scheda **Controlli comuni** della Casella degli strumenti, trascinare un controllo <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> in `Sheet1`.  
  
3.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
4.  Accertarsi che nella casella di riepilogo della finestra **Proprietà** sia visualizzato **TextBox1** e modificare la proprietà **Name** della casella di testo in **displayText**.  
  
5.  Trascinare un controllo **Button** in `Sheet1` e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**insertText**|  
    |**Testo**|Insert Text|  
  
 Scrivere ora il codice da eseguire quando si fa clic sul pulsante.  
  
## Compilazione della casella di testo alla selezione del pulsante  
 Quando l'utente fa clic sul pulsante, **Hello World\!** viene aggiunto alla casella di testo.  
  
#### Per scrivere nella casella di testo quando si fa clic sul pulsante  
  
1.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse su **Sheet1**, quindi scegliere **Visualizza codice** dal menu di scelta rapida.  
  
2.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  In C\#, è necessario aggiungere un gestore eventi all'evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>, come mostrato di seguito.  Per informazioni sulla creazione dei gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## Verifica dell'applicazione  
 È ora possibile testare la cartella di lavoro per assicurarsi che il messaggio **Hello World\!** visualizzato nella casella di testo quando si fa clic sul pulsante.  
  
#### Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic sul pulsante.  
  
3.  Verificare che **Hello World\!** visualizzato nella casella di testo.  
  
## Passaggi successivi  
 In questa procedura dettagliata vengono fornite le informazioni di base sull'utilizzo di pulsanti e caselle di testo nei fogli di lavoro di Excel.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Distribuzione del progetto.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilizzo di caselle di controllo per modificare la formattazione.  Per ulteriori informazioni, vedere [Procedura dettagliata: modifica della formattazione dei fogli di lavoro mediante i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Vedere anche  
 [Procedura: aggiungere controlli Windows Form a documenti di Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  