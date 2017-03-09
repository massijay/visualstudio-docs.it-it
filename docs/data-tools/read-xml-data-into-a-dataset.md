---
title: "Procedura dettagliata: lettura dei dati XML in un dataset | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], lettura da file XML"
  - "accesso ai dati [Visual Studio], XML (dati)"
  - "dataset [Visual Basic], lettura di dati XML"
  - "lettura di dati, XML (file)"
  - "lettura di file, XML"
  - "lettura di XML"
  - "XML [Visual Studio], lettura"
  - "XML (documenti), lettura"
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura dettagliata: lettura dei dati XML in un dataset
In ADO.NET sono disponibili semplici metodi per lavorare con i dati XML.  In questa procedura dettagliata verrà creata un'applicazione Windows con la quale i dati XML saranno caricati in un DataSet.  Il dataset verrà quindi visualizzato in un <xref:System.Windows.Forms.DataGridView>.  Infine, in una casella di testo verrà visualizzato codice XML Schema basato sul contenuto del file XML.  
  
 La procedura dettagliata è costituita da cinque passaggi principali:  
  
1.  Creazione di un nuovo progetto  
  
2.  Creazione di un file XML con i dati da inserire nel DataSet.  
  
3.  Creazione dell'interfaccia utente.  
  
4.  Creazione del dataset, lettura del file XML e visualizzazione del contenuto in un controllo <xref:System.Windows.Forms.DataGridView>.  
  
5.  Aggiunta di codice per la visualizzazione del linguaggio XML Schema basato sul file XML in un controllo <xref:System.Windows.Forms.TextBox>.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Creazione di un nuovo progetto  
 In questo passaggio verrà creato un progetto Visual Basic o Visual C\# che conterrà questa procedura dettagliata.  
  
#### Per creare un nuovo progetto Windows  
  
1.  Scegliere il comando per la creazione di un nuovo progetto dal menu **File**.  
  
2.  Assegnazione del nome `ReadingXML` al progetto.  
  
3.  Selezionare **Applicazione Windows** e scegliere **OK**.  Per ulteriori informazioni, vedere [Applicazioni client](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Il progetto **ReadingXML** verrà creato e aggiunto a Esplora soluzioni.  
  
## Creazione del file XML con i dati da inserire nel DataSet  
 Poiché la procedura dettagliata è incentrata sull'inserimento dei dati XML in un dataset, viene fornito il contenuto di un file XML.  
  
#### Per creare il file XML con i dati da inserire nel DataSet  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  Selezionare il **File XML**, denominarlo `authors.xml`, quindi scegliere **Aggiungi**.  
  
     Il file XML verrà caricato nella finestra di progettazione e sarà quindi pronto per la modifica.  
  
3.  Incollare il codice riportato di seguito nell'editor, sotto la dichiarazione XML.  
  
    ```xml  
    <Authors_Table>  
      <authors>  
        <au_id>172-32-1176</au_id>  
        <au_lname>White</au_lname>  
        <au_fname>Johnson</au_fname>  
        <phone>408 496-7223</phone>  
        <address>10932 Bigge Rd.</address>  
        <city>Menlo Park</city>  
        <state>CA</state>  
        <zip>94025</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>213-46-8915</au_id>  
        <au_lname>Green</au_lname>  
        <au_fname>Margie</au_fname>  
        <phone>415 986-7020</phone>  
        <address>309 63rd St. #411</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94618</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>238-95-7766</au_id>  
        <au_lname>Carson</au_lname>  
        <au_fname>Cheryl</au_fname>  
        <phone>415 548-7723</phone>  
        <address>589 Darwin Ln.</address>  
        <city>Berkeley</city>  
        <state>CA</state>  
        <zip>94705</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>267-41-2394</au_id>  
        <au_lname>Hunter</au_lname>  
        <au_fname>Anne</au_fname>  
        <phone>408 286-2428</phone>  
        <address>22 Cleveland Av. #14</address>  
        <city>San Jose</city>  
        <state>CA</state>  
        <zip>95128</zip>  
        <contract>true</contract>  
      </authors>  
      <authors>  
        <au_id>274-80-9391</au_id>  
        <au_lname>Straight</au_lname>  
        <au_fname>Dean</au_fname>  
        <phone>415 834-2919</phone>  
        <address>5420 College Av.</address>  
        <city>Oakland</city>  
        <state>CA</state>  
        <zip>94609</zip>  
        <contract>true</contract>  
      </authors>  
    </Authors_Table>  
    ```  
  
4.  Dal menu **File** scegliere **Salva authors.xml**.  
  
## Creazione dell'interfaccia utente  
 L'interfaccia utente per questa applicazione è composta dai seguenti elementi:  
  
-   Un controllo <xref:System.Windows.Forms.DataGridView> per la visualizzazione del contenuto del file XML sotto forma di dati.  
  
-   Un controllo <xref:System.Windows.Forms.TextBox> per la visualizzazione del codice XML Schema associato al file XML.  
  
-   Due controlli <xref:System.Windows.Forms.Button>.  
  
    -   Un pulsante per la lettura del file XML e l'inserimento dei dati nel dataset e la visualizzazione dei dati nel controllo <xref:System.Windows.Forms.DataGridView>.  
  
    -   Un secondo pulsante per l'estrazione dello schema dal dataset e la relativa visualizzazione nel controllo <xref:System.Windows.Forms.TextBox> mediante una classe <xref:System.IO.StringWriter>.  
  
#### Per aggiungere controlli al form  
  
1.  Aprire il `Form1` nella visualizzazione Progettazione.  
  
2.  Dalla **Casella degli strumenti** trascinare i due controlli seguenti nel form.  
  
    -   Un controllo <xref:System.Windows.Forms.DataGridView>  
  
    -   Un controllo <xref:System.Windows.Forms.TextBox>  
  
    -   Due controlli <xref:System.Windows.Forms.Button>  
  
3.  Impostare le seguenti proprietà:  
  
    |Controllo|Proprietà|Impostazione|  
    |---------------|---------------|------------------|  
    |`TextBox1`|**Multiline**|`true`|  
    ||**ScrollBars**|**Verticale**|  
    |`Button1`|**Nome**|`ReadXmlButton`|  
    ||**Text**|`Read XML`|  
    |`Button2`|**Nome**|`ShowSchemaButton`|  
    ||**Text**|`Show Schema`|  
  
## Creazione del DataSet in cui saranno inseriti i dati XML  
 Nella procedura seguente, viene creato un nuovo dataset denominato `authors`.  Per ulteriori informazioni sui dataset, vedere [Utilizzo di dataset in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Per creare un nuovo dataset per la ricezione dei dati XML  
  
1.  Dopo aver selezionato il file di origine di **Form1** in **Esplora soluzioni**, fare clic sul pulsante **Visualizza finestra di progettazione** nella barra degli strumenti di **Esplora soluzioni**.  
  
2.  Dalla [Casella degli strumenti, Scheda Dati](../ide/reference/toolbox-data-tab.md), trascinare un **DataSet** nel **Form1**.  
  
3.  selezionato **dataset non tipizzato** in  **aggiungere il dataset** la finestra di dialogo e quindi fare clic su  **Scegliere OK**.  
  
     Il **DataSet1** viene aggiunto alla barra dei componenti.  
  
4.  Nella finestra **Proprietà** impostare le proprietà **Name** e <xref:System.Data.DataSet.DataSetName%2A> su `AuthorsDataSet`.  
  
## Creazione del gestore eventi per l'inserimento dei dati XML nel DataSet  
 Il pulsante **Read XML** consente di leggere il file XML e inserire i relativi dati nel dataset, quindi di impostare le proprietà del controllo <xref:System.Windows.Forms.DataGridView> per l'associazione di tale oggetto al dataset.  
  
#### Per aggiungere codice al gestore eventi ReadXmlButton\_Click  
  
1.  In **Esplora soluzioni** selezionare **Form1** e fare clic sul pulsante **Visualizza finestra di progettazione** sulla barra degli strumenti **Esplora soluzioni**.  
  
2.  Fare doppio clic sul pulsante **Read XML**.  
  
     Nell'**editor di codice** verrà visualizzato il gestore eventi `ReadXmlButton_Click`.  
  
3.  Digitare il codice che segue nel gestore eventi `ReadXmlButton_Click`:  
  
     [!code-cs[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]  
  
4.  Nel codice del gestore eventi `ReadXMLButton_Click` modificare la voce `filepath =` nel percorso corretto.  
  
## Creazione del gestore eventi per la visualizzazione dello schema nell'oggetto Textbox  
 Tramite il pulsante **Show Schema** viene creato un oggetto <xref:System.IO.StringWriter> nel quale viene inserito lo schema e che viene visualizzato nell'oggetto <xref:System.Windows.Forms.TextBox>.  
  
#### Per aggiungere codice al gestore eventi ShowSchemaButton\_Click  
  
1.  In **Esplora soluzioni** selezionare **Form1**, quindi fare clic sul pulsante **Visualizza finestra di progettazione**.  
  
2.  Fare doppio clic sul pulsante **Show Schema**.  
  
     Nell'**editor di codice** verrà visualizzato il gestore eventi `ShowSchemaButton_Click`.  
  
3.  Digitare il codice che segue nel gestore eventi `ShowSchemaButton_Click`:  
  
     [!code-cs[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]  
  
## Test  
 È ora possibile verificare il form per assicurarsi che funzioni correttamente.  
  
#### Per eseguire il test del form  
  
1.  ‎Premere F5 per eseguire l'applicazione.  
  
2.  Fare clic sul pulsante **Read XML**.  
  
     Nel controllo DataGridView verrà visualizzato il contenuto del file XML.  
  
3.  Fare clic sul pulsante **Show Schema**.  
  
     Nella casella di testo verrà visualizzato il codice XML Schema associato al file XML.  
  
## Passaggi successivi  
 In questa procedura dettagliata vengono riportati i concetti di base per la lettura di un file XML e l'inserimento dei dati in un DataSet e per la creazione di uno schema basato sul contenuto del file XML.  Di seguito sono elencate alcune procedure che potrebbero essere necessarie per estendere il progetto:  
  
-   Modifica dei dati del DataSet e relativa riscrittura come XML.  Per ulteriori informazioni, vedere <xref:System.Data.DataSet.WriteXml%2A>.  
  
-   Modifica dei dati del DataSet e relativa scrittura in un database.  Per ulteriori informazioni, vedere [Salvataggio di dati](../data-tools/saving-data.md).  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)