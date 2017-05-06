---
title: "Procedura dettagliata: aggiornamento di un grafico in un documento mediante pulsanti di opzione"
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
  - "controlli [sviluppo per Office in Visual Studio], aggiornamento di documenti"
  - "documenti [sviluppo per Office in Visual Studio], aggiornamento tramite controlli"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Procedura dettagliata: aggiornamento di un grafico in un documento mediante pulsanti di opzione
  Questa procedura dettagliata illustra come usare i pulsanti di opzione in una personalizzazione a livello di documento per Microsoft Office Word, per consentire agli utenti di selezionare stili del grafico nel documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di un grafico al documento di un progetto a livello di documento in fase di progettazione.  
  
-   Raggruppamento dei pulsanti di opzione aggiungendoli a un controllo utente.  
  
-   Modifica dello stile del grafico quando si seleziona un'opzione.  
  
 Per vedere il risultato in un esempio completato, vedere l'esempio relativo ai controlli di Word in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Documento di Word con il nome **My Chart Options**.  Nella procedura guidata selezionare **Crea un nuovo documento**.  Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Il nuovo documento di Word viene aperto nella finestra di progettazione di Visual Studio e il progetto **My Chart Options** viene aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di un grafico al documento  
  
#### Per aggiungere un grafico  
  
1.  Nel documento di Word ospitato nella finestra di progettazione di Visual Studio fare clic sulla scheda **Inserisci** della bara multifunzione.  
  
2.  Nel gruppo **Testo** fare clic sul pulsante a discesa **Inserisci oggetto** e fare clic su **Oggetto**.  
  
     Viene aperta la finestra di dialogo **Oggetto**.  
  
3.  Nell'elenco **Tipo di oggetto** della scheda **Crea nuovo** selezionare **Grafico di Microsoft Graph** e quindi fare clic su **OK**.  
  
     Nel documento viene aggiunto un grafico in corrispondenza del punto di inserimento e compare la finestra **Foglio dati** con alcuni dati predefiniti.  
  
4.  Chiudere la finestra **Foglio dati** per accettare i valori predefiniti del grafico e fare clic all'interno del documento per spostare lo stato attivo al di fuori del grafico.  
  
5.  Fare clic con il pulsante destro del mouse sul grafico e quindi scegliere **Formato oggetto**.  
  
6.  Nella scheda **Layout** della finestra di dialogo **Formato oggetto** selezionare **Incorniciato** e fare clic su **OK**.  
  
## Aggiunta di un controllo utente al progetto  
 I pulsanti di opzione in un documento non si escludono a vicenda per impostazione predefinita.  È possibile farli funzionare correttamente aggiungendoli a un controllo utente e quindi scrivendo il codice per controllare la selezione.  
  
#### Per aggiungere un controllo utente  
  
1.  Selezionare il progetto **My Chart Options** in **Esplora soluzioni**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
3.  Nella finestra di dialogo **Aggiungi nuovo elemento** fare clic su **Controllo utente**, denominare il controllo **ChartOptions** e fare clic su **Aggiungi**.  
  
#### Per aggiungere controlli Windows Form al controllo utente  
  
1.  Se il controllo utente non è visibile nella finestra di progettazione, fare doppio clic su **ChartOptions** in **Esplora soluzioni**.  
  
2.  Nella scheda **Controlli comuni** della **Casella degli strumenti** trascinare il primo controllo **RadioButton** sul secondo controllo e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**columnChart**|  
    |**Testo**|Istogramma|  
  
3.  Aggiungere un secondo **RadioButton** al controllo utente e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**barChart**|  
    |**Testo**|Grafico a barre|  
  
4.  Aggiungere un terzo **RadioButton** al controllo utente e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**lineChart**|  
    |**Testo**|Grafico a linee|  
  
5.  Aggiungere un quarto **RadioButton** al controllo utente e modificare le seguenti proprietà.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**areaBlockChart**|  
    |**Testo**|Grafico ad area|  
  
## Aggiunta di riferimenti  
 Per accedere al grafico dal controllo utente in un documento, è necessario avere un riferimento all'assembly Microsoft.Office.Interop.Graph nel progetto.  
  
#### Per aggiungere un riferimento all'assembly Microsoft.Office.Interop.Graph  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi riferimento**.  
  
     Viene visualizzata la finestra di dialogo **Aggiungi riferimento**.  
  
2.  Nella scheda **.NET** selezionare **Microsoft.Office.Interop.Graph** e fare clic su **OK**.  Selezionare la versione 14.0.0.0 dell'assembly.  
  
## Modifica dello stile del grafico quando si seleziona un pulsante di opzione  
 Per far funzionare i pulsanti correttamente, creare un evento pubblico nel controllo utente, aggiungere una proprietà per impostare il tipo di selezione e creare una routine per l'evento `CheckedChanged` di ogni pulsante di opzione.  
  
#### Per creare un evento e una proprietà in un controllo utente  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul controllo utente e quindi scegliere **Visualizza codice**.  
  
2.  Aggiungere il codice per creare un evento `SelectionChanged` e la proprietà `Selection` nella classe `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### Per gestire l'evento CheckedChange dei pulsanti di opzione  
  
1.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `areaBlockChart` e quindi generare l'evento.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  Impostare il tipo di grafico nel gestore eventi `CheckedChanged` del pulsante di opzione `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  In C\# è necessario aggiungere gestori eventi per i pulsanti di opzione.  È possibile aggiungere questo codice al costruttore `ChartOptions` dopo la chiamata a `InitializeComponent`.  Per informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## Aggiunta del controllo utente al documento  
 Quando si compila la soluzione, il nuovo controllo utente viene aggiunto automaticamente alla **Casella degli strumenti**.  È quindi possibile trascinare il controllo dalla **Casella degli strumenti** al documento.  
  
#### Per aggiungere il controllo utente al documento  
  
1.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Il controllo utente **ChartOptions** viene aggiunto alla **Casella degli strumenti**.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument.vb** o su **ThisDocument.cs** e quindi scegliere **Visualizza finestra di progettazione**.  
  
3.  Trascinare il controllo `ChartOptions` dalla **Casella degli strumenti** nel documento.  
  
     Nella finestra **Proprietà** assegnare il nome `ChartOptions1` al controllo appena aggiunto al documento.  
  
## Modifica del tipo di grafico  
 Creare un gestore eventi per modificare il tipo di grafico in base all'opzione selezionata nel controllo utente.  
  
#### Per modificare il tipo di grafico visualizzato nel documento  
  
1.  Aggiungere il seguente gestore eventi alla classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  In C\# è necessario aggiungere un gestore eventi per il controllo utente all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## Verifica dell'applicazione  
 A questo punto è possibile testare il documento per accertarsi che lo stile del grafico sia aggiornato correttamente quando si seleziona un pulsante di opzione.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare vari pulsanti di opzione.  
  
3.  Verificare che lo stile del grafico sia modificato in base alla selezione.  
  
## Passaggi successivi  
 Ecco alcune possibili attività successive:  
  
-   Usare un pulsante per popolare una casella di testo.  Per altre informazioni, vedere [Procedura dettagliata: visualizzazione di testo in una casella di testo di un documento tramite un pulsante](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Modificare la formattazione selezionando uno stile da una casella combinata.  Per altre informazioni, vedere [Procedura dettagliata: modifica della formattazione dei documenti mediante i controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Vedere anche  
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Limitazioni dei controlli Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  