---
title: "Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante i pulsanti di opzione | Microsoft Docs"
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
  - "controlli [sviluppo per Office in Visual Studio], aggiornamento di fogli di lavoro"
  - "fogli di lavoro, aggiornamento tramite controlli gestiti"
  - "fogli di lavoro, utilizzo di pulsanti di opzione"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Procedura dettagliata: aggiornamento di un grafico in un foglio di lavoro mediante i pulsanti di opzione
  In questa procedura dettagliata vengono fornite le informazioni di base per utilizzare i pulsanti di opzione in un foglio di lavoro Microsoft Office Excel per fornire all'utente un modello per passare rapidamente da un'opzione all'altra.  In questo caso, le opzioni modificano lo stile di un grafico.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Per visualizzare il risultato come un esempio completo, vedere l'esempio relativo ai controlli di Excel in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di un gruppo di pulsanti di opzione a un foglio di lavoro.  
  
-   Modifica dello stile del grafico alla selezione di un'opzione.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Aggiunta di un grafico a un foglio di lavoro  
 È possibile creare un progetto Cartella di lavoro di Excel che personalizzi una cartella di lavoro esistente.  In questa procedura dettagliata verrà aggiunto un grafico a una cartella di lavoro, quindi quest'ultima verrà utilizzata in una nuova soluzione Excel.  L'origine dati di questa procedura dettagliata è un foglio di lavoro denominato **Data for Chart**.  
  
#### Per aggiungere i dati  
  
1.  Aprire Microsoft Excel.  
  
2.  Fare clic con il pulsante destro del mouse sulla scheda **Foglio3** e scegliere **Rinomina** dal menu di scelta rapida.  
  
3.  Rinominare la scheda in Data for Chart.  
  
4.  Aggiungere i dati indicati di seguito a **Data for Chart**. La cella A4 corrisponde all'angolo superiore sinistro e la cella E8 all'angolo inferiore destro.  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |West|500|550|550|600|  
    |East|600|625|675|700|  
    |North|450|470|490|510|  
    |South|800|750|775|790|  
  
 Aggiungere quindi un grafico al primo foglio di lavoro per visualizzare i dati.  
  
#### Per aggiungere un grafico in Excel  
  
1.  Nella scheda **Inserisci**, nel gruppo **Grafici** fare clic **su Colonna**, quindi scegliere **Tutti i tipi di grafico**.  
  
2.  Scegliere **OK** nella finestra di dialogo **Inserisci grafico**.  
  
3.  Nella scheda **Progettazione**, nel gruppo **Dati** fare clic **su Seleziona dati**.  
  
4.  Nella finestra di dialogo **Seleziona origine dati**, fare clic nella casella **intervallo dati** del **Grafico** e cancellare le selezioni predefinite.  
  
5.  Nel foglio **Data for Chart**, selezionare il blocco di celle contenente i numeri, dalla cella A4 nell'angolo superiore sinistro alla cella E8 nell'angolo inferiore destro.  
  
6.  Nella finestra di dialogo **Seleziona origine dati** scegliere **OK**.  
  
7.  Riposizionare il grafico in modo da allineare l'angolo superiore destro alla cella **E2**.  
  
8.  Salvare il file su C e denominarlo **ExcelChart.xlsx**.  
  
9. Uscire da Excel.  
  
## Creazione di un nuovo progetto  
 In questo passaggio verrà creato un progetto Cartella di lavoro di Excel sulla base del foglio di lavoro **ExcelChart**.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Cartella di lavoro di Excel con il nome **My Excel Chart**.  Nella procedura guidata, selezionare **Copia di un documento esistente**.  
  
     Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Fare clicsul pulsante e individuare **Sfoglia** la cartella di lavoro creata precedentemente in questa procedura dettagliata.  
  
3.  Fare clic su **OK**.  
  
     La nuova cartella di lavoro di Excel verrà aperta nella finestra di progettazione e il progetto **My Excel Chart** verrà aggiunto a **Esplora soluzioni**.  
  
## Impostazione delle proprietà del grafico  
 Quando si crea un nuovo progetto Cartella di lavoro di Excel che utilizza una cartella di lavoro esistente, vengono creati automaticamente controlli host per tutti gli intervalli denominati, gli oggetti elenco e i grafici presenti nella cartella di lavoro.  È possibile modificare il nome del controllo <xref:Microsoft.Office.Tools.Excel.Chart> mediante la finestra **Proprietà**.  
  
#### Per modificare il nome del controllo Chart  
  
1.  Selezionare il controllo <xref:Microsoft.Office.Tools.Excel.Chart> nella finestra di progettazione e modificare le proprietà indicate di seguito nella finestra **Proprietà**:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## Aggiunta di controlli  
 Questo foglio di lavoro utilizza i pulsanti di opzione per consentire agli utenti di modificare rapidamente lo stile del grafico.  Tuttavia, i pulsanti di opzione devono escludersi a vicenda, consentendo di selezionare solo un pulsante di opzione alla volta.  Questo comportamento non si verifica per impostazione predefinita quando si aggiungono molti pulsanti di opzione a un foglio di lavoro.  
  
 Per aggiungere questo comportamento, raggruppare i pulsanti di opzione in un controllo utente, scrivere il codice associato e aggiungere il controllo utente al foglio di lavoro.  
  
#### Per aggiungere un controllo utente  
  
1.  Selezionare il progetto **My Excel Chart** in **Esplora soluzioni**.  
  
2.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
3.  Fare clic su **Controllo utente** nella finestra di dialogo **Aggiungi nuovo elemento**, assegnare al controllo il nome **ChartOptions** e fare clic su **Aggiungi**.  
  
#### Per aggiungere pulsanti di opzione al controllo utente  
  
1.  Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** in **Esplora soluzioni**.  
  
2.  Trascinare sul controllo utente un controllo **RadioButton** dalla scheda **Controlli comuni** della **Casella degli strumenti** e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**columnChart**|  
    |**Testo**|Istogramma|  
  
3.  Aggiungere un secondo pulsante di opzione al controllo utente e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**barChart**|  
    |**Testo**|Grafico a barre|  
  
4.  Aggiungere un terzo pulsante di opzione al controllo utente e modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**lineChart**|  
    |**Testo**|Grafico a linee|  
  
5.  Aggiungere un quarto pulsante di opzione al controllo utente e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**areaBlockChart**|  
    |**Testo**|Grafico ad area|  
  
 Scrivere quindi il codice per aggiornare il grafico alla selezione di un pulsante di opzione.  
  
## Modifica dello stile del grafico alla selezione di un pulsante di opzione  
 Ora è possibile aggiungere il codice per modificare lo stile del grafico.  A tale scopo, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare un gestore eventi per l'evento `CheckedChanged` di ciascuno dei pulsanti di opzione.  
  
#### Per creare un evento e una proprietà in un controllo utente  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul controllo utente e scegliere **Visualizza codice**.  
  
2.  Aggiungere il codice alla classe `ChartOptions` per la creazione di un evento `SelectionChanged` e della proprietà `Selection`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### Per gestire l'evento CheckedChanged dei pulsanti di opzione  
  
1.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e generare l'evento.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  In C\# è necessario aggiungere gestori eventi per i pulsanti di opzione.  È possibile aggiungere questo codice al costruttore `ChartOptions`, dopo la chiamata a `InitializeComponent`.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## Aggiunta del controllo utente al foglio di lavoro  
 Durante la compilazione della soluzione, il nuovo controllo utente viene aggiunto automaticamente alla **Casella degli strumenti**.  È possibile trascinare il controllo dalla **Casella degli strumenti** nel foglio di lavoro.  
  
#### Per aggiungere il controllo utente al foglio di lavoro  
  
1.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il controllo utente **ChartOptions** verrà aggiunto alla **Casella degli strumenti**.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1.vb** o su **Sheet1.cs** e scegliere **Progettazione visualizzazioni**.  
  
3.  Trascinare il controllo **ChartOptions** dalla **Casella degli strumenti** sul foglio di lavoro.  
  
     Un nuovo controllo denominato `my_Excel_Chart_ChartOptions1` verrà aggiunto al progetto.  
  
4.  Modificare il nome del controllo in ChartOptions1.  
  
## Modifica del tipo di grafico  
 Per modificare il tipo di grafico, creare un gestore eventi che imposti lo stile in base all'opzione selezionata nel controllo utente.  
  
#### Per modificare il tipo di grafico visualizzato nel foglio di lavoro  
  
1.  Aggiungere il gestore eventi indicato di seguito alla classe `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  In C\#, è necessario aggiungere un gestore eventi per il controllo utente all'evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>, come mostrato di seguito.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## Verifica dell'applicazione  
 È ora possibile provare la cartella di lavoro per assicurarsi che al grafico venga applicato lo stile corretto quando si sceglie un pulsante di opzione.  
  
#### Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare i vari pulsanti di opzione.  
  
3.  Verificare che lo stile del grafico venga modificato in base alla selezione.  
  
## Passaggi successivi  
 In questa procedura dettagliata vengono fornite le informazioni di base sull'utilizzo dei pulsanti di opzione e degli stili dei grafici nei fogli di lavoro.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Distribuzione del progetto.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilizzo di un pulsante per compilare una casella di testo.  Per ulteriori informazioni, vedere [Procedura dettagliata: visualizzazione di testo in una casella di testo di un foglio di lavoro tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Modifica della formattazione di un foglio di lavoro mediante caselle di controllo.  Per ulteriori informazioni, vedere [Procedura dettagliata: modifica della formattazione dei fogli di lavoro mediante i controlli CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Vedere anche  
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)  
  
  