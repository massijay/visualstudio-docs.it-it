---
title: "Procedura dettagliata: raccolta di dati tramite Windows Form | Microsoft Docs"
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
  - "dati [sviluppo per Office in Visual Studio], Windows Form"
  - "Windows Form [sviluppo per Office in Visual Studio], raccolta dei dati"
  - "form [sviluppo per Office in Visual Studio], procedure dettagliate"
  - "fogli di lavoro [sviluppo per Office in Visual Studio], raccolta dei dati"
ms.assetid: 40e87f7f-cfbb-4761-bf1b-d042f45f4f09
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura dettagliata: raccolta di dati tramite Windows Form
  Questa procedura dettagliata spiega come aprire un Windows Form da una personalizzazione a livello di documento per Microsoft Office Excel, raccogliere le informazioni dall'utente e scriverle in una cella del foglio di lavoro.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Nonostante in questa procedura dettagliata venga usato un progetto a livello di documento in modo specifico per Excel, i concetti illustrati sono applicabili ad altri progetti di Office.  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
> [!NOTE]  
>  Nomi o percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Creazione di un nuovo progetto  
 Il primo passaggio consiste nella creazione di un progetto Cartella di lavoro di Excel.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto relativo a una cartella di lavoro di Excel denominato **WinFormInput** e selezionare **Crea un nuovo documento** nella procedura guidata. Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     La nuova cartella di lavoro di Excel viene aperta nella finestra di progettazione di Visual Studio e il progetto **WinFormInput** viene aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di un controllo NamedRange al foglio di lavoro  
  
#### Per aggiungere un intervallo denominato a Sheet1  
  
1.  Selezionare la cella **A1** in `Sheet1`.  
  
2.  Nella casella **Nome** digitare **formInput**.  
  
     La casella **Nome** si trova a sinistra della barra della formula, sopra la colonna **A** del foglio di lavoro.  
  
3.  Premere INVIO.  
  
     Un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> viene aggiunto nella cella **A1**. Sul foglio di lavoro non sono presenti indicazioni visibili, ma nella casella **Nome** \(al di sotto del foglio di lavoro sul lato sinistro\) e nella finestra **Proprietà** viene visualizzato **formInput** quando la cella **A1** viene selezionata.  
  
## Aggiunta di Windows Form al progetto  
 Creare un controllo Windows Form per richiedere informazioni all'utente.  
  
#### Per aggiungere un controllo Windows Form  
  
1.  Selezionare il progetto **WinFormInput** in **Esplora soluzioni**.  
  
2.  Scegliere **Aggiungi Windows Form** dal menu **Progetto**.  
  
3.  Assegnare al modulo il nome **GetInputString.vb** o **GetInputString.cs**, quindi scegliere **Aggiungi**.  
  
     Il nuovo modulo verrà aperto nella finestra di progettazione.  
  
4.  Aggiungere al modulo una classe <xref:System.Windows.Forms.TextBox> e una classe <xref:System.Windows.Forms.Button>.  
  
5.  Scegliere il pulsante, trovare la proprietà **Text** nella finestra **Proprietà**, quindi modificare il testo in **OK**.  
  
 Aggiungere quindi codice a `ThisWorkbook.vb` o `ThisWorkbook.cs` per raccogliere le informazioni relative all'utente.  
  
## Visualizzazione di Windows Form e raccolta di informazioni  
 Creare un'istanza del controllo Windows Form `GetInputString` e visualizzarla, quindi scrivere le informazioni relative all'utente in una cella del foglio di lavoro.  
  
#### Per visualizzare il modulo e raccogliere informazioni  
  
1.  Fare clic con il pulsante destro del mouse su **ThisWorkbook.vb** o **ThisWorkbook.cs** in **Esplora soluzioni** e selezionare **Visualizza codice**.  
  
2.  Nel gestore dell'evento <xref:Microsoft.Office.Tools.Excel.Workbook.Open> di `ThisWorkbook`, aggiungere il codice riportato di seguito per dichiarare una variabile per il modulo `GetInputString` e visualizzare il modulo.  
  
    > [!NOTE]  
    >  In C\# è necessario aggiungere un gestore dell'evento, come mostrato nell'evento <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> che segue. Per informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#1)]  
  
3.  Creare un metodo denominato `WriteStringToCell`, che consente di scrivere testo in un intervallo denominato. Tale metodo viene chiamato dal modulo e l'input utente viene passato al controllo <xref:Microsoft.Office.Tools.Excel.NamedRange>, `formInput`, posizionato sulla cella **A1**.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/ThisWorkbook.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/ThisWorkbook.vb#2)]  
  
 Aggiungere quindi al modulo il codice per la gestione dell'evento Click del pulsante.  
  
## Invio di informazioni al foglio di lavoro  
  
#### Per inviare informazioni al foglio di lavoro  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **GetInputString**, quindi scegliere **Progettazione visualizzazioni**.  
  
2.  Fare doppio clic sul pulsante per aprire il file di codice contenente il gestore dell'evento <xref:System.Windows.Forms.Control.Click> del pulsante aggiunto.  
  
3.  Aggiungere il codice al gestore dell'evento per estrarre l'input dalla casella di testo, inviarlo alla funzione `WriteStringToCell`, quindi chiudere il modulo.  
  
     [!code-csharp[Trin_VstcoreProgrammingCollectingData#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/CS/GetInputString.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingCollectingData#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingCollectingData/VB/GetInputString.vb#3)]  
  
## Test  
 È ora possibile eseguire il progetto. Windows Form viene visualizzato e l'input è presente nel foglio di lavoro.  
  
#### Per testare la cartella di lavoro  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il controllo Windows Form venga visualizzato.  
  
3.  Digitare **Hello World** nella casella di testo e fare clic su **OK**.  
  
4.  Assicurarsi che il testo **Hello World** sia visualizzato nella cella **A1** del foglio di lavoro.  
  
## Passaggi successivi  
 Questa procedura dettagliata fornisce le informazioni di base sulla visualizzazione di un controllo Windows Form e sul passaggio di dati a un foglio di lavoro. Altre attività che è possibile eseguire includono:  
  
-   Usare i controlli Windows Form in una cartella di lavoro di Excel o un documento di Word. Per altre informazioni, vedere [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
-   Modificare l'interfaccia utente di un'applicazione di Microsoft Office da una personalizzazione a livello di documento o un componente aggiuntivo VSTO a livello di applicazione. Per altre informazioni, vedere [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md).  
  
## Vedere anche  
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Programmazione di componenti aggiuntivi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programmazione delle personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)   
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate con Excel](../vsto/walkthroughs-using-excel.md)  
  
  