---
title: "Procedura dettagliata: programmazione per eventi di un controllo NamedRange"
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
  - "NamedRange (controllo), eventi"
  - "intervalli, programmazione per eventi"
  - "fogli di lavoro, automazione"
  - "fogli di lavoro, modifica di valori di celle"
  - "fogli di lavoro, eventi"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# Procedura dettagliata: programmazione per eventi di un controllo NamedRange
  In questa procedura dettagliata viene illustrato come aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro di Microsoft Office Excel e come programmare in base ai relativi eventi utilizzando gli strumenti di sviluppo di Office in Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In particolare, vengono illustrate le seguenti operazioni:  
  
-   Aggiunta di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> a un foglio di lavoro.  
  
-   Programmazione per eventi del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
-   Test del progetto.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Creazione del progetto  
 In questo passaggio verrà creato un progetto cartella di lavoro di Excel con Visual Studio.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Cartella di lavoro di Excel con il nome My Named Range Events.  Verificare che l'opzione **Crea nuovo documento** sia selezionata.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel verrà aperta nella finestra di progettazione e il progetto My Named Range Events verrà aggiunto a **Esplora soluzioni**.  
  
## Aggiunta di testo e di intervalli denominati al foglio di lavoro  
 Poiché i controlli host sono oggetti estesi di Office, è possibile aggiungerli al documento utilizzando la stessa procedura prevista per gli oggetti nativi.  È possibile aggiungere, ad esempio, un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> di Excel a un foglio di lavoro aprendo il menu **Inserisci**, scegliendo **Nome**, quindi facendo clic su **Definisci**.  È inoltre possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> trascinandolo dalla **Casella degli strumenti** sul foglio di lavoro.  
  
 In questo passaggio verranno aggiunti al foglio di lavoro due controlli Range denominati mediante la **Casella degli strumenti**, quindi verrà aggiunto testo al foglio di lavoro.  
  
#### Per aggiungere un intervallo al foglio di lavoro  
  
1.  Verificare che la cartella di lavoro **Un intervallo denominato Events.xlsx** sia aperta nella finestra di progettazione di Visual Studio, con `Sheet1` visualizzare.  
  
2.  Trascinare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> dalla scheda **Controlli Excel** della Casella degli strumenti alla cella **A1** in `Sheet1`.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo NamedRange**.  
  
3.  Verificare che nella casella di testo modificabile sia visualizzato **$A$1** e che sia selezionata la cella **A1**.  In caso contrario, fare clic sulla cella **A1** per selezionarla.  
  
4.  Fare clic su **OK**.  
  
     La cella **A1** diventerà un intervallo denominato `namedRange1`.  Anche se non esiste alcuna indicazione visibile sul foglio di lavoro, quando viene selezionata la cella **A1** `namedRange1` verrà visualizzato nella casella **Nome**, che si trova sul lato sinistro del foglio di lavoro.  
  
5.  Aggiungere un altro controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> alla cella **B3**.  
  
6.  Verificare che nella casella di testo modificabile sia visualizzato **$B$3** e che sia selezionata la cella **B3**.  In caso contrario, fare clic sulla cella **B3** per selezionarla.  
  
7.  Fare clic su **OK**.  
  
     La cella **B3** diventerà un intervallo denominato `namedRange2`.  
  
#### Per aggiungere testo al foglio di lavoro  
  
1.  Digitare il testo riportato di seguito nella cella **A1**:  
  
     This is an example of a NamedRange control.  
  
2.  Digitare il testo riportato di seguito nella cella **A3** \(a sinistra di `namedRange2`\):  
  
     Events:  
  
 Negli scenari successivi verrà creato codice che consente di inserire testo in `namedRange2` e modificare le proprietà del controllo `namedRange2` in risposta agli eventi <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> e <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> di `namedRange1`.  
  
## Aggiunta di codice in risposta all'evento BeforeDoubleClick  
  
#### Per inserire testo nel controllo NamedRange2 in base all'evento BeforeDoubleClick  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **Sheet1.vb** o **Sheet1.cs** e scegliere **Visualizza codice**.  
  
2.  Aggiungere il codice in modo che il gestore eventi di `namedRange1_BeforeDoubleClick` rispecchi l'esempio seguente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  In C\#, è necessario aggiungere gestori eventi per l'intervallo con nome, come illustrato nell'evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> che segue.  Per informazioni sulla creazione dei gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## Aggiunta di codice in risposta all'evento Change  
  
#### Per inserire testo nel controllo namedRange2 in base all'evento Change  
  
1.  Aggiungere il codice in modo che il gestore eventi `NamedRange1_Change` rispecchi l'esempio seguente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Poiché la selezione con doppio clic di una cella in un intervallo di Excel attiva la modalità di modifica, si verifica un evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> quando la selezione si sposta all'esterno dell'intervallo, anche se non sono state apportate modifiche al testo.  
  
## Aggiunta di codice in risposta all'evento SelectionChange  
  
#### Per inserire testo nel controllo namedRange2 in base all'evento SelectionChange  
  
1.  Aggiungere il codice in modo che il gestore eventi **NamedRange1\_SelectionChange** rispecchi l'esempio seguente:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Poiché la selezione con doppio clic di una cella in un intervallo di Excel comporta lo spostamento della selezione all'interno dell'intervallo, si verifica un evento <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> prima dell'evento <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>.  
  
## Verifica dell'applicazione  
 A questo punto è possibile eseguire il test della cartella di lavoro per verificare che il testo che descrive gli eventi di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> venga inserito in un altro intervallo denominato quando vengono generati gli eventi.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Posizionare il cursore in `namedRange1` e verificare che venga visualizzato il testo relativo all'evento <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> e che nel foglio di lavoro venga inserito un commento.  
  
3.  Fare doppio clic all'interno di `namedRange1` e verificare che il testo relativo agli eventi <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick> venga visualizzato in corsivo e di colore rosso in `namedRange2`.  
  
4.  Fare clic all'esterno di `namedRange1` e verificare se viene generato l'evento Change quando si esce dalla modalità di modifica anche se non è stata apportata alcuna modifica al testo.  
  
5.  Cambiare il testo all'interno di `namedRange1`.  
  
6.  Fare clic all'esterno di `namedRange1` e verificare che il testo relativo all'evento <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> venga visualizzato di colore blu in `namedRange2`.  
  
## Passaggi successivi  
 In questa procedura dettagliata sono state fornite le informazioni di base sulla programmazione per eventi di un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Un'attività successiva potrebbe essere la seguente:  
  
-   Distribuzione del progetto.  Per ulteriori informazioni, vedere [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## Vedere anche  
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Automazione di Excel usando oggetti estesi](../vsto/automating-excel-by-using-extended-objects.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Procedura: aggiungere controlli NamedRange a fogli di lavoro](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  