---
title: "Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate"
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
  - "controlli del contenuto [sviluppo per Office in Visual Studio], associazione dati"
  - "parti XML personalizzate, associazione ai controlli contenuto"
  - "associazione dati [sviluppo per Office in Visual Studio], controlli contenuto"
  - "DatePickerContentControl, associazione a una parte XML personalizzata"
  - "DropDownListContentControl, associazione di elementi a una parte XML personalizzata"
  - "PlainTextContentControl, associazione a una parte XML personalizzata"
ms.assetid: 10d67769-6157-4703-a10c-d33e988f9095
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate
  Questa procedura dettagliata illustra come associare i controlli contenuto in una personalizzazione a livello di documento per Word a dati XML archiviati nel documento.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word consente di archiviare dati XML, denominati *parti XML personalizzate* in un documento.  È possibile controllare la visualizzazione di questi dati associando i controlli contenuto a elementi in una parte XML personalizzata.  Il documento di esempio in questa procedura dettagliata visualizza informazioni sui dipendenti che vengono archiviate in una parte XML personalizzata.  Quando si apre il documento, i controlli contenuto visualizzano i valori degli elementi XML.  Nella parte XML personalizzata vengono salvate le eventuali modifiche apportate al testo nei controlli contenuto.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di controlli contenuto al documento di Word presente in un progetto a livello di documento in fase di progettazione.  
  
-   Creazione di un file di dati XML e di uno schema XML che definisce gli elementi da associare ai controlli contenuto.  
  
-   Associazione dello schema XML al documento in fase di progettazione.  
  
-   Aggiunta dei contenuti del file XML a una parte XML personalizzata nel documento in fase di progettazione.  
  
-   Binding dei controlli contenuto a elementi nella parte XML personalizzata.  
  
-   Binding di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori definiti nello schema XML.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Creazione di un nuovo progetto di documento di Word  
 Creare un documento di Word che verrà usato nella procedura dettagliata.  
  
#### Per creare un progetto di documento di Word  
  
1.  Creare un progetto di documento di Word con il nome EmployeeControls.  Creare un nuovo documento per la soluzione.  Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] apre il nuovo documento di Word nella finestra di progettazione e aggiunge il progetto EmployeeControls a **Esplora soluzioni**.  
  
## Aggiunta di controlli contenuto al documento  
 Creare una tabella che contiene tre tipi diversi di controlli contenuto in cui un utente può visualizzare o modificare informazioni su un dipendente.  
  
#### Per aggiungere controlli contenuto al documento  
  
1.  Nel documento di Word ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] scegliere la scheda **Inserisci** della barra multifunzione.  
  
2.  Scegliere **Tabella** nel gruppo **Tabelle** e inserire una tabella con 2 colonne e 3 righe.  
  
3.  Digitare il testo nella prima colonna in modo che sia simile alla colonna seguente:  
  
    ||  
    |-|  
    |Nome dipendente|  
    |Data assunzione|  
    |Titolo|  
  
4.  Nella seconda colonna della tabella scegliere la prima riga \(accanto **Nome dipendente**\).  
  
5.  Nella barra multifunzione scegliere la scheda **Sviluppatore**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non è visibile, è necessario prima di tutto visualizzarla.  Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  Nel gruppo **Controlli** scegliere il pulsante **Testo** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> alla prima cella.  
  
7.  Nella seconda colonna della tabella, scegliere la seconda riga \(accanto a **Data assunzione**\).  
  
8.  Nel gruppo **Controlli** scegliere il pulsante **Selezione data** ![DatePickerContentControl](../vsto/media/datepicker.png "DatePickerContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> alla seconda cella.  
  
9. Nella seconda colonna della tabella selezionare la terza riga \(accanto a **Posizione**\).  
  
10. Nel gruppo **Controlli** scegliere il pulsante **Elenco a discesa** ![DropDownListContentControl](../vsto/media/dropdownlist.png "DropDownListContentControl") per aggiungere un <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> all'ultima cella.  
  
 È l'intera interfaccia utente per questo progetto.  Se si esegue il progetto a questo punto, è possibile digitare un testo nella prima riga e selezionare una data nella seconda riga.  Il passaggio successivo consiste nell'allegare i dati che si vogliano visualizzare al documento in un file XML.  
  
## Creazione di file di dati XML  
 In genere, si ottengono dati XML da archiviare in una parte XML personalizzata da un'origine esterna, ad esempio un file o un database.  In questa procedura dettagliata è possibile creare un file XML che contiene i dati del dipendente, contrassegnati da elementi che verranno associati ai controlli contenuto del documento.  Per rendere disponibili i dati in fase di esecuzione, incorporare il file XML come risorsa nell'assembly di personalizzazione.  
  
#### Per creare il file di dati  
  
1.  Scegliere **Aggiungi nuovo elemento**dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Scegliere **File XML** dal riquadro **Modelli**.  
  
3.  Denominare il file **employees.xml** e quindi scegliere il pulsante **Aggiungi**.  
  
     Il file **employees.xml** viene aperto nell'Editor di codice.  
  
4.  Sostituire i contenuti del file **employees.xml** con il testo seguente.  
  
    ```  
  
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">  
      <employee>  
        <name>Karina Leal</name>  
        <hireDate>1999-04-01</hireDate>  
        <title>Manager</title>  
      </employee>  
    </employees>  
    ```  
  
5.  In **Esplora soluzioni** scegliere il file **employees.xml**.  
  
6.  Nella finestra **Proprietà** selezionare la proprietà **Azione di compilazione** e quindi modificare il valore in **Risorsa incorporata**.  
  
     Questo passaggio incorpora il file XML come risorsa nell'assembly quando si compila il progetto.  e consente di accedere al contenuto del file XML in fase di esecuzione.  
  
## Creazione di uno schema XML  
 Se si intende associare un controllo contenuto a un singolo elemento in una parte XML personalizzata, non è necessario usare uno schema XML.  Tuttavia, per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a un set di valori, è necessario creare uno schema XML che convalida il file di dati XML creato in precedenza.  Lo schema XML definisce i valori possibili per l'elemento `title`.  L'associazione di <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> a questo elemento viene eseguita più avanti in questa procedura dettagliata.  
  
#### Per creare uno schema XML  
  
1.  Scegliere **Aggiungi nuovo elemento**dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Scegliere **Schema XML** dal riquadro **Modelli**.  
  
3.  Denominare lo schema **employees.xsd** e scegliere il pulsante **Aggiungi**.  
  
     Viene aperta la progettazione schema.  
  
4.  In **Esplora soluzioni** aprire il menu di scelta rapida per il file **employees.xsd** e scegliere **Visualizza codice**.  
  
5.  Sostituire i contenuti del file **employees.xsd** con lo schema seguente.  
  
    ```  
  
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"   
        targetNamespace="http://schemas.microsoft.com/vsto/samples"  
        xmlns:xs="http://www.w3.org/2001/XMLSchema"  
        elementFormDefault="qualified">  
      <xs:element name="employees" type="EmployeesType"></xs:element>  
      <xs:complexType name="EmployeesType">  
        <xs:all>  
          <xs:element name="employee" type="EmployeeType"/>  
        </xs:all>  
      </xs:complexType>  
      <xs:complexType name="EmployeeType">  
        <xs:sequence>  
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>  
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>  
        </xs:sequence>  
      </xs:complexType>  
      <xs:simpleType name="TitleType">  
        <xs:restriction base="xs:string">  
          <xs:enumeration value ="Engineer"/>  
          <xs:enumeration value ="Designer"/>  
          <xs:enumeration value ="Manager"/>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:schema>  
    ```  
  
6.  Scegliere **Salva tutto** dal menu **File** per salvare le modifiche nei file **employees.xml** e **employees.xsd**.  
  
## Associazione dello schema XML al documento  
 È necessario allegare lo schema XML al documento per associare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> ai valori validi dell'elemento `title`.  
  
#### Per allegare lo schema XML al documento \([!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]\)  
  
1.  Attivare **EmployeeControls.docx** nella finestra di progettazione.  
  
2.  Sulla barra multifunzione scegliere la scheda **Sviluppatore** e quindi il comando **Componenti aggiuntivi**.  
  
3.  Nella finestra di dialogo **Modelli e componenti aggiuntivi** scegliere la scheda **Schema XML** e quindi scegliere il pulsante **Aggiungi schema**.  
  
4.  Individuare lo schema **employees.xsd** creato in precedenza, che si trova nella directory del progetto e quindi scegliere il pulsante **Apri**.  
  
5.  Scegliere il pulsante **OK** nella finestra di dialogo **Impostazioni schema**.  
  
6.  Scegliere il pulsante **OK** per chiudere la finestra di dialogo **Modelli e componenti aggiuntivi**.  
  
#### Per allegare lo schema XML al documento \(Word 2010\)  
  
1.  Attivare **EmployeeControls.docx** nella finestra di progettazione.  
  
2.  Nella barra multifunzione scegliere la scheda **Sviluppatore**.  
  
3.  Nel gruppo **XML** scegliere il pulsante **Schema**.  
  
4.  Nella finestra di dialogo **Modelli e componenti aggiuntivi** scegliere la scheda **Schema XML** e quindi scegliere il pulsante **Aggiungi schema**.  
  
5.  Individuare lo schema **employees.xsd** creato in precedenza, che si trova nella directory del progetto e quindi scegliere il pulsante **Apri**.  
  
6.  Scegliere il pulsante **OK** nella finestra di dialogo **Impostazioni schema**.  
  
7.  Scegliere il pulsante **OK** per chiudere la finestra di dialogo **Modelli e componenti aggiuntivi**.  
  
     Visualizza il riquadro attività **Struttura XML**.  
  
8.  Chiudere il riquadro attività **Struttura XML**.  
  
## Aggiunta di una parte XML personalizzata al documento  
 Prima di poter associare i controlli contenuto a elementi nel file XML, è necessario aggiungere il contenuto del file XML a una nuova parte XML personalizzata nel documento.  
  
#### Per aggiungere una parte XML personalizzata al documento  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per **ThisDocument.cs** o **ThisDocument.vb** e quindi scegliere**Visualizza codice**.  
  
2.  Aggiungere le seguenti dichiarazioni alla classe `ThisDocument`.  Questo codice dichiara diversi oggetti che verranno usati per aggiungere una parte XML personalizzata al documento.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Aggiungere il metodo seguente alla classe `ThisDocument`.  Questo metodo ottiene il contenuto del file di dati XML incorporato come risorsa nell'assembly e restituisce il contenuto come stringa XML.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#3)]  
  
4.  Aggiungere il metodo seguente alla classe `ThisDocument`.  Il metodo crea `AddCustomXmlPart` una nuova parte XML personalizzata che contiene una stringa XML che viene passata al metodo.  
  
     Per garantire che la parte XML personalizzata venga creata solo una volta, il metodo crea la parte XML personalizzata solo se non esiste già nel documento una parte XML personalizzata con GUID corrispondente.  La prima volta che viene chiamato questo metodo, viene salvato il valore della proprietà <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> per la stringa `employeeXMLPartID`.  Il valore della stringa `employeeXMLPartID` viene mantenuto nel documento perché è stato dichiarato mediante l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#4)]  
  
## Binding dei controlli contenuto a elementi nella parte XML personalizzata  
 Associare ogni controllo contenuto a un elemento nella parte XML personalizzata usando la proprietà **XMLMapping** di ogni controllo contenuto.  
  
#### Per associare i controlli contenuto a elementi nella parte XML personalizzata  
  
1.  Aggiungere il metodo seguente alla classe `ThisDocument`.  Questo metodo associa ogni controllo del contenuto a un elemento nella parte XML personalizzata e imposta il formato di visualizzazione della data di <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#5)]  
  
## Esecuzione di codice quando il documento è aperto  
 Creare la parte XML personalizzata e associare i controlli personalizzati ai dati quando il documento viene aperto.  
  
#### Per eseguire il codice quando il documento è aperto  
  
1.  Aggiungere il seguente codice al metodo `ThisDocument_Startup` della classe `ThisDocument`.  Questo codice ottiene la stringa XML dal file **employees.xml**, aggiunge la stringa XML a una nuova parte XML personalizzata nel documento e associa i controlli contenuto agli elementi nella parte XML personalizzata.  
  
     [!code-csharp[Trin_ContentControlXmlPartWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlXmlPartWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlXmlPartWalkthrough/VB/ThisDocument.vb#2)]  
  
## Test del progetto  
 Quando si apre il documento, i controlli contenuto consentono di visualizzare dati dagli elementi nella parte XML personalizzata.  È possibile selezionare <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> per scegliere uno dei tre valori validi per l'elemento `title`, definiti nel file **employees.xsd**.  Se si modificano i dati in uno dei controlli contenuto, i nuovi valori vengono salvati nella parte XML personalizzata del documento.  
  
#### Per testare i controlli contenuto  
  
1.  Premere F5 per eseguire il progetto.  
  
2.  Verificare che la tabella nel documento sia simile alla tabella seguente.  Tutte le stringhe della seconda colonna sono ottenute da un elemento nella parte XML personalizzata del documento.  
  
    |||  
    |-|-|  
    |Nome dipendente|**Karina Leal**|  
    |Data assunzione|**1 aprile 1999**|  
    |Titolo|**Manager**|  
  
3.  Scegliere la cella a destra della cella Nome dipendente e digitare un nome diverso.  
  
4.  Scegliere la cella a destra della cella Data assunzione e selezionare una data diversa nella selezione data.  
  
5.  Scegliere la cella a destra della cella Titolo e selezionare un nuovo elemento dall'elenco a discesa.  
  
6.  Salvare e chiudere il documento.  
  
7.  In Esplora file aprire la cartella \\bin\\Debug nel percorso del progetto.  
  
8.  Aprire il menu di scelta rapida per il file EmployeeControls.docx e quindi scegliere **Rinomina**.  
  
9. Assegnare al file il nome EmployeeControls.docx.zip.  
  
     Il documento EmployeeControls.docx viene salvato nel formato Open XML.  Il documento è stato rinominato con l'estensione del nome file zip e quindi è possibile esaminarne il contenuto.  Per altre informazioni sul formato Open XML, vedere l'articolo tecnico [Introduzione ai formati di file Office Open XML \(2007\)](http://msdn.microsoft.com/it-it/96018532-f62c-4da7-bbff-16b96a483fbf).  
  
10. Aprire il file EmployeeControls.docx.zip.  
  
11. Aprire la cartella **customXml**.  
  
12. Aprire il menu di scelta rapida per **item2.xml** e quindi scegliere **Apri**.  
  
     Il file contiene la parte XML personalizzata che è stata aggiunta al documento.  
  
13. Verificare che gli elementi `name`, `hireDate` e `title` contengano i nuovi valori immessi nei controlli contenuto nel documento.  
  
14. Chiudere il file **item2.xml**.  
  
## Passaggi successivi  
 Per altre informazioni sull'utilizzo dei controlli contenuto, vedere gli argomenti seguenti:  
  
-   Usare tutti i controlli contenuto disponibili per creare un modello.  Per altre informazioni, vedere [Procedura dettagliata: creazione di un modello utilizzando i controlli del contenuto](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
-   Modificare i dati nella parte XML personalizzata mentre il documento è chiuso.  Alla successiva apertura del documento, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati.  
  
-   Usare i controlli contenuto per proteggere parti di un documento.  Per altre informazioni, vedere [Procedura: proteggere parti di documenti mediante i controlli del contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controlli del contenuto](../vsto/content-controls.md)   
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Procedura: proteggere parti di documenti mediante i controlli del contenuto](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  