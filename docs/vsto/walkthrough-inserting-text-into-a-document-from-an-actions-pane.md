---
title: "Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni"
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
  - "riquadri azioni [sviluppo per Office in Visual Studio], aggiunta di controlli"
  - "riquadri azioni [sviluppo per Office in Visual Studio], creazione in Word"
  - "Smart document [sviluppo per Office in Visual Studio], aggiunta di controlli"
  - "Smart document [sviluppo per Office in Visual Studio], creazione in Word"
ms.assetid: fd14c896-5737-4a20-94f7-6064b67112c5
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Procedura dettagliata: inserimento di testo in un documento da un riquadro azioni
  In questa procedura dettagliata verrà illustrata la creazione di un riquadro azioni in un documento di Microsoft Office Word.  Il riquadro azioni contiene due controlli che raccolgono l'input e inviano il testo al documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Progettazione di un'interfaccia utilizzando i controlli Windows Form in un controllo del riquadro azioni.  
  
-   Visualizzazione del riquadro azioni all'apertura dell'applicazione.  
  
> [!NOTE]  
>  Il computer potrebbe mostrare nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Creazione del progetto  
 Il primo passaggio consiste nella creazione di un progetto Documento di Word.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto Documento di Word denominato My Basic Actions Pane.  Nella procedura guidata, scegliere **Crea un nuovo documento**.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Il nuovo documento di Word verrà aperto nella finestra di progettazione e il progetto **My Basic Actions Pane** verrà aggiunto in **Esplora soluzioni**.  
  
## Aggiunta di testo e segnalibri al documento  
 Il riquadro azioni inserirà il testo nei segnalibri del documento.  Per progettare il documento, digitare del testo per creare un modulo di base.  
  
#### Per aggiungere testo al documento  
  
1.  Digitare nel documento di Word il testo riportato di seguito:  
  
     March 21, 2008  
  
     Nome  
  
     Address  
  
     Questo è un esempio di un riquadro azioni di base in Word.  
  
 È possibile aggiungere un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al documento trascinandolo dalla **Casella degli strumenti** in Visual Studio o utilizzando la finestra di dialogo **Segnalibro** in Word.  
  
#### Per aggiungere un controllo Bookmark al documento  
  
1.  Trascinare sul documento un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> dalla scheda **Controlli Word** della **Casella degli strumenti**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark**.  
  
2.  Selezionare la parola **Name**, senza selezionare il segno di paragrafo, quindi scegliere **OK**.  
  
    > [!NOTE]  
    >  Il segno di paragrafo deve trovarsi all'esterno del segnalibro.  Se nel documento non sono visibili segni di paragrafo, scegliere **Strumenti di Microsoft Office Word** dal menu **Strumenti** quindi scegliere **Opzioni**.  Fare clic sulla scheda **Visualizza** e selezionare la casella di controllo **Segni di paragrafo** nella sezione **Segni di formattazione** della finestra di dialogo **Opzioni**.  
  
3.  Nella finestra **Proprietà** impostare la proprietà **Name** di **Bookmark1** su **showName**.  
  
4.  Selezionare la parola **Address**, senza selezionare il segno di paragrafo.  
  
5.  Nella scheda **Inserisci** della barra multifunzione fare clic su **Segnalibro** nel gruppo **Collegamenti**.  
  
6.  Nella finestra di dialogo **Segnalibro**, digitare **showAddress** nella casella **Nome segnalibro** e fare clic su **Aggiungi**.  
  
## Aggiunta di controlli al riquadro delle azioni  
 Per progettare l'interfaccia del riquadro azioni, aggiungere un controllo riquadro azioni al progetto, quindi aggiungere i controlli Windows Form al controllo riquadro azioni.  
  
#### Per aggiungere un controllo riquadro azioni  
  
1.  Selezionare il progetto **My Basic Actions Pane** in **Esplora soluzioni**.  
  
2.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
3.  Fare clic su **Controllo riquadro azioni** nella finestra di dialogo **Aggiungi nuovo elemento**, assegnare al controllo il nome **InsertTextControl** e fare clic su **Aggiungi**.  
  
#### Per aggiungere controlli Windows Form al controllo riquadro azioni  
  
1.  Se il controllo riquadro azioni non è visibile nella finestra di progettazione, fare doppio clic su **InsertTextControl**.  
  
2.  Trascinare un controllo **Label** sul controllo riquadro azioni dalla scheda **Controlli comuni** della **Casella degli strumenti**.  
  
3.  Modificare la proprietà **Text** del controllo Label in **Name**.  
  
4.  Aggiungere un controllo **Textbox** al controllo riquadro azioni e modificare le proprietà riportate di seguito.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**getName**|  
    |**Dimensione**|**130, 20**|  
  
5.  Aggiungere un secondo controllo **Label** al controllo riquadro azioni e modificare la proprietà **Text** in **Address**.  
  
6.  Aggiungere un secondo controllo **Textbox** al controllo riquadro azioni e modificare le proprietà riportate di seguito.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**getAddress**|  
    |**Accepts Return**|**True**|  
    |**Multiline**|**True**|  
    |**Dimensione**|**130, 40**|  
  
7.  Aggiungere un controllo **Button** al controllo riquadro azioni e modificare le proprietà riportate di seguito.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|**addText**|  
    |**Testo**|**Insert**|  
  
## Aggiunta di codice per l'inserimento di testo nel documento  
 Nel riquadro azioni, creare il codice per inserire il testo delle caselle di testo nei controlli <xref:Microsoft.Office.Tools.Word.Bookmark> appropriati del documento.  È possibile utilizzare la classe `Globals` per accedere ai controlli nel documento dai controlli nel riquadro azioni.  Per ulteriori informazioni, vedere [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
#### Per inserire testo dal riquadro azioni in un segnalibro del documento  
  
1.  Aggiungere il codice riportato di seguito al gestore eventi <xref:System.Windows.Forms.Control.Click> del pulsante **addText**.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/InsertTextControl.vb#8)]  
  
2.  Per C\#, è necessario aggiungere un gestore eventi per il clic su un pulsante.  È possibile inserire il codice nel costruttore `InsertTextControl` dopo la chiamata a `IntializeComponent`.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/InsertTextControl.cs#9)]  
  
## Aggiunta di codice per mostrare il riquadro delle azioni  
 Per visualizzare il riquadro azioni, aggiungere il controllo creato alla raccolta di controlli.  
  
#### Per mostrare il riquadro delle azioni  
  
1.  Creare una nuova istanza del controllo riquadro azioni nella classe `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#10)]  
  
2.  Aggiungere al gestore eventi <xref:Microsoft.Office.Tools.Word.Document.Startup> di `ThisDocument` il seguente codice:  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#11)]  
  
## Verifica dell'applicazione  
 Eseguire il test del documento per verificare che il riquadro azioni venga visualizzato all'apertura del documento e che il testo digitato nelle caselle di testo venga inserito nei segnalibri quando si fa clic sul pulsante.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che il riquadro delle azioni sia visibile.  
  
3.  Digitare il nome e l'indirizzo nelle caselle di testo del riquadro delle azioni e fare clic su **Inserisci**.  
  
## Passaggi successivi  
 Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Creazione di un riquadro delle azioni in Excel.  Per ulteriori informazioni, vedere [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/it-it/62abfce6-e44f-419d-85d8-26bf59f33872).  
  
-   Associazione di dati a controlli in un riquadro azioni.  Per ulteriori informazioni, vedere [Procedura dettagliata: associazione di dati a controlli in un riquadro delle azioni di Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## Vedere anche  
 [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md)   
 [Procedura: aggiungere un riquadro ai documenti Word o alle cartelle di lavoro di Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [How to: Add an Actions Pane to Excel Workbooks](http://msdn.microsoft.com/it-it/62abfce6-e44f-419d-85d8-26bf59f33872)   
 [Procedura: gestire il layout di controllo dei riquadri delle azioni](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Controllo Bookmark](../vsto/bookmark-control.md)  
  
  