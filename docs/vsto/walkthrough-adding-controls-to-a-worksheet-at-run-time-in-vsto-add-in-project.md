---
title: "Procedura dettagliata: Aggiunta di controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO | Microsoft Docs"
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
  - "controlli [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro in fase di esecuzione"
  - "fogli di lavoro, aggiunta di controlli in fase di esecuzione"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura dettagliata: Aggiunta di controlli a un foglio di lavoro in fase di esecuzione in un progetto di componente aggiuntivo VSTO
  È possibile aggiungere controlli a qualsiasi foglio di lavoro aperto mediante un componente aggiuntivo VSTO per Excel.  Questa procedura dettagliata illustra come usare la barra multifunzione per consentire agli utenti l'aggiunta di oggetti <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> a un foglio di lavoro.  Per informazioni vedere [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Si applica a:** le informazioni contenute in questo argomento sono valide per i progetti di componenti aggiuntivi VSTO per Excel.  Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'interfaccia utente per l'aggiunta di controlli al foglio di lavoro.  
  
-   Aggiunta di controlli al foglio di lavoro.  
  
-   Rimozione di controlli dal foglio di lavoro.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## Creazione di un nuovo progetto di componente aggiuntivo VSTO per Excel  
 Creare innanzitutto un progetto di componente aggiuntivo VSTO per Excel.  
  
#### Per creare un nuovo progetto di componente aggiuntivo VSTO per Excel  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto di componente aggiuntivo VSTO per Excel con il nome ExcelDynamicControls.  Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Aggiungere un riferimento all'assembly **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll**.  Tale riferimento è necessario per aggiungere a livello di codice un controllo Windows Form al foglio di lavoro più avanti in questa procedura dettagliata.  
  
## Creazione di un'interfaccia utente per l'aggiunta di controlli a un foglio di lavoro  
 Aggiungere una scheda personalizzata alla barra multifunzione di Excel.  Gli utenti possono selezionare caselle di controllo nella scheda per aggiungere i controlli a un foglio di lavoro.  
  
#### Per creare un'interfaccia utente per l'aggiunta di controlli a un foglio di lavoro  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **Barra multifunzione \(Progettazione grafica\)** e quindi scegliere **Aggiungi**.  
  
     Nella finestra di progettazione della barra multifunzione viene aperto un file denominato **Ribbon1.cs** o **Ribbon1.vb**, che visualizza una scheda e un gruppo predefiniti.  
  
3.  Dalla scheda **Controlli barra multifunzione di Office** della **Casella degli strumenti** trascinare un controllo CheckBox in **group1**.  
  
4.  Fare clic su **CheckBox1** per selezionarlo.  
  
5.  Nella finestra **Proprietà** modificare le seguenti proprietà:  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|Pulsante|  
    |**Etichetta**|Pulsante|  
  
6.  Aggiungere una seconda casella di controllo a **group1** e quindi modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|NamedRange|  
    |**Etichetta**|NamedRange|  
  
7.  Aggiungere una terza casella di controllo a **group1** e quindi modificare le proprietà seguenti.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**Nome**|ListObject|  
    |**Etichetta**|ListObject|  
  
## Aggiunta di controlli al foglio di lavoro  
 I controlli gestiti possono essere aggiunti solo a elementi host che fungono da contenitori.  Poiché i progetti di componenti aggiuntivi VSTO vengono usati con qualsiasi cartella di lavoro aperta, il componente aggiuntivo VSTO converte il foglio di lavoro in un elemento host oppure ottiene un elemento host esistente, prima di aggiungere il controllo.  Aggiungere codice ai gestori di eventi Click di ciascun controllo per generare un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> basato su un foglio di lavoro aperto.  Aggiungere quindi un oggetto <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> e <xref:Microsoft.Office.Tools.Excel.ListObject> alla selezione corrente nel foglio di lavoro.  
  
#### Per aggiungere controlli a un foglio di lavoro  
  
1.  Nella finestra di progettazione della barra multifunzione, fare doppio clic su **Pulsante**.  
  
     Il gestore eventi <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> della casella di controllo **Pulsante** viene aperto nell'editor di codice.  
  
2.  Sostituire il gestore eventi `Button_Click` con il codice seguente.  
  
     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi viene aggiunto un controllo <xref:Microsoft.Office.Tools.Excel.Controls.Button> per la cella attualmente selezionata.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  In **Esplora soluzioni** selezionare Ribbon1.cs o Ribbon1.vb.  
  
4.  Scegliere **Finestra di progettazione** dal menu **Visualizza**.  
  
5.  Nella finestra di progettazione della barra multifunzione fare doppio clic su **NamedRange**.  
  
6.  Sostituire il gestore eventi `NamedRange_Click` con il codice seguente.  
  
     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi definisce un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> per la cella o le celle attualmente selezionate.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  Nella finestra di progettazione della barra multifunzione fare doppio clic su **ListObject**.  
  
8.  Sostituire il gestore eventi `ListObject_Click` con il codice seguente.  
  
     Questo codice usa il metodo `GetVstoObject` per ottenere un elemento host che rappresenta il primo foglio di lavoro nella cartella di lavoro e quindi definisce un oggetto <xref:Microsoft.Office.Tools.Excel.ListObject> per la cella o le celle attualmente selezionate.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. Aggiungere le seguenti istruzioni alla parte iniziale del file di codice della barra multifunzione.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## Rimozione di controlli dal foglio di lavoro  
 I controlli non sono resi permanenti quando il foglio di lavoro viene salvato e chiuso.  È necessario rimuovere a livello di codice tutti i controlli Windows Form generati prima che il foglio di lavoro venga salvato, altrimenti quando la cartella di lavoro viene nuovamente aperta, verrà visualizzata solo una struttura del controllo.  Aggiungere all'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> il codice per rimuovere i controlli Windows Form dalla raccolta di controlli dell'elemento host generato.  Per altre informazioni, vedere [Persistenza dei controlli dinamici nei documenti di Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### Per rimuovere i controlli dal foglio di lavoro  
  
1.  In **Esplora soluzioni** selezionare ThisAddIn.cs o ThisAddIn.vb.  
  
2.  Scegliere **Codice** dal menu **Visualizza**.  
  
3.  Aggiungere il metodo seguente alla classe ThisAddIn.  In questo codice si ottiene il primo foglio di lavoro della cartella di lavoro e viene usato il metodo `HasVstoObject` per controllare se il foglio di lavoro dispone di un oggetto foglio di lavoro generato.  Se l'oggetto foglio di lavoro generato dispone di controlli, il codice ottiene tale oggetto ed esegue l'iterazione della raccolta di controlli rimuovendo questi ultimi.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  In C\# è necessario creare un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  Questo codice può essere inserito nel metodo `ThisAddIn_Startup`.  Per altre informazioni sulla creazione di questi gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  Sostituire il metodo `ThisAddIn_Startup` con il codice seguente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## Test della soluzione  
 Aggiungere controlli a un foglio di lavoro selezionandoli da una scheda personalizzata sulla barra multifunzione.  Quando si salva il foglio di lavoro, questi controlli vengono rimossi.  
  
#### Per testare la soluzione.  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Selezionare una qualsiasi cella di Sheet1.  
  
3.  Fare clic sulla scheda **Componenti aggiuntivi**.  
  
4.  Nel gruppo **group1** scegliere **Pulsante**.  
  
     Nella cella selezionata viene visualizzato un pulsante.  
  
5.  Selezionare una cella diversa di Sheet1.  
  
6.  Nel gruppo **group1** scegliere **NamedRange**.  
  
     Per la cella selezionata viene definito un intervallo denominato.  
  
7.  Selezionare una serie di celle di Sheet1.  
  
8.  Nel gruppo **group1** scegliere **ListObject**.  
  
     Per le celle selezionate viene aggiunto un oggetto elenco.  
  
9. Salvare il foglio di lavoro.  
  
     I controlli aggiunti a Sheet1 non vengono più visualizzati.  
  
## Passaggi successivi  
 In questo argomento vengono fornite altre informazioni sui controlli nei progetti di componenti aggiuntivi VSTO per Excel:  
  
-   Per altre informazioni sul salvataggio dei controlli in un foglio di lavoro, vedere l'esempio relativo ai controlli dinamici nel componente aggiuntivo VSTO di Excel in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Vedere anche  
 [Soluzioni Excel](../vsto/excel-solutions.md)   
 [Panoramica dei controlli Windows Form nei documenti di Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Controllo ListObject](../vsto/listobject-control.md)  
  
  