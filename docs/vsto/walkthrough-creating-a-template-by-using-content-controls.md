---
title: "Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto"
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
  - "compilazione di blocchi [sviluppo per Office in Visual Studio]"
  - "controlli del contenuto [sviluppo per Office in Visual Studio], aggiunta a documenti"
  - "Word [sviluppo per Office in Visual Studio], creazione di documenti"
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto
  Questa procedura dettagliata mostra come creare una personalizzazione a livello di documento che usa i controlli contenuto per creare contenuti strutturati e riutilizzabili in un modello di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word consente di creare una raccolta di parti di documento riutilizzabili, denominate *blocchi predefiniti*.  Questa procedura dettagliata mostra come creare due tabelle come blocchi predefiniti.  Ogni tabella contiene diversi controlli contenuto che possono includere diversi tipi di contenuto, ad esempio testo normale o date.  Una delle tabelle contiene informazioni su un dipendente, mentre un'altra contiene i suggerimenti del cliente.  
  
 Dopo aver creato un documento dal modello, è possibile aggiungere una delle tabelle al documento usando diversi oggetti <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, che visualizzano i blocchi predefiniti disponibili nel modello.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di una tabella contenente i controlli contenuto in un modello di Word in fase di progettazione.  
  
-   Popolamento a livello di codice di un controllo contenuto della casella combinata e di un controllo contenuto dell'elenco a discesa.  
  
-   Impedire agli utenti di modificare una tabella specificata.  
  
-   Aggiunta di tabelle alla raccolta di blocchi predefiniti di un modello.  
  
-   Creazione di un controllo contenuto che visualizza i blocchi predefiniti disponibili nel modello.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Creazione di un nuovo progetto di modello di Word  
 Creare un modello di Word in modo che gli utenti possano creare facilmente le proprie copie.  
  
#### Per creare un nuovo progetto di modello di Word  
  
1.  Creare un progetto di modello di Word denominato MyBuildingBlockTemplate.  Nella procedura guidata creare un nuovo documento nella soluzione.  Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il nuovo modello di Word nella finestra di progettazione e aggiunge il progetto **MyBuildingBlockTemplate** a **Esplora soluzioni**.  
  
## Creazione della tabella dei dipendenti  
 Creare una tabella che contiene quattro tipi differenti di controlli contenuto in cui un utente può immettere le informazioni su un dipendente.  
  
#### Per creare la tabella dei dipendenti  
  
1.  Nel modello di Word ospitato nella finestra di progettazione [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], nella barra multifunzione, fare clic sulla scheda **Inserisci**.  
  
2.  Scegliere **Tabella** nel gruppo **Tabelle** e inserire una tabella con 2 colonne e 4 righe.  
  
3.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |Nome dipendente|  
    |Data assunzione|  
    |Titolo|  
    |Immagine|  
  
4.  Fare clic nella prima cella della seconda colonna \(accanto a **Nome dipendente**\).  
  
5.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non è visibile, è necessario prima di tutto visualizzarla.  Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Nel gruppo **Controlli** scegliere il pulsante **Testo** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> alla prima cella.  
  
7.  Fare clic nella seconda cella della seconda colonna \(accanto a **Data assunzione**\).  
  
8.  Nel gruppo **Controlli** scegliere il pulsante **Selezione data** ![DatePickerContentControl](../vsto/media/datepicker.png "DatePickerContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.  
  
9. Fare clic sulla terza cella della seconda colonna \(accanto a **Titolo**\).  
  
10. Nel gruppo **Controlli** scegliere il pulsante **Casella combinata** ![ComboBoxContentControl](../vsto/media/combobox.png "ComboBoxContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> alla terza cella.  
  
11. Fare clic sull'ultima cella della seconda colonna \(accanto a **Immagine**\).  
  
12. Nel gruppo **Controlli** scegliere il pulsante **Controllo contenuto immagine** ![PictureContentControl](../vsto/media/pictcontentcontrol.png "PictureContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.PictureContentControl> all'ultima cella.  
  
## Creazione della tabella dei suggerimenti dei clienti  
 Creare una tabella che contiene tre tipi differenti di controlli contenuto in cui un utente può immettere le informazioni relative ai suggerimenti dei clienti.  
  
#### Per creare una tabella dei suggerimenti dei clienti  
  
1.  Nel modello di Word fare clic sulla riga dopo la tabella dei dipendenti aggiunta in precedenza, quindi premere INVIO per aggiungere un nuovo paragrafo.  
  
2.  Fare clic sulla scheda **Inserisci** della barra multifunzione.  
  
3.  Scegliere **Tabella** nel gruppo **Tabelle** e inserire una tabella con 2 colonne e 3 righe.  
  
4.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |Nome cliente|  
    |Valutazione soddisfazione|  
    |Commenti|  
  
5.  Fare clic nella prima cella della seconda colonna \(accanto a **Nome cliente**\).  
  
6.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore**.  
  
7.  Nel gruppo **Controlli** scegliere il pulsante **Testo** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> alla prima cella.  
  
8.  Fare clic nella seconda cella della seconda colonna \(accanto a **Valutazione soddisfazione**\).  
  
9. Nel gruppo **Controlli** scegliere il pulsante **Elenco a discesa** ![DropDownListContentControl](../vsto/media/dropdownlist.png "DropDownListContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> alla seconda cella.  
  
10. Fare clic nell'ultima cella della seconda colonna \(accanto a **Commenti**\).  
  
11. Nel gruppo **Controlli** scegliere il pulsante **Formato RTF** ![RichTextContentControl](../vsto/media/richtextcontrol.png "RichTextContentControl") per aggiungere <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'ultima cella.  
  
## Popolamento a livello di codice della casella combinata e dell'elenco a discesa  
 È possibile inizializzare i controlli contenuto in fase di progettazione usando la finestra **Proprietà** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  È anche possibile inizializzarli in fase di esecuzione. In questo caso gli stati iniziali possono essere impostati dinamicamente.  Per questa procedura dettagliata, usare il codice per popolare le voci in <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in fase di esecuzione in modo da visualizzare il funzionamento degli oggetti.  
  
#### Per modificare l'interfaccia utente dei controlli contenuto a livello di codice  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse su **ThisDocument.cs** o **ThisDocument.vb**, quindi scegliere **Visualizza codice**.  
  
2.  Aggiungere il codice seguente alla classe `ThisDocument`.  Questo codice dichiara diversi oggetti che verranno usati più avanti nella procedura dettagliata.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`.  Questo codice aggiunge voci a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> e <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> nelle tabelle e imposta il testo del segnaposto visualizzato in ciascun controllo prima che l'utente apporti modifiche.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#2)]  
  
## Impedire agli utenti di modificare la tabella dei dipendenti  
 Usare l'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza per proteggere la tabella dei dipendenti.  Dopo aver protetto la tabella, gli utenti possono comunque modificarne i controlli contenuto.  Tuttavia, non possono modificare il testo nella prima colonna o modificare la tabella in altri modi, ad esempio aggiungendo o rimuovendo righe e colonne.  Per altre informazioni su come usare <xref:Microsoft.Office.Tools.Word.GroupContentControl> per proteggere una parte di un documento, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
#### Per impedire agli utenti di modificare la tabella dei dipendenti  
  
1.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente.  Questo codice impedisce agli utenti di modificare la tabella dei dipendenti inserendo la tabella all'interno dell'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> dichiarato in precedenza.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#3)]  
  
## Aggiunta di tabella alla raccolta di blocchi predefiniti  
 Aggiungere le tabelle a una raccolta di blocchi predefiniti del documento nel modello in modo che gli utenti possano inserire le tabelle create all'interno di quel documento.  Per altre informazioni sui blocchi predefiniti del documento, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
#### Per aggiungere le tabelle ai blocchi predefiniti nel modello  
  
1.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente.  Questo codice aggiunge nuovi blocchi predefiniti che contengono le tabelle alla raccolta Microsoft.Office.Interop.Word.BuildingBlockEntries che contiene tutti i blocchi predefiniti riutilizzabili nel modello.  I nuovi blocchi predefiniti vengono definiti in una nuova categoria denominata **Informazioni su dipendenti e clienti** e gli viene assegnato il tipo di blocco predefinito Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#4)]  
  
2.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente.  Questo codice elimina le tabelle dal modello.  Le tabelle non sono più necessarie perché sono state aggiunte alla raccolta di blocchi predefiniti riutilizzabili nel modello.  Il codice passa innanzitutto il documento in modalità progettazione in modo che la tabella dei dipendenti protetta possa essere eliminata.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#5)]  
  
## Creazione di un controllo contenuto che visualizza i blocchi predefiniti  
 Creare un controllo contenuto che fornisca l'accesso ai blocchi predefiniti \(ossia, alle tabelle\) create in precedenza.  Gli utenti possono selezionare questo controllo per aggiungere le tabelle al documento.  
  
#### Per creare un controllo contenuto che visualizza i blocchi predefiniti  
  
1.  Aggiungere il codice seguente al metodo `ThisDocument_Startup` della classe `ThisDocument` dopo il codice aggiunto nel passaggio precedente.  Il codice inizializza l'oggetto <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> dichiarato in precedenza.  <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> visualizza tutti i blocchi predefiniti definiti nella categoria **Informazioni su dipendenti e clienti** e che hanno il tipo di blocco predefinito Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#6)]  
  
## Test del progetto  
 Gli utenti possono fare clic sui controlli della raccolta di blocchi predefiniti nel documento per inserire la tabella dei dipendenti o la tabella dei suggerimenti dei clienti.  Gli utenti possono digitare o selezionare le risposte nei controlli contenuto in entrambe le tabelle.  Gli utenti possono modificare altre parti della tabella dei suggerimenti dei clienti, ma non devono poter modificare altre parti della tabella dei dipendenti.  
  
#### Per testare la tabella dei dipendenti  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic su **Scegli il primo blocco predefinito** per visualizzare il primo controllo contenuto della raccolta di blocchi predefiniti.  
  
3.  Fare clic sulla freccia a discesa accanto all'intestazione **Raccolta personalizzata 1** nel controllo e selezionare **Tabella dei dipendenti**.  
  
4.  Fare clic nella cella a destra della cella Nome dipendente e digitare un nome.  
  
     Verificare di poter aggiungere solo testo alla cella.  <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> consente agli utenti di aggiungere solo testo, non altri tipi di contenuto, ad esempio grafici o tabelle.  
  
5.  Fare clic nella cella a destra della cella Data assunzione e selezionare una data nella selezione data.  
  
6.  Fare clic nella cella a destra della cella Titolo e selezionare uno dei titoli professionali nella casella combinata.  
  
     Facoltativamente, digitare il nome di un titolo professionale non presente nell'elenco.  <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>, infatti, consente agli utenti di effettuare una selezione da un elenco di voci oppure di digitare le voci personalizzate.  
  
7.  Fare clic sull'icona nella cella a destra della cella Immagine e cercare un'immagine per visualizzarla.  
  
8.  Provare ad aggiungere e quindi a eliminare le righe o le colonne dalla tabella.  Verificare che non sia possibile modificare la tabella.  <xref:Microsoft.Office.Tools.Word.GroupContentControl> impedisce di apportare modifiche.  
  
#### Per testare la tabella dei suggerimenti dei clienti  
  
1.  Fare clic su **Scegli il secondo blocco predefinito** per visualizzare il secondo controllo contenuto della raccolta di blocchi predefiniti.  
  
2.  Fare clic sulla freccia a discesa accanto all'intestazione **Raccolta personalizzata 1** nel controllo e selezionare **Tabella dei clienti**.  
  
3.  Fare clic nella cella a destra della cella Nome cliente e digitare un nome.  
  
4.  Fare clic nella cella a destra della cella Valutazione soddisfazione e selezionare una delle opzioni disponibili.  
  
     Verificare che non sia possibile digitare una voce personalizzata.  <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> consente di selezionare solo da un elenco di voci.  
  
5.  Fare clic nella cella a destra della cella Commenti e digitare i commenti.  
  
     Facoltativamente, aggiungere alcuni contenuti diversi dal testo, ad esempio un grafico o una tabella incorporata.  <xref:Microsoft.Office.Tools.Word.RichTextContentControl> consente, infatti, agli utenti di aggiungere contenuti diversi dal testo.  
  
6.  Verificare di poter aggiungere e quindi eliminare le righe o le colonne dalla tabella.  Ciò è possibile perché la tabella non è stata protetta inserendola in <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Chiudere il modello.  
  
## Passaggi successivi  
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere l'argomento seguente:  
  
-   Associare controlli contenuto a parti del codice XML, chiamate anche parti XML personalizzate, incorporate in un documento.  Per altre informazioni, vedere [Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controlli del contenuto](../vsto/content-controls.md)   
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: proteggere parti di documenti mediante i controlli del contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  