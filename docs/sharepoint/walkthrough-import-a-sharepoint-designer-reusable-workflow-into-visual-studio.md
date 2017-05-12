---
title: "Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio"
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
  - "VS.SharePointTools.WSPImport.ImportWF"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, importazione di flussi di lavoro riutilizzabili"
  - "flussi di lavoro riutilizzabili [sviluppo per SharePoint in Visual Studio]"
ms.assetid: a6550615-4433-4aba-8bdf-0fcbf8dbcf97
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio
  In questa procedura dettagliata viene illustrato come importare un flusso di lavoro riutilizzabile creato in SharePoint Designer 2010 in un progetto flusso di lavoro di SharePoint per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 I flussi di lavoro creati in SharePoint Designer, o *flussi di lavoro dichiarativi*, sono costituiti da istruzioni [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] anziché codice.  SharePoint Designer 2010 introduce i *flussi di lavoro riutilizzabili*, ovvero flussi di lavoro portabili e dichiarativi che possono essere utilizzati in diversi elenchi dei siti di SharePoint.  
  
 I flussi di lavoro creati in [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], come ad esempio i flussi di lavoro sequenziali e la macchine a stati, vengono definiti *flussi di lavoro di codice*.  Questi ultimi sono costituiti da file XML e da moduli di codice nei quali gli utenti possono personalizzare il comportamento del flusso di lavoro.  
  
 Visual Studio consente di importare i flussi di lavoro riutilizzabili creati in SharePoint Designer 2010 e di convertirli in flussi di lavoro di codice per utilizzarli nei siti di SharePoint.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un flusso di lavoro semplice, riutilizzabile in SharePoint Designer.  
  
-   Esportazione del flusso di lavoro riutilizzabile di SharePoint Designer in un file con estensione wsp e in SharePoint.  
  
-   Importazione del file con estensione wsp in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite il progetto di importazione del flusso di lavoro riutilizzabile.  
  
-   Modifica del flusso di lavoro tramite l'aggiunta di codice.  
  
-   Utilizzo del flusso di lavoro importato in un sito di SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## Creare siti secondari di destinazione di SharePoint  
 Innanzitutto si creano due nuovi siti secondari di SharePoint: uno per ospitare i flussi di lavoro riutilizzabili da SharePoint Designer e un altro per ospitare i flussi di lavoro convertiti.  
  
#### Per creare i siti secondari di SharePoint  
  
1.  In SharePoint Designer 2010, nella barra dei menu, scegliere **File**, **Nuovo sito Web vuoto**.  
  
2.  Nella finestra di dialogo **Nuovo sito Web vuoto**, passare da un sito di SharePoint in cui si desidera creare il flusso di lavoro o utilizzare il valore predefinito http:\/\/*SystemName*\/ e quindi selezionare il pulsante **OK**.  
  
     Verrà visualizzata la home page.  
  
3.  Nella sezione **Sotto siti**, scegliere il pulsante di **Nuovo**.  
  
4.  Nella finestra di dialogo **Nuovo**, scegliere **Modelli di SharePoint** dall'elenco nel riquadro a sinistra e scegliere **Sito team** dall'elenco nel riquadro di destra.  
  
5.  Nella casella **Specificare l'indirizzo del sito Web** sostituire la parola **sito secondario** nell'URL con SPD1, quindi selezionare il pulsante **OK**.  
  
     Questa operazione comporta l'apertura del nuovo sito secondario in SharePoint Designer.  Chiudere questa istanza di SharePoint Designer e tornare alla prima istanza \(sito principale\).  
  
6.  Ripetere i passaggi da 3 a 5 per creare il secondo sito secondario, questa volta sostituendo la parola **sito secondario** nell'[!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con SPD2.  
  
## Creare un flusso di lavoro riutilizzabile in SharePoint Designer  
 Poiché in SharePoint non è incluso alcun flusso di lavoro riutilizzabile che è possibile utilizzare per questo esempio, se ne creerà uno.  In questo semplice flusso di lavoro, quando un utente immette una nuova attività con un titolo specifico nell'apposito elenco, l'attività viene assegnata a tale utente.  
  
#### Per creare un flusso di lavoro riutilizzabile in SharePoint Designer  
  
1.  Nella sezione **Sito secondario**, scegliere il sito **SPD1** per modificarlo.  
  
2.  Sulla barra multifunzione, fare clic sul pulsante **Flusso di lavoro riutilizzabile**.  
  
     Viene visualizzata la Creazione guidata flusso di lavoro riutilizzabile.  
  
3.  Nella casella **Nome**, inserire SPD Task Workflow.  
  
4.  Nell'elenco **Tipo di contenuto**, scegliere **Attività**, quindi scegliere il pulsante **OK**.  
  
     Il flusso di lavoro viene aperto in Progettazione flussi di lavoro di SharePoint Designer.  
  
5.  In Progettazione flussi di lavoro, scegliere il punto 1 sulla barra multifunzione, quindi scegliere il pulsante **Condizione**.  
  
6.  Nell'elenco delle condizioni, scegliere **Se il campo dell'elemento corrente equivale al valore**.  
  
     Questo passaggio aggiunge una condizione denominata **Se il campo equivale al valore**.  
  
7.  Nella condizione **Se il campo equivale al valore**, scegliere il collegamento **campo**.  
  
8.  Nell'elenco dei valori, selezionare **Title**.  
  
9. Nella conduzione **Se il campo equivale al valore**, scegliere il collegamento **valore**.  
  
10. Nella casella immettere Nuova attività.  
  
     L'istruzione della condizione è ora **Se Elemento corrente:Titolo è uguale a Nuova attività**.  
  
11. Scegliere la riga sotto l'istruzione della condizione, quindi sulla barra multifunzione, fare clic sul pulsante **Azione**.  
  
12. Nell'elenco di azioni, scegliere **Imposta campo nell'elemento corrente**.  
  
13. Nell'azione **Imposta campo su valore**, scegliere il collegamento **campo**, nell'elenco, quindi scegliere **Assegnato a**.  
  
14. In azione di **Imposta campo su valore**, scegliere il collegamento **valore** quindi, nell'elenco degli utenti esistenti e gruppi, scegliere **Utente che ha creato l'elemento**.  
  
15. Scegliere il pulsante **Aggiungi**, quindi fare clic sul pulsante **OK**.  
  
     L'istruzione dell'azione è ora **Imposta Assegnato a su Elemento corrente:CreatedBy**.  
  
## Salvataggio e distribuzione del flusso di lavoro riutilizzabile  
 Dato che [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] può importare solo file con estensione wsp, è necessario salvare il flusso di lavoro riutilizzabile come file con estensione wsp e distribuirlo su SharePoint prima di importarlo in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Se durante l'esecuzione della procedura seguente si riceve un errore di runtime è necessario eseguirla su un sistema che dispone dell'accesso al sito di SharePoint.  
  
#### Per salvare e distribuire il flusso di lavoro riutilizzabile  
  
1.  Nella parte superiore del SharePoint Designer, selezionare il pulsante **Salva** per salvare lo stato di avanzamento, quindi selezionare il pulsante **Pubblica** per distribuire il flusso di lavoro al sito SharePoint **SPD1**.  
  
2.  Nel riquadro di navigazione, selezionare l'oggetto **Flussi di lavoro**.  
  
3.  Sotto il **Flusso di lavoro riutilizzabile**, scegliere **SPD Task Workflow**.  
  
4.  Sulla barra multifunzione, selezionare il pulsante **Salva come modello** per salvare il flusso di lavoro come file con estensione .wsp.  
  
5.  Aprire il sito di SharePoint **SPD1** in un browser per visualizzare il file con estensione wsp in SharePoint.  
  
6.  Nella barra Avvio Veloce, scegliere il collegamento **Raccolte**.  
  
7.  Nella sezione **Raccolte documenti**, selezionare il collegamento **Risorse del sito**.  
  
     Il file di **SPD Task Workflow** viene elencato con altre risorse del sito.  
  
8.  Nell'elenco di file, scegliere il nome del file  
  
9. Nella finestra di dialogo **Download file**, selezionare il pulsante **Salva** per salvare il file con estensione .wsp nel sistema locale.  
  
## Importare il file con estensione wsp in Visual Studio  
 Importare il file con estensione wsp in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tramite un progetto di importazione del flusso di lavoro riutilizzabile.  Questo progetto consente di convertire il flusso di lavoro da riutilizzabile e dichiarativo a flusso di lavoro di codice.  Una volta convertito il flusso di lavoro, si utilizzerà il codice per modificarne il comportamento.  
  
#### Per importare un flusso di lavoro da un file con estensione wsp e modificarlo  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sulla barra dei menu, selezionare **File**, **Nuovo**, **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Nel riquadro **Modelli**, scegliere il modello **Importa flusso di lavoro riutilizzabile SharePoint 2010**, lasciare il nome del progetto come **WorkflowImportProject1**, quindi scegliere il pulsante **OK**.  
  
     Viene visualizzata la Personalizzazione guidata SharePoint.  
  
4.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] per il secondo sito secondario di SharePoint creato precedentemente: http:\/\/*system name*\/SPD2.  
  
5.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint**, scegliere il pulsante di opzione **Distribuisci come soluzione farm** e quindi selezionare il pulsante **Avanti**.  
  
     Per ulteriori informazioni sulle differenze tra le soluzioni create mediante sandbox e quelle della farm, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Nella pagina **Specificare l'origine del nuovo progetto** individuare il percorso nel sistema in cui è stato precedentemente salvato il file con estensione .wsp, quindi selezionare il pulsante **Avanti**.  
  
    > [!NOTE]  
    >  Scegliere il pulsante **Fine** per importare tutti gli elementi disponibili nel file con estensione .wsp.  
  
     Viene visualizzato un elenco di flussi di lavoro riutilizzabili disponibili per l'importazione.  
  
7.  Nella casella **Selezionare gli elementi da importare**, selezionare il flusso di lavoro **SPD Workflow Test**, quindi selezionare il pulsante **Fine**.  
  
     Una volta terminata l'operazione di importazione, viene creato un progetto denominato **WorkflowImportProject1** in cui è contenuto un flusso di lavoro denominato **SPD\_Workflow\_TestFT**.  In questa cartella sono presenti il file di definizione del flusso di lavoro Elements.xml e il file di Progettazione flusso di lavoro \(con estensione xoml\).  Nella finestra di progettazione sono contenuti due file: il file di regole \(con estensione rules\) e il file code\-behind \(con estensione cs o vb a seconda del linguaggio di programmazione del progetto\).  
  
8.  In **Esplora soluzioni**, eliminare la cartella **Altri file importati**.  
  
9. Nel file Elements.xml, eliminare `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. In **Esplora soluzioni**, scegliere **WorkflowImportProject1** quindi, nella barra dei menu, scegliere **Progetto**, **Imposta come progetto di avvio** per impostare **WorkflowImportProject1** come elemento di avvio.  
  
     In questo modo l'elenco verrà immediatamente visualizzato quando si esegue il debug del progetto.  
  
11. Poiché mediante il modello **Importa flusso di lavoro riutilizzabile SharePoint 2010** non vengono importati i valori delle proprietà di associazione per il flusso di lavoro importato, è necessario immetterli.  Per eseguire questa operazione, seguire la procedura seguente:  
  
    1.  In **Esplora soluzioni** scegliere il nodo del progetto **SPD\_Workflow\_TestFT**.  
  
    2.  Scegliere il pulsante con i puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.png "Ellisse di ASP.NET Mobile Designer")\) accanto alla proprietà dell'elenco, come ad esempio la proprietà **Elenco di destinazione**.  
  
    3.  Compilare i valori mancanti nella personalizzazione guidata SharePoint e quindi scegliere il pulsante **Fine**.  
  
12. Scegliere il file con estensione .xoml e successivamente, nella barra dei menu, scegliere **Visualizza**, **Finestra di progettazione** per visualizzare il flusso di lavoro importato in Progettazione flussi di lavoro.  
  
13. Nel nodo **Windows Workflow v3.0** della **Casella degli strumenti**, eseguire una delle seguenti procedure:  
  
    -   Aprire il menu di scelta rapida per l'attività **Code**, quindi scegliere **Copia**.  In Progettazione flussi di lavoro, aprire il menu di scelta rapida per la riga sottostante l'attività **SequenceActivity1** quindi scegliere **Incolla**.  
  
    -   Trascinare l'attività **Codice** da **Casella degli strumenti** a Progettazione flussi di lavoro e connetterla alla riga sottostante l'attività **SequenceActivity1**.  
  
     In questo modo viene aggiunta un'attività denominata **CodeActivity1** a Progettazione flussi di lavoro.  In questa attività si aggiungerà un'azione codice che consente di creare un annuncio nel relativo elenco quando l'utente avvia il flusso di lavoro.  
  
14. Eseguire una delle procedure seguenti:  
  
    -   Fare doppio clic su **CodeActivity1** per generare un gestore eventi e visualizzare il codice.  
  
    -   Nella finestra **Proprietà** per **CodeActivity1**, impostare il valore della proprietà **ExecuteCode** a **codeActivity\_ExecuteCode**.  
  
15. Aggiungere quanto segue per le istruzioni **using** o **Imports** esistenti:  
  
     [!code-csharp[SP_SPDWFImport#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Sostituire `codeActivity1_ExecuteCode` con l'istruzione seguente:  
  
     [!code-csharp[SP_SPDWFImport#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_spdwfimport/cs/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_spdwfimport/vb/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## Distribuire il progetto e associare il flusso di lavoro  
 Eseguire il progetto WorkflowImportProject1 per distribuirlo in un sito di SharePoint, quindi associare il flusso di lavoro all'elenco Attività per visualizzare e testare il flusso di lavoro modificato e convertito.  
  
#### Per distribuire il progetto e associare il flusso di lavoro  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] premere il tasto F5 per eseguire e distribuire il progetto flusso di lavoro convertito.  
  
2.  Nella barra Avvio veloce, scegliere il collegamento **Attività** per visualizzare l'elenco Attività.  
  
3.  Nella scheda **Strumenti elenco**, scegliere il pulsante **Elementi** quindi scegliere il pulsante **Nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Attività \- Nuovo elemento**.  
  
4.  Nella casella **Titolo** inserire la Nuova attività, quindi scegliere il pulsante **Salva**.  
  
5.  Nella scheda di **Strumenti elenco**, scegliere il pulsante **Elenco** quindi scegliere il pulsante **Impostazioni elenco**.  
  
     La pagina **Impostazioni elenco** viene visualizzata.  
  
6.  Nella sezione **Autorizzazioni e gestione**, selezionare il collegamento **Impostazioni flusso di lavoro**.  
  
     Viene visualizzata la pagina **Impostazioni flusso di lavoro**.  
  
7.  Scegliere il collegamento **Aggiungi un flusso di lavoro**.  
  
8.  Nell'elenco **Flusso di lavoro** scegliere **WorkflowImportProject1 \- SPD Workflow Test**.  
  
9. Nella casella **Nome** immettere SPD Workflow Test, quindi selezionare il pulsante **OK**.  
  
10. Nella barra Avvio Veloce, scegliere l'elenco **Attività**.  
  
11. Scegliere la freccia accanto a **Nuova attività** quindi, nell'elenco, scegliere **Flussi di lavoro**.  
  
12. Nella sezione **Avvio di un nuovo flusso di lavoro**, selezionare il collegamento per **SPD Workflow Test**, quindi selezionare il pulsante **Start** per inizializzare il flusso di lavoro.  
  
    > [!NOTE]  
    >  In alternativa, è possibile associare automaticamente un flusso di lavoro a un elenco eseguendo l'impostazione guidata del flusso di lavoro e impostando per quest'ultimo l'associazione automatica.  
  
     Notare che vengono eseguite due azioni dal flusso di lavoro: il nome viene visualizzato nella colonna **Assegnato a** dell'attività e nell'elenco **Annunci** viene visualizzato un annuncio.  
  
## Vedere anche  
 [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Creazione di controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  