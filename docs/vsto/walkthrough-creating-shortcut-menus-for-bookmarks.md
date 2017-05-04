---
title: "Procedura dettagliata: creazione di menu di scelta rapida per segnalibri | Microsoft Docs"
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
  - "Bookmark (controllo), eventi"
  - "menu di scelta rapida, Word"
  - "menu, creazione in applicazioni Office"
  - "menu di scelta rapida, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura dettagliata: creazione di menu di scelta rapida per segnalibri
  In questa procedura dettagliata viene illustrato come creare menu di scelta rapida per i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> in una personalizzazione a livello di documento per Word.  Quando un utente fa clic con il pulsante destro del mouse sul testo di un segnalibro, il sistema visualizza un menu di scelta rapida contenente alcune opzioni di formattazione del testo.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   [Creazione del progetto](#BKMK_CreateProject).  
  
-   [Aggiunta di testo e segnalibri al documento](#BKMK_addtextandbookmarks).  
  
-   [Aggiunta di controlli a un menu di scelta rapida](#BKMK_AddCmndsShortMenu).  
  
-   [Formattare il testo in un segnalibro](#BKMK_formattextbkmk).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Creazione del progetto  
 Il primo passaggio consiste nel creare un progetto Documento di Word in Visual Studio.  
  
#### Per creare un nuovo progetto  
  
-   Creare un progetto Documento di Word denominato My Bookmark Shortcut Menu.  Nella procedura guidata, scegliere **Crea un nuovo documento**.  Per ulteriori informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Il nuovo documento di Word verrà aperto nella finestra di progettazione e il progetto **My Bookmark Shortcut Menu** verrà aggiunto in **Esplora soluzioni**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Aggiunta di testo e segnalibri al documento  
 Aggiungere testo al documento e quindi aggiungere due segnalibri sovrapposti.  
  
#### Per aggiungere testo al documento  
  
-   Nel documento visualizzato nella finestra di progettazione del progetto, digitare il seguente testo.  
  
     This is an example of creating a shortcut menu when you right\-click the text in a bookmark.  
  
#### Per aggiungere un controllo Bookmark al documento  
  
1.  In **Casella degli strumenti**, dalla scheda **Controlli Word**, trascinare un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> al documento.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi controllo Bookmark**.  
  
2.  Selezionare le parole "per creare un menu di scelta rapida facendo clic con il pulsante destro del mouse sul testo" e quindi fare clic su **OK**.  
  
     `bookmark1` verrà aggiunto al documento.  
  
3.  Aggiungere un altro controllo <xref:Microsoft.Office.Tools.Word.Bookmark> alle parole "fare clic con il pulsante destro del mouse sul testo in un segnalibro".  
  
     `bookmark2` verrà aggiunto al documento.  
  
    > [!NOTE]  
    >  Le parole "fare clic con il pulsante destro del mouse sul testo" sono in `bookmark1` e `bookmark2`.  
  
 Quando si aggiunge in fase di progettazione un segnalibro a un documento, il sistema crea un controllo <xref:Microsoft.Office.Tools.Word.Bookmark>.  È possibile programmare il segnalibro in funzione di vari eventi.  È possibile scrivere codice nell'evento <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> del segnalibro che consente di visualizzare un menu di scelta rapida quando l'utente fa clic con il pulsante destro del mouse sul testo del segnalibro.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Aggiunta di controlli a un menu di scelta rapida  
 Aggiungere pulsanti al menu di scelta rapida visualizzato quando si fa clic con il pulsante destro del mouse sul documento.  
  
#### Per aggiungere controlli a un menu di scelta rapida  
  
1.  Aggiungere un elemento **Barra multifunzione XML** al progetto.  Per ulteriori informazioni, vedere [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  In **Esplora soluzioni**, selezionare **ThisDocument.cs** o in **ThisDocument.vb**.  
  
3.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file di classe **ThisDocument** viene aperto nell'editor di codice.  
  
4.  Aggiungere il codice seguente alla classe **ThisDocument**.  Questo codice esegue l'override del metodo CreateRibbonExtensibilityObject e restituisce la classe Ribbon XML all'applicazione di Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  In **Esplora soluzioni**, selezionare il file XML della barra multifunzione.  Per impostazione predefinita, il file XML della barra multifunzione è denominato Ribbon1.xml.  
  
6.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file XML della barra multifunzione viene aperto nell'editor di codice.  
  
7.  Nell'editor di codice, sostituire il contenuto del file XML della barra multifunzione con il codice seguente.  
  
    ```  
  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     Questo codice consente di aggiungere due pulsanti al menu di scelta rapida visualizzato quando si fa clic con il pulsante destro del mouse sul documento.  
  
8.  In **Esplora soluzioni**, fare clic con il pulsante destro del mouse su `ThisDocument` e quindi scegliere **Visualizza codice**.  
  
9. Dichiarare le variabili e una variabile segnalibro a livello di classe.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. In **Esplora soluzioni**, selezionare il file di codice di.  Per impostazione predefinita, il file di codice di è denominato **Ribbon1.cs** o **Ribbon1.vb**.  
  
11. Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file di codice della barra multifunzione viene aperto nell'editor di codice.  
  
12. Nel file di codice della barra multifunzione, aggiungere il seguente metodo.  Si tratta di un metodo di callback per i due pulsanti aggiunto al menu di scelta rapida del documento.  Questo metodo determina se questi pulsanti visualizzati nel menu di scelta rapida.  I pulsanti grassetto e corsivo vengono visualizzati solo facendo clic con il pulsante destro del mouse sul testo nel segnalibro.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Formattare il testo in un segnalibro  
  
#### Per formattare il testo nel segnalibro  
  
1.  Nel file di codice della barra multifunzione, aggiungere un gestore eventi `ButtonClick` per applicare la formattazione al segnalibro.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  **Esplora soluzioni**, selezionare **ThisDocument.cs** o **ThisDocument.vb**.  
  
3.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
     Il file di classe **ThisDocument** viene aperto nell'editor di codice.  
  
4.  Aggiungere il codice seguente alla classe **ThisDocument**.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  È necessario creare codice per gestire eventuali segnalibri sovrapposti.  In caso contrario, per impostazione predefinita verrà chiamato il codice di tutti i segnalibri all'interno della selezione.  
  
5.  In C\# è necessario aggiungere gestori eventi per i controlli Bookmark all'evento <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Per ulteriori informazioni sulla creazione di gestori eventi, vedere [Procedura: creare gestori eventi in progetti di Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## Verifica dell'applicazione  
 Verificare il documento per verificare che le voci di menu bold e corsive vengono visualizzati nel menu di scelta rapida facendo clic con il pulsante destro del mouse sul testo nel segnalibro e che il testo sia corretta.  
  
#### Per testare il documento  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Fare clic con il pulsante destro del mouse sul primo segnalibro e quindi scegliere **Bold**.  
  
3.  Verificare che tutto il testo presente in `bookmark1` sia formattato in grassetto.  
  
4.  Fare clic con il pulsante destro del mouse sul testo di sovrapposizione dei segnalibri e quindi fare clic su **Italic**.  
  
5.  Verificare che l'intero testo del segnalibro `bookmark2` sia in corsivo e che solo la parte di testo del segnalibro `bookmark1` che si sovrappone al segnalibro `bookmark2` sia in corsivo.  
  
## Passaggi successivi  
 Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Creazione di codice in risposta a eventi di controlli host in Excel.  Per ulteriori informazioni, vedere [Procedura dettagliata: programmazione per eventi di un controllo NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Utilizzo di una casella di controllo per modificare la formattazione di un segnalibro.  Per ulteriori informazioni, vedere [Procedura dettagliata: modifica della formattazione dei documenti mediante i controlli CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## Vedere anche  
 [Procedure dettagliate con Word](../vsto/walkthroughs-using-word.md)   
 [Personalizzazione dell'interfaccia utente di Office](../vsto/office-ui-customization.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controllo Bookmark](../vsto/bookmark-control.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  