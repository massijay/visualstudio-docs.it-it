---
title: "Procedura dettagliata: aggiungere una pagina dell&#39;applicazione a un flusso di lavoro"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "pagina applicazione [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, aggiunta di pagine di applicazioni a flussi di lavoro"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura dettagliata: aggiungere una pagina dell&#39;applicazione a un flusso di lavoro
  In questa procedura dettagliata viene illustrato come aggiungere a un progetto flusso di lavoro una pagina dell'applicazione in cui vengono visualizzati i dati derivati da un flusso di lavoro.  Si basa sul progetto descritto nell'argomento [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Aggiunta di una pagina dell'applicazione ASPX a un progetto flusso di lavoro di SharePoint.  
  
-   Acquisizione e modifica dei dati del progetto flusso di lavoro.  
  
-   Visualizzazione dei dati in una tabella nella pagina dell'applicazione.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   È inoltre necessario aver completato il progetto nell'argomento [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## Modifica del codice del flusso di lavoro  
 Innanzitutto, aggiungere una riga di codice al flusso di lavoro per impostare il valore della colonna Risultato sull'importo della nota spese.  Questo valore viene utilizzato in un secondo momento per il calcolo riepilogativo della nota spese.  
  
#### Per impostare il valore della colonna Risultato nel flusso di lavoro  
  
1.  Caricare il progetto completato dall'argomento [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Aprire il codice per Workflow1.cs o Workflow1.vb \(a seconda del linguaggio di programmazione\).  
  
3.  Nella parte inferiore del metodo `createTask1_MethodInvoking` aggiungere il codice seguente:  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## Creazione di una pagina applicazione  
 Aggiungere un form ASPX al progetto.  In questo form verranno visualizzati i dati ottenuti dal progetto flusso di lavoro della nota spese.  A tal fine si aggiungerà una pagina dell'applicazione.  In quest'ultima viene utilizzata la stessa pagina master delle altre pagine di SharePoint, pertanto assomiglierà alle altre pagine del sito di SharePoint.  
  
#### Per aggiungere una pagina dell'applicazione al progetto  
  
1.  Scegliere il progetto ExpenseReport quindi, nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
2.  Nel riquadro di **Modelli**, scegliere il modello **Pagina applicazione**, utilizzare il nome predefinito per l'elemento di progetto \(**ApplicaitonPage1.aspx**\) e selezionare il pulsante **Aggiungi**.  
  
3.  Nel codice [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] di ApplicationPage1.aspx sostituire la sezione `PlaceHolderMain` con quanto riportato di seguito:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Questo codice consente di aggiungere alla pagina una tabella con il relativo titolo.  
  
4.  Aggiungere un titolo alla pagina dell'applicazione sostituendo la sezione `PlaceHolderPageTitleInTitleArea` con quanto riportato di seguito:  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## Codifica della pagina dell'applicazione  
 Aggiungere codice alla pagina dell'applicazione relativa al riepilogo della nota spese.  Quando si apre la pagina, l'elenco Attività di SharePoint viene analizzato dal codice relativamente alle spese che hanno superato il limite di spesa allocato.  Nella nota spese viene elencato ogni elemento insieme all'importo delle spese.  
  
#### Per codificare la pagina dell'applicazione  
  
1.  Selezionare il nodo **ApplicationPage1.aspx**, quindi scegliere sulla barra dei menu **Visualizza**, **Code** per visualizzare il code\-behind della pagina dell'applicazione.  
  
2.  Sostituire le istruzioni **using** o **Import** \(a seconda del linguaggio di programmazione\) nella parte superiore della classe con quanto riportato di seguito:  
  
    ```vb  
    Imports System  
    Imports Microsoft.SharePoint  
    Imports Microsoft.SharePoint.WebControls  
    Imports System.Collections  
    Imports System.Data  
    Imports System.Web.UI  
    Imports System.Web.UI.WebControls  
    Imports System.Web.UI.WebControls.WebParts  
    Imports System.Drawing  
    Imports Microsoft.SharePoint.Navigation  
    ```  
  
    ```csharp  
    using System;  
    using Microsoft.SharePoint;  
    using Microsoft.SharePoint.WebControls;  
    using System.Collections;  
    using System.Data;  
    using System.Web.UI;  
    using System.Web.UI.WebControls;  
    using System.Web.UI.WebControls.WebParts;  
    using System.Drawing;  
    using Microsoft.SharePoint.Navigation;  
    ```  
  
3.  Aggiungere al metodo `Page_Load` il codice seguente:  
  
    ```vb  
    Try  
        ' Reference the Tasks list on the SharePoint site.  
        ' Replace "TestServer" with a valid SharePoint server name.  
        Dim site As SPSite = New SPSite("http://TestServer")  
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")  
        ' string text = "";  
        Dim sum As Integer = 0  
        Table1.Rows.Clear()  
        ' Add table headers.  
        Dim hr As TableHeaderRow = New TableHeaderRow  
        hr.BackColor = Color.LightBlue  
        Dim hc1 As TableHeaderCell = New TableHeaderCell  
        Dim hc2 As TableHeaderCell = New TableHeaderCell  
        hc1.Text = "Expense Report Name"  
        hc2.Text = "Amount Exceeded"  
        hr.Cells.Add(hc1)  
        hr.Cells.Add(hc2)  
        ' Add the TableHeaderRow as the first item   
        ' in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr)  
        ' Iterate through the tasks in the Task list and collect those    
        ' that have values in the "Related Content" and "Outcome" fields   
        ' - the fields written to when expense approval is required.  
        For Each item As SPListItem In list.Items  
            Dim s_relContent As String = ""  
            Dim s_outcome As String = ""  
            Try  
                ' Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related Content")  
                s_outcome = item.GetFormattedValue("Outcome")  
            Catch erx As System.Exception  
                ' Task does not have fields - skip it.  
                Continue For  
            End Try  
            ' Convert amount to an int and keep a running total.  
            If (Not String.IsNullOrEmpty(s_relContent) And Not   
              String.IsNullOrEmpty(s_outcome)) Then  
                sum = (sum + Convert.ToInt32(s_outcome))  
                Dim relContent As TableCell = New TableCell  
                relContent.Text = s_relContent  
                Dim outcome As TableCell = New TableCell  
                outcome.Text = ("$" + s_outcome)  
                Dim dataRow2 As TableRow = New TableRow  
                dataRow2.Cells.Add(relContent)  
                dataRow2.Cells.Add(outcome)  
                Table1.Rows.Add(dataRow2)  
            End If  
        Next  
        ' Report the sum of the reports in the table footer.  
        Dim tfr As TableFooterRow = New TableFooterRow  
        tfr.BackColor = Color.LightGreen  
        ' Create a TableCell object to contain the   
        ' text for the footer.  
        Dim ftc1 As TableCell = New TableCell  
        Dim ftc2 As TableCell = New TableCell  
        ftc1.Text = "TOTAL: "  
        ftc2.Text = ("$" + Convert.ToString(sum))  
        ' Add the TableCell object to the Cells  
        ' collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1)  
        tfr.Cells.Add(ftc2)  
        ' Add the TableFooterRow to the Rows  
        ' collection of the table.  
        Table1.Rows.Add(tfr)  
    Catch errx As Exception  
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))  
    End Try  
    ```  
  
    ```csharp  
    try  
    {  
        // Reference the Tasks list on the SharePoint site.  
        // Replace "TestServer" with a valid SharePoint server name.  
        SPSite site = new SPSite("http://TestServer");  
        SPList list = site.AllWebs[0].Lists["Tasks"];  
  
        // string text = "";  
        int sum = 0;  
  
        Table1.Rows.Clear();  
  
        // Add table headers.  
        TableHeaderRow hr = new TableHeaderRow();  
        hr.BackColor = Color.LightBlue;  
        TableHeaderCell hc1 = new TableHeaderCell();  
        TableHeaderCell hc2 = new TableHeaderCell();  
        hc1.Text = "Expense Report Name";  
        hc2.Text = "Amount Exceeded";  
        hr.Cells.Add(hc1);  
        hr.Cells.Add(hc2);  
        // Add the TableHeaderRow as the first item   
        // in the Rows collection of the table.  
        Table1.Rows.AddAt(0, hr);  
  
        // Iterate through the tasks in the Task list and collect those   
        // that have values in the "Related Content" and "Outcome"   
        // fields - the fields written to when expense approval is   
        // required.  
        foreach (SPListItem item in list.Items)  
        {  
            string s_relContent = "";  
            string s_outcome = "";  
  
            try  
            {  
                // Task has the fields - treat as expense report.  
                s_relContent = item.GetFormattedValue("Related   
                  Content");  
                s_outcome = item.GetFormattedValue("Outcome");  
            }  
            catch  
            {  
                // Task does not have fields - skip it.  
                continue;  
            }  
  
            if (!String.IsNullOrEmpty(s_relContent) &&   
              !String.IsNullOrEmpty(s_outcome))  
            {  
                // Convert amount to an int and keep a running total.  
                sum += Convert.ToInt32(s_outcome);  
                TableCell relContent = new TableCell();  
                relContent.Text = s_relContent;  
                TableCell outcome = new TableCell();  
                outcome.Text = "$" + s_outcome;  
                TableRow dataRow2 = new TableRow();  
                dataRow2.Cells.Add(relContent);  
                dataRow2.Cells.Add(outcome);  
                Table1.Rows.Add(dataRow2);  
            }  
        }  
  
        // Report the sum of the reports in the table footer.  
           TableFooterRow tfr = new TableFooterRow();  
        tfr.BackColor = Color.LightGreen;  
  
        // Create a TableCell object to contain the   
        // text for the footer.  
        TableCell ftc1 = new TableCell();  
        TableCell ftc2 = new TableCell();  
        ftc1.Text = "TOTAL: ";  
        ftc2.Text = "$" + Convert.ToString(sum);  
  
        // Add the TableCell object to the Cells  
        // collection of the TableFooterRow.  
        tfr.Cells.Add(ftc1);  
        tfr.Cells.Add(ftc2);  
  
        // Add the TableFooterRow to the Rows  
        // collection of the table.  
        Table1.Rows.Add(tfr);  
    }  
  
    catch (Exception errx)  
    {  
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());  
    }  
    ```  
  
    > [!WARNING]  
    >  Assicurarsi di sostituire "TestServer" nel codice con quello di un valido server sul quale è in esecuzione SharePoint.  
  
## Test della pagina dell'applicazione  
 Determinare se i dati della spesa vengono visualizzati correttamente nella pagina dell'applicazione.  
  
#### Per testare la pagina dell'applicazione  
  
1.  Selezionare il tasto F5 per eseguire e distribuire il progetto in SharePoint.  
  
2.  Selezionare il pulsante **Pagina iniziale**, quindi selezionare il collegamento **Documenti condivisi** sulla barra Avvio veloce per visualizzare l'elenco dei Documenti condivisi sul sito SharePoint.  
  
3.  Per rappresentare i rapporti spese per questo esempio, caricare alcuni nuovi documenti nell'elenco Documenti selezionando il collegamento **Documenti** nella scheda **Strumenti raccolta** nella parte superiore della pagina e selezionare il pulsante **Carica documento** sulla barra multifunzione.  
  
4.  Dopo aver caricato alcuni documenti, creare un'istanza del flusso di lavoro scegliendo il collegamento **Libreria** nella scheda **Parte** nella parte superiore della pagina e selezionando il pulsante **Impostazioni libreria** sulla barra multifunzione degli strumenti.  
  
5.  Nella pagina **Impostazioni raccolta documenti**, selezionare il collegamento **Impostazioni flusso di lavoro** nella sezione **Autorizzazioni e gestione**.  
  
6.  Nella pagina **Impostazioni flusso di lavoro** selezionare il collegamento **Aggiungi flusso di lavoro**.  
  
7.  Nella pagina **Aggiungi flusso di lavoro** selezionare il flusso di lavoro **ExpenseReport \- Workflow1**, immettere un nome per il flusso di lavoro, come ad esempio ExpenseTest, quindi selezionare il pulsante **Avanti**.  
  
     Viene visualizzato il form di associazione del flusso di lavoro.  Utilizzarlo per indicare l'importo del limite di spesa.  
  
8.  Nel form di Associazione, immettere **1000** nella casella **Limite di auto approvazione** quindi scegliere il pulsante **Associa flusso di lavoro**.  
  
9. Selezionare il pulsante **Pagina iniziale** per ritornare alla home page di SharePoint.  
  
10. Selezionare il collegamento **Documenti condivisi** sulla barra Avvio veloce.  
  
11. Scegliere uno dei documenti caricati per visualizzare una freccia a discesa, selezionare il documento, quindi scegliere l'elemento **Workflows**.  
  
12. Selezionare l'immagine accanto a ExpenseTest per visualizzare il form di avvio del flusso di lavoro.  
  
13. Nella casella di testo **Expense Total**, immettere un valore maggiore di 1000, quindi selezionare il pulsante **Avvia flusso di lavoro**.  
  
     Quando una spesa segnalata supera l'importo allocato, viene aggiunta un'attività al relativo elenco.  All'elemento della nota spese nell'elenco Documenti condivisi viene aggiunta anche una colonna denominata **ExpenseTest** con il valore **Completato**.  
  
14. Ripetere i passaggi da 11 a 13 con gli altri documenti dell'elenco Documenti condivisi. Il numero esatto di documenti non è importante.  
  
15. Visualizzare la pagina dell'applicazione relativa al riepilogo del report delle spese aprendo il seguente URL in un browser: **http:\/\/***SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**.  
  
     Nella pagina riepilogativa della nota spese sono elencate tutte le note spese che hanno superato l'importo allocato, l'importo della differenza superata e l'importo totale per tutte le note spese.  
  
## Passaggi successivi  
 Per ulteriori informazioni sulle pagine dell'applicazione di SharePoint, vedere [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Per ulteriori informazioni su come progettare il contenuto delle pagine di SharePoint tramite Visual Web Designer di Visual Studio consultare gli argomenti seguenti:  
  
-   [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## Vedere anche  
 [Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Procedura: creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)   
 [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  