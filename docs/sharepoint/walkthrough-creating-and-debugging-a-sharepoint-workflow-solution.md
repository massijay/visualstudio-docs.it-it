---
title: "Procedura dettagliata: creazione e debug di una soluzione flusso di lavoro SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Workflow.WorkflowConditions"
  - "VS.SharePointTools.Workflow.WorkflowList"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, flussi di lavoro"
  - "flussi di lavoro [sviluppo per SharePoint in Visual Studio]"
ms.assetid: 81756490-ab5a-4fa4-96c6-eed2cfbf8374
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura dettagliata: creazione e debug di una soluzione flusso di lavoro SharePoint
  In questa procedura dettagliata viene illustrato come creare un modello di base di flusso di lavoro sequenziale.  Il flusso di lavoro controlla una proprietà di una raccolta documenti condivisa per determinare se un documento è stato rivisto.  In caso positivo, il flusso di lavoro viene terminato.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto flusso di lavoro sequenziale per la definizione dell'elenco di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Creazione di attività del flusso di lavoro.  
  
-   Gestione degli eventi di attività del flusso di lavoro.  
  
> [!NOTE]  
>  Sebbene in questa procedura dettagliata venga utilizzato un progetto flusso di lavoro sequenziale, il processo è identico per un progetto flusso di lavoro macchina a stati.  
>   
>  Inoltre, sul computer potrebbero essere visualizzati nomi o percorsi diversi per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti.  Questi elementi sono determinati dall'edizione di Visual Studio in uso e dalle impostazioni utilizzate.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## Aggiunta di proprietà alla raccolta Documenti condivisi di SharePoint  
 Per tenere traccia dello stato di revisione dei documenti nella raccolta **Documenti condivisi**, saranno create tre nuove proprietà per i documenti condivisi nel sito di SharePoint: `Status`, `Assignee` e `Review Comments`.  Tali proprietà sono definite nella raccolta **Documenti condivisi**.  
  
#### Per aggiungere proprietà alla raccolta Documenti condivisi di SharePoint  
  
1.  Aprire un sito SharePoint, ad esempio http:\/\/\<nome del sistema\>\/SitePages\/Home.aspx, in un browser.  
  
2.  Nella barra Avvio veloce, scegliere **CondivisiDocumenti**.  
  
3.  Selezionare **Raccolta** sulla barra multifunzione **Strumenti raccolta**, quindi selezionare il pulsante **Crea colonna** sulla barra multifunzione per creare una nuova colonna.  
  
4.  Assegnare un nome alla colonna Stato documento, impostarne il tipo su **Scelta \(menu in cui eseguire una selezione\)**, specificare le tre scelte seguenti, quindi selezionare il pulsante **OK**:  
  
    -   **Review Needed**  
  
    -   **Review Complete**  
  
    -   **Changes Requested**  
  
5.  Creare altre due colonne e denominarle Assignee e Review Comments.  Impostare il tipo della colonna Assignee come singola riga di testo e il tipo della colonna Review Comments come più righe di testo.  
  
## Possibilità di modifica dei documenti senza necessità di estrazione  
 Il test del modello di flusso di lavoro risulta più facile quando è possibile modificare i documenti senza doverli estrarre.  Nella procedura descritta di seguito, viene configurato il sito di SharePoint per consentirne l'attivazione.  
  
#### Per consentire la modifica dei documenti senza estrazione  
  
1.  Sulla barra Avvio veloce, selezionare il collegamento **Documenti condivisi**.  
  
2.  Sulla barra multifunzione **Raccolta**, scegliere la scheda **Strumenti raccolta**, quindi selezionare il pulsante **Impostazioni raccolta** per visualizzare la pagina **Impostazioni raccolta documenti**.  
  
3.  Nella sezione **Impostazioni generali**, scegliere il collegamento **Impostazioni controllo versioni** per visualizzare la pagina **Impostazioni controllo versioni**.  
  
4.  Verificare che l'impostazione per **Estrazione obbligatoria dei documenti prima della modifica** sia **No**.  Se non lo è, modificarlo su **No** e quindi selezionare il pulsante **OK**.  
  
5.  Chiudere il browser.  
  
## Creazione di un progetto Flusso di lavoro sequenziale SharePoint  
 Un flusso di lavoro sequenziale è un set di passaggi eseguiti in ordine fino al completamento dell'ultima attività.  In questa procedura si crea un flusso di lavoro sequenziale che verrà applicato all'elenco Documenti condivisi.  La procedura guidata del flusso di lavoro consente di associare quest'ultimo alla definizione di sito o alla definizione di elenco, nonché di determinare quando verrà avviato.  
  
#### Per creare un progetto Flusso di lavoro sequenziale SharePoint  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Sulla barra dei menu scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  
  
3.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
4.  Nel riquadro **Modelli**, scegliere il modello **Progetto SharePoint 2010**.  
  
5.  Nella casella di testo **Nome**, inserire MySharePointWorkflow e selezionare il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
6.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug**, scegliere il pulsante di opzione **Distribuisci come soluzione farm**, quindi selezionare il pulsante **Fine** per accettare il livello di affidabilità e il sito predefinito.  
  
     Questo passaggio consente di impostare il livello di attendibilità per la soluzione come soluzione della farm, ovvero l'unica opzione disponibile per i progetti flusso di lavoro.  Per ulteriori informazioni, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  In **Esplora soluzioni** scegliere il nodo del progetto, quindi, nella barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
8.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
9. Nel riquadro **Modelli**, scegliere il modello **Flusso di lavoro sequenziale \(solo soluzione farm\)** quindi scegliere il pulsante **Aggiungi**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
10. Nella pagina **Specificare il nome del flusso di lavoro per il debug** accettare il nome predefinito \(**MySharePointWorkflow \- Workflow1**\).  Mantenere il valore predefinito **Flusso di lavoro elenco** del tipo di modello di flusso di lavoro, quindi selezionare il pulsante **Avanti**.  
  
11. Nella pagina **Associare automaticamente il flusso di lavoro in una sessione di debug** selezionare il pulsante **Avanti** per accettare tutte le impostazioni predefinite.  
  
     Questo passaggio consente di associare automaticamente il flusso di lavoro alla raccolta Documenti condivisi.  
  
12. Nella pagina **Specificare le condizioni relative alle modalità di avvio del flusso di lavoro** lasciare le opzioni predefinite selezionate nella sezione **Selezionare la modalità di avvio del flusso di lavoro** e selezionare il pulsante **Fine**.  
  
     Questa pagina consente di specificare quando viene avviato il flusso di lavoro.  Per impostazione predefinita, il flusso di lavoro si avvia quando un utente lo avvia manualmente in SharePoint o quando viene creato un elemento al quale è associato il flusso di lavoro.  
  
## Creazione di attività del flusso di lavoro  
 Nei flussi di lavoro sono contenute una o più *attività* che rappresentano le azioni da effettuare.  Utilizzare Progettazione flussi di lavoro per organizzare le attività per un flusso di lavoro.  In questa procedura verranno aggiunte due attività al flusso di lavoro: HandleExternalEventActivity e OnWorkFlowItemChanged.  Queste attività consentono di monitorare lo stato di revisione dei documenti nell'elenco **Documenti condivisi**  
  
#### Per creare attività del flusso di lavoro  
  
1.  Il flusso di lavoro deve essere visualizzato in Progettazione flussi di lavoro.  In caso contrario, allora aprire **Workflow1.cs** o **Workflow1.vb** in **Esplora soluzioni**.  
  
2.  Nella finestra di progettazione, selezionare l'attività **OnWorkflowActivated1**.  
  
3.  Nella finestra **Proprietà** inserire onWorkflowActivated accanto alla proprietà **Invoked**, quindi premere il tasto Invio.  
  
     Viene aperto l'editor del codice e un metodo per la gestione eventi denominato onWorkflowActivated viene aggiunto al file di codice Workflow1.  
  
4.  Tornare a Progettazione flussi di lavoro, aprire la casella degli strumenti, quindi espandere il nodo **Windows Workflow v3.0**.  
  
5.  Nel nodo **Windows Workflow v3.0** della **Casella degli strumenti**, eseguire una delle seguenti procedure:  
  
    1.  Aprire il menu di scelta rapida per l'attività **While**, quindi scegliere **Copia**.  In Progettazione flussi di lavoro, aprire il menu di scelta rapida per la riga sottostante l'attività **onWorkflowActivated1** quindi scegliere **Incolla**.  
  
    2.  Trascinare l'attività **While** dalla **Casella degli strumenti** alla Progettazione flussi di lavoro e connetterla con la riga sottostante l'attività **onWorkflowActivated1**.  
  
6.  Scegliere l'attività **WhileActivity1**.  
  
7.  Nella finestra **Proprietà** impostare **Condition** sulla condizione relativa al codice.  
  
8.  Espandere la proprietà **Condition** inserire isWorkflowPending accanto alla proprietà figlia **Condition**, quindi premere il tasto Invio.  
  
     Viene aperto l'editor di codice e un metodo denominato isWorkflowPending viene aggiunto al file di codice Workflow1.  
  
9. Tornare a Progettazione flussi di lavoro, aprire la casella degli strumenti, quindi espandere il nodo **Flusso di lavoro di SharePoint**.  
  
10. Nel nodo **SharePoint Workflow** della **Casella degli strumenti**, eseguire una delle seguenti procedure:  
  
    -   Aprire il menu di scelta rapida per l'attività **OnWorkflowItemChanged** quindi scegliere **Copia**.  In Progettazione flussi di lavoro, aprire il menu di scelta rapida per la riga interna all'attività **onWorkflowActivated1** quindi scegliere **Incolla**.  
  
    -   Trascinare un'attività **OnWorkflowItemChanged** dalla **Casella degli strumenti** alla Progettazione flussi di lavoro e connetterla con la riga interna all'attività **whileActivity1**.  
  
11. Scegliere l'attività **onWorkflowItemChanged1**.  
  
12. Nella finestra **Proprietà** impostare le proprietà come mostrato nella tabella riportata di seguito.  
  
    |Proprietà|Valore|  
    |---------------|------------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Invoked**|**onWorkflowItemChanged**|  
  
## Gestione degli eventi di attività  
 Infine, controllare lo stato del documento di ogni attività.  Se il documento è stato rivisto, il flusso di lavoro è terminato.  
  
#### Per gestire gli eventi di attività  
  
1.  In Workflow1.cs o Workflow1.vb aggiungere il campo seguente nella parte superiore della classe `Workflow1`.  Questo campo viene utilizzato in un'attività per determinare se il flusso di lavoro è terminato.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Aggiungere il seguente metodo alla classe `Workflow1`.  Questo metodo controlla il valore della proprietà `Document Status` dell'elenco Documenti per determinare se il documento è stato rivisto.  Se la proprietà `Document Status` è impostata su `Review Complete`, il metodo `checkStatus` imposta il campo `workflowPending` su **false** per indicare che il flusso di lavoro è pronto per essere terminato.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Aggiungere il codice riportato di seguito ai metodi `onWorkflowActivated` e `onWorkflowItemChanged` per chiamare il metodo `checkStatus`.  Quando viene avviato il flusso di lavoro, il metodo `onWorkflowActivated` chiama il metodo `checkStatus` per determinare se il documento è già stato rivisto.  In caso negativo, il flusso di lavoro continua.  Quando il documento viene salvato, il metodo `onWorkflowItemChanged` chiama nuovamente il metodo `checkStatus` per determinare se il documento è stato rivisto.  Finché il campo `workflowPending` è impostato su **true**, l'esecuzione del flusso di lavoro continua.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Aggiungere il codice riportato di seguito al metodo `isWorkflowPending` per controllare lo stato della proprietà `workflowPending`.  Ogni volta che il documento viene salvato, l'attività **whileActivity1** chiama il metodo `isWorkflowPending`.  Questo metodo esamina la proprietà <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> dell'oggetto <xref:System.Workflow.Activities.ConditionalEventArgs> per determinare se l'attività **WhileActivity1** deve continuare o essere terminata.  Se la proprietà è impostata su **true**, l'attività continua.  In caso contrario, l'attività e il flusso di lavoro vengono terminati.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Salvare il progetto.  
  
## Test del modello di flusso di lavoro SharePoint  
 Quando si avvia il debugger, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente la distribuzione del modello di flusso di lavoro al server SharePoint e di associare il flusso di lavoro all'elenco **Documenti condivisi**.  Per testare il flusso di lavoro, avviare una relativa istanza da un documento dell'elenco **Documenti condivisi**.  
  
#### Per testare il modello di flusso di lavoro SharePoint  
  
1.  In Workflow1.cs o Workflow1.vb impostare un punto di interruzione accanto al metodo **onWorkflowActivated**.  
  
2.  Premere il tasto F5 per compilare ed eseguire la soluzione.  
  
     Verrà aperto il sito di SharePoint.  
  
3.  Nel riquadro di navigazione di SharePoint selezionare il collegamento **Documenti**.  
  
4.  Nella pagina **Documenti condivisi** selezionare il collegamento **Documenti** nella scheda **Strumenti raccolta**, quindi selezionare il pulsante **Carica documento**.  
  
5.  Nella finestra di dialogo **Carica documento**, scegliere il pulsante **Sfoglia**, scegliere qualsiasi file di documento, scegliere il pulsante **Apri** quindi scegliere il pulsante **OK**.  
  
     In questo modo viene caricato il documento selezionato nell'elenco **Documenti condivisi** e avviato il flusso di lavoro.  
  
6.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verificare che l'esecuzione del debugger venga interrotta in corrispondenza del punto di interruzione accanto al metodo `onWorkflowActivated`.  
  
7.  Premere il tasto F5 per continuare l'esecuzione.  
  
8.  In questa fase è possibile modificare le impostazioni per il documento, tuttavia per il momento mantenere i valori predefiniti selezionando il pulsante **Salva**.  
  
     In questo modo si torna alla pagina **Documenti condivisi** del sito Web predefinito di SharePoint.  
  
9. Nella pagina **Documenti condivisi** verificare che il valore sottostante la colonna **MySharePointWorkflow – Workflow1** sia impostato su **In corso**.  Questa impostazione indica che il flusso di lavoro è in corso e che il documento è in attesa di revisione.  
  
10. Nella pagina **Documenti condivisi**, scegliere il documento, scegliere la freccia visualizzata quindi selezionare la voce del menu **Modifica proprietà**.  
  
11. Impostare **Stato documento** su **Revisione completata**, quindi selezionare il pulsante **Salva**.  
  
     In questo modo si torna alla pagina **Documenti condivisi** del sito Web predefinito di SharePoint.  
  
12. Nella pagina **Documenti condivisi** verificare che il valore sottostante la colonna **Document Status** sia impostato su **Revisione completata**.  Aggiornare la pagina **Documenti condivisi** e verificare che il valore sottostante la colonna **MySharePointWorkflow – Workflow1** sia impostato su **Completato**.  Questa impostazione indica che il flusso di lavoro è stato completato e che il documento è stato rivisto.  
  
## Passaggi successivi  
 Per ulteriori informazioni su come creare modelli di flusso di lavoro, vedere i seguenti argomenti:  
  
-   Per ulteriori informazioni sulle attività del flusso di lavoro SharePoint, vedere l'argomento relativo alle [Attività di flusso di lavoro per SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Per ulteriori informazioni sulle attività di Windows Workflow Foundation, vedere l'argomento relativo allo [System.Workflow.Activities Namespace](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## Vedere anche  
 [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  