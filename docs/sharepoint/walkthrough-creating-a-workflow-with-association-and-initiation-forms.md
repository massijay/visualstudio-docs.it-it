---
title: "Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio"
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
  - "form di associazione [sviluppo per SharePoint in Visual Studio]"
  - "form di avvio [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, form di associazione del flusso di lavoro"
  - "sviluppo per SharePoint in Visual Studio, form di avvio del flusso di lavoro"
  - "sviluppo per SharePoint in Visual Studio, flussi di lavoro"
  - "flussi di lavoro [sviluppo per SharePoint in Visual Studio]"
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura dettagliata: creazione di un flusso di lavoro con form di associazione e di avvio
  In questa procedura dettagliata viene illustrato come creare un flusso di lavoro sequenziale di base in cui è incorporato l'utilizzo di form di associazione e di avvio.  Si tratta di form ASPX che consentono di aggiungere parametri a un flusso di lavoro quando viene sottoposto alla prima associazione dall'amministratore di SharePoint \(form di associazione\) e quando il flusso di lavoro viene avviato dall'utente \(form di avvio\).  
  
 In questa procedura dettagliata viene illustrato uno scenario in cui un utente desidera creare un flusso di lavoro di approvazione per le note spese con i requisiti seguenti:  
  
-   Quando il flusso di lavoro è associato a un elenco, all'amministratore viene presentato un form di associazione in cui immettere un limite in dollari per le note spese.  
  
-   I dipendenti caricano le note spese nell'elenco Documenti condivisi, avviano il flusso di lavoro, quindi immettono il totale della spesa nel form di avvio del flusso di lavoro.  
  
-   Se il totale della nota spese di un dipendente supera il limite stabilito dall'amministratore, viene creata un'attività affinché il responsabile del dipendente approvi la nota spese.  Tuttavia, se il totale della nota spese di un dipendente è minore o uguale al limite della spesa, nell'elenco della cronologia del flusso di lavoro viene scritto un messaggio approvato automaticamente.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto flusso di lavoro sequenziale per la definizione dell'elenco di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Creazione di una pianificazione del flusso di lavoro.  
  
-   Gestione degli eventi di attività del flusso di lavoro.  
  
-   Creazione di form di associazione e di avvio per il flusso di lavoro.  
  
-   Associazione del flusso di lavoro.  
  
-   Avvio manuale del flusso di lavoro.  
  
> [!NOTE]  
>  Sebbene in questa procedura dettagliata venga utilizzato un progetto flusso di lavoro sequenziale, il processo è identico per i flussi di lavoro macchina a stati.  
>   
>  Inoltre, sul computer potrebbero essere visualizzati nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] presenti nelle istruzioni seguenti.  L'edizione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] di cui si dispone e le impostazioni utilizzate determinano questi elementi.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Creazione di un progetto Flusso di lavoro sequenziale SharePoint  
 Innanzitutto, creare un progetto flusso di lavoro sequenziale in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Un flusso di lavoro sequenziale è una serie di passaggi eseguiti in ordine fino al completamento dell'ultima attività.  In questa procedura si creerà un flusso di lavoro sequenziale che verrà applicato all'elenco Documenti condivisi di SharePoint.  La procedura guidata del flusso di lavoro consente di associare quest'ultimo alla definizione di sito o alla definizione di elenco, nonché di determinare quando verrà avviato.  
  
#### Per creare un progetto Flusso di lavoro sequenziale SharePoint  
  
1.  Sulla barra dei menu scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  
  
2.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Nel riquadro **Modelli**, scegliere il modello di progetto **Progetto SharePoint 2010**.  
  
4.  Nella casella di testo **Nome** inserire ExpenseReport e quindi selezionare il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
5.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug**, scegliere il pulsante di opzione **Distribuisci come soluzione farm**, quindi selezionare il pulsante **Fine** per accettare il livello di affidabilità e il sito predefinito.  
  
     Questo passaggio consente anche di impostare il livello di attendibilità per la soluzione come soluzione della farm, ovvero l'unica opzione disponibile per i progetti flusso di lavoro.  
  
6.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
7.  Sulla barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
8.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
9. Nel riquadro **Modelli**, scegliere il modello **Flusso di lavoro sequenziale \(solo soluzione farm\)** quindi scegliere il pulsante **Aggiungi**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
10. Nella pagina **Specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito \(**ExpenseReport \- Workflow1**\).  Mantenere il valore predefinito del tipo di modello di flusso di lavoro, ovvero **Flusso di lavoro elenco**.  Fare clic sul pulsante **Avanti**.  
  
11. Nella pagina **Associare automaticamente il flusso di lavoro in una sessione di debug** deselezionare la casella che consente di associare automaticamente il modello di flusso di lavoro, se selezionata.  
  
     Questo passaggio permette di associare manualmente il flusso di lavoro all'elenco Documenti condivisi in una fase successiva e di visualizzare quindi il form di associazione.  
  
12. Fare clic sul pulsante **Fine**.  
  
## Aggiunta di un form di associazione al flusso di lavoro  
 Creare un form di associazione con estensione ASPX che viene visualizzato quando l'amministratore di SharePoint associa per la prima volta il flusso di lavoro a un documento della nota spese.  
  
#### Per aggiungere un form di associazione al flusso di lavoro  
  
1.  Scegliere il nodo **Workflow1** in **Solution Explorer**.  
  
2.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi nuovo elemento** per visualizzare la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Nella visualizzazione struttura ad albero della finestra di dialogo espandere **Visual C\#** o **Visual Basic** \(a seconda del linguaggio del progetto\), espandere il nodo **SharePoint**, quindi selezionare il nodo **2010**.  
  
4.  Nell'elenco di modelli, scegliere il modello **Form di associazione flusso di lavoro**.  
  
5.  Nella casella di testo **Nome** inserire ExpenseReportAssocForm.aspx.  
  
6.  Selezionare il pulsante **Aggiungi** per aggiungere il form al progetto.  
  
## Progettazione e codifica del form di associazione  
 In questa procedura si fornisce funzionalità al form di associazione aggiungendovi controlli e codice.  
  
#### Per progettare e codificare il form di associazione  
  
1.  Nel form di associazione \(ExpenseReportAssocForm.aspx\), individuare l'elemento `asp:Content` con `ID="Main"`.  
  
2.  Subito dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo in cui viene richiesto il limite per l'approvazione della spesa \(*AutoApproveLimit*\):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Espandere il file **ExpenseReportAssocForm.aspx** in **Esplora soluzioni** per visualizzare i file dipendenti.  
  
    > [!NOTE]  
    >  Se il progetto è in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], è necessario selezionare il pulsante **Mostra tutti i file** per effettuare questo passaggio.  
  
4.  Aprire il menu di scelta rapida per il file ExpenseReportAssocForm.aspx e scegliere **Visualizza codice**.  
  
5.  Sostituire il metodo `GetAssociationData` con:  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## Aggiunta di un form di avvio al flusso di lavoro  
 Creare il form di avvio che viene visualizzato quando gli utenti eseguono il flusso di lavoro relativo alle note spese.  
  
#### Per creare un form di avvio  
  
1.  Scegliere il nodo **Workflow1** in **Solution Explorer**.  
  
2.  Nella barra dei menu, selezionare **Progetto**, **Aggiungi nuovo elemento** visualizza la finestra di dialogo **Aggiungi nuovo elemento**.  
  
3.  Nella visualizzazione struttura ad albero della finestra di dialogo espandere **Visual C\#** o **Visual Basic**  \(a seconda del linguaggio del progetto\), espandere il nodo **SharePoint**, quindi selezionare il nodo **2010**.  
  
4.  Nell'elenco di modelli, scegliere il modello **Form di avvio del flusso di lavoro**.  
  
5.  Nella casella di testo **Nome**, inserire ExpenseReportInitForm.aspx.  
  
6.  Selezionare il pulsante **Aggiungi** per aggiungere il form al progetto.  
  
## Progettazione e codifica del form di avvio  
 Fornire funzionalità al form di avvio aggiungendovi controlli e codice.  
  
#### Per codificare il form di avvio  
  
1.  Nel form di avvio \(ExpenseReportInitForm.aspx\), individuare l'elemento `asp:Content` con contiene `ID="Main"`.  
  
2.  Subito dopo la prima riga in questo elemento di contenuto, aggiungere il codice seguente per creare un'etichetta e una casella di testo in cui viene visualizzato il limite per l'approvazione della spesa \(*AutoApproveLimit*\) immesso nel form di associazione, nonché un'etichetta e una casella di testo aggiuntive per il totale della spesa \(*ExpenseTotal*\):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Espandere il file **ExpenseReportInitForm.aspx** in **Esplora soluzioni** per visualizzare i file dipendenti.  
  
4.  Aprire il menu di scelta rapida per il file ExpenseReportInitForm.aspx e scegliere **Visualizza codice**.  
  
5.  Sostituire il metodo `Page_Load` con l'esempio seguente:  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  Sostituire il metodo `GetInitiationData` con l'esempio seguente:  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## Personalizzazione del flusso di lavoro  
 Personalizzare il flusso di lavoro.  In un secondo momento si assoceranno due form al flusso di lavoro.  
  
#### Per personalizzare il flusso di lavoro  
  
1.  Visualizzare il flusso di lavoro in Progettazione flussi di lavoro aprendo Workflow1 nel progetto.  
  
2.  Nella **Casella degli strumenti**, espandere il nodo **Windows Workflow v3.0** e individuare l'attività **IfElse**.  
  
3.  Aggiungere questa attività al flusso di lavoro eseguendo una delle seguenti operazioni:  
  
    -   Aprire il menu di scelta rapida per l'attività **IfElse**, scegliere **Copy**, aprire il menu di scelta rapida per la riga sotto l'attività **onWorkflowActivated1** nella finestra di progettazione flussi di lavoro, quindi scegliere **Incolla**.  
  
    -   Trascinare l'attività **IfElse** dalla **Casella degli strumenti**, e connetterla con line sotto l'attività **onWorkflowActiviated1** nella finestra di progettazione flussi di lavoro.  
  
4.  Nella casella degli strumenti espandere il nodo **Flusso di lavoro di SharePoint** e individuare l'attività **CreateTask**.  
  
5.  Aggiungere questa attività al flusso di lavoro eseguendo una delle seguenti operazioni:  
  
    -   Aprire il menu di scelta rapida per l'attività **CreateTask**, scegliere **Copia**, aprire il menu di scelta rapida per una delle due aree **Rilascia attività qui** all'interno di IfElseActivity1 nella finestra di progettazione flussi di lavoro, quindi scegliere **Incolla**.  
  
    -   Trascinare l'attività **CreateTask** da **Casella degli strumenti** in una delle due aree **Rilascia attività qui** all'interno di IfElseActivity1.  
  
6.  Nella finestra **Proprietà** immettere un valore *taskToken* per la proprietà **CorrelationToken**  
  
7.  Espandere la proprietà **CorrelationToken** selezionando il segno più \(![Più di TreeView](~/sharepoint/media/plus.gif "Più di TreeView")\) accanto ad essa.  
  
8.  Scegliere la freccia a discesa della proprietà sottostante **OwnerActivityName** e impostare il valore *Workflow1*.  
  
9. Selezionare la proprietà **TaskId**, quindi selezionare il pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\) per visualizzare la finestra di dialogo **Associa proprietà**.  
  
10. Scegliere la scheda **Associazione a un nuovo membro**, scegliere il pulsante di opzione **Crea campo** quindi scegliere il pulsante **OK**.  
  
11. selezionare la proprietà **TaskProperties**, quindi selezionare il pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\) per visualizzare la finestra di dialogo **Associa proprietà**.  
  
12. Scegliere la scheda **Associazione a un nuovo membro**, scegliere il pulsante di opzione **Crea campo** quindi scegliere il pulsante **OK**.  
  
13. Nella **Casella degli strumenti**, espandere il nodo **Flusso di lavoro di SharePoint** e individuare l'attività **LogToHistoryListActivity**.  
  
14. Aggiungere questa attività al flusso di lavoro eseguendo una delle seguenti operazioni:  
  
    -   Aprire il menu di scelta rapida per l'attività **LogToHistoryListActivity**, scegliere **Copia**, aprire il menu di scelta rapida per l'altra area **Rilascia attività qui** all'interno di IfElseActivity1 nella finestra di progettazione flussi di lavoro, quindi scegliere **Incolla**.  
  
    -   Trascinare l'attività **LogToHistoryListActivity** da **Casella degli strumenti** e rilasciarla nell'altra area di **Attività qui** all'interno di IfElseActivity1.  
  
## Aggiunta di codice al flusso di lavoro  
 Aggiungere codice al flusso di lavoro per fornirvi la funzionalità.  
  
#### Per aggiungere codice al flusso di lavoro  
  
1.  Aprire il menu di scelta rapida per l'attività **createTask1** in Progettazione flussi di lavoro quindi scegliere **Visualizza codice**.  
  
2.  Aggiungere il seguente metodo :  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  Nel codice sostituire `somedomain\\someuser` con un dominio e un nome utente per i quali verrà creata un'attività, ad esempio "`Office\\JoeSch`".  Per il test è più semplice sfruttare l'account utilizzato per lo sviluppo.  
  
3.  Sotto il metodo `MethodInvoking` aggiungere l'esempio seguente:  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  In Progettazione flussi di lavoro selezionare l'attività **ifElseBranchActivity1**.  
  
5.  Nella finestra **Proprietà** selezionare la freccia a discesa della proprietà **Condizione** e quindi impostare il valore *Code Condition*.  
  
6.  Espandere la proprietà **Condizione** selezionando il segno più \(![Più di TreeView](~/sharepoint/media/plus.gif "Più di TreeView")\) accanto ad essa, quindi impostarne il valore su *checkApprovalNeeded*.  
  
7.  In Progettazione flussi di lavoro aprire il menu di scelta rapida per l'attività **logToHistoryListActivity1** e quindi selezionare **Genera gestori** per generare un metodo vuoto per l'evento `MethodInvoking`.  
  
8.  Sostituire il codice `MethodInvoking` con quanto segue:  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. Premere il tasto F5 per eseguire il debug del programma.  
  
     In questo modo l'applicazione viene compilata, assemblata, distribuita e ne vengono attivate le funzionalità; inoltre viene riciclato il pool di applicazioni [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)], quindi avviato il browser nel percorso specificato nella proprietà **URL sito**.  
  
## Associazione del flusso di lavoro all'elenco documenti  
 Visualizzare il form di associazione del flusso di lavoro associando il flusso di lavoro all'elenco **Documenticondivisi** sul sito di SharePoint.  
  
#### Per associare il flusso di lavoro  
  
1.  Selezionare il collegamento **Documenti condivisi** sulla barra Avvio veloce.  
  
2.  Selezionare il collegamento **Raccolta** sulla scheda **Strumenti raccolta** e quindi selezionare la barra multifunzione **Impostazioni raccolta**.  
  
3.  Nella sezione **Autorizzazioni e gestione** selezionare il collegamento **Impostazioni flusso di lavoro**, quindi selezionare il collegamento **Aggiungi flusso di lavoro** nella pagina **Flussi di lavoro**.  
  
4.  Nell'elenco di primo livello nella pagina delle impostazioni del flusso di lavoro, selezionare il modello **ExpenseReport \- Workflow1**.  
  
5.  Nel campo successivo, inserire ExpenseReportWorkflow, quindi selezionare il pulsante **Avanti**.  
  
     In questo modo il flusso di lavoro viene associato all'elenco **Documenti condivisi** e viene visualizzato il form di associazione del flusso di lavoro.  
  
6.  Nella casella di testo **Limite di auto approvazione** digitare 1200, quindi selezionare il pulsante **Associa flusso di lavoro**.  
  
## Avvio del flusso di lavoro  
 Associare il flusso di lavoro a uno dei documenti dell'elenco **Documenti condivisi** per visualizzare il form di avvio del flusso di lavoro.  
  
#### Per avviare il flusso di lavoro  
  
1.  Nella pagina SharePoint, selezionare il pulsante **Home**.  
  
2.  Scegliere il collegamento **Documenti condivisi** sulla barra Avvio Veloce per visualizzare l'elenco **Documenti condivisi**.  
  
3.  Selezionare il collegamento **Documenti** sulla scheda nella parte superiore della pagina **Strumenti raccolta** e quindi selezionare il pulsante **Carica documento** sulla barra multifunzione, per caricare un nuovo documento nell'elenco **Documenti condivisi**.  
  
4.  Nella finestra di dialogo **Carica documento**, scegliere il pulsante **Sfoglia**, scegliere qualsiasi file di documento, scegliere il pulsante **Apri** quindi scegliere il pulsante **OK**.  
  
     In questa finestra di dialogo è possibile modificare le impostazioni per il documento, tuttavia per il momento mantenere i valori predefiniti selezionando il pulsante **Salva**.  
  
5.  Scegliere il documento caricato, scegliere la freccia a discesa che viene visualizzata, quindi selezionare l'elemento **Flussi di lavoro**.  
  
6.  Selezionare l'immagine successiva a ExpenseReportWorkflow.  
  
     In questo modo viene visualizzato il form di avvio del flusso di lavoro. Notare che il valore visualizzato nella casella **Auto Approval Limit** è di sola lettura poiché è stato immesso nel form di associazione.  
  
7.  Nella casella di testo **Spese totali**, immettere 1600 e quindi scegliere il pulsante di **Avvia flusso di lavoro**.  
  
     In questo modo viene visualizzato nuovamente l'elenco **Documenti condivisi**.  Una nuova colonna denominata **ExpenseReportWorkflow** con il valore **Completato** viene aggiunta all'elemento appena avviato dal flusso di lavoro.  
  
8.  Selezionare la freccia a discesa accanto al documento caricato, quindi selezionare l'elemento **Flussi di lavoro** per visualizzare la pagina dello stato del flusso di lavoro.  Scegliere il valore **Completato** sotto **Flussi di lavoro completati**.  L'attività viene elencata sotto la sezione **Attività**.  
  
9. Selezionare il titolo dell'attività per visualizzarne i dettagli.  
  
10. Tornare all'elenco **Documenticondivisi** e riavviare il flusso di lavoro utilizzando lo stesso documento o uno diverso.  
  
11. Nella pagina di avvio immettere un importo minore o uguale a quello immesso nella pagina di associazione \(1200\).  
  
     In tal caso, nell'elenco della cronologia viene creata una voce anziché un'attività.  La voce viene visualizzata nella sezione **Cronologia flusso di lavoro** della pagina dello stato del flusso di lavoro.  Notare il messaggio nella colonna **Risultato** dell'evento di cronologia.  È contenuto il testo immesso nell'evento `logToHistoryListActivity1.MethodInvoking` in cui è incluso l'importo che è stato approvato automaticamente.  
  
## Passaggi successivi  
 Per ulteriori informazioni su come creare modelli di flusso di lavoro, vedere i seguenti argomenti:  
  
-   Per ulteriori informazioni sui flussi di lavoro SharePoint, vedere [Flussi di lavoro in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## Vedere anche  
 [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Procedura dettagliata: aggiungere una pagina dell'applicazione a un flusso di lavoro](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  