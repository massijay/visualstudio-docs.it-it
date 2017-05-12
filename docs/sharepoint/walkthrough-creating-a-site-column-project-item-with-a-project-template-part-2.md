---
title: "Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elementi di progetto [sviluppo per SharePoint in Visual Studio], creazione di creazioni guidate di modelli"
  - "elementi di progetto SharePoint, creazione di creazioni guidate di modelli"
  - "sviluppo per SharePoint in Visual Studio, definizione di nuovi tipi di elemento di progetto"
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2
  Dopo avere definito un tipo di elemento di progetto SharePoint personalizzato e averlo associato a un modello di progetto in Visual Studio, è anche possibile fornire una procedura guidata per il modello.  È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando utilizzano il modello per creare un nuovo progetto contenente l'elemento di progetto.  Le informazioni raccolte possono essere utilizzate per inizializzare l'elemento di progetto.  
  
 In questa procedura dettagliata verrà aggiunta una procedura guidata al modello di progetto Site Column illustrato in [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  Quando un utente crea un progetto Site Column, tramite la procedura guidata vengono raccolte informazioni sulla colonna del sito \(ad esempio il tipo di base e il gruppo\) e queste informazioni vengono aggiunte al file Elements.xml nel nuovo progetto.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di progetto.  
  
-   Definizione di un'interfaccia utente della procedura guidata personalizzata simile a quella delle procedure guidate predefinite per i progetti SharePoint in Visual Studio .  
  
-   Creazione di due *comandi di SharePoint* utilizzati per una chiamata nel sito di SharePoint locale durante l'esecuzione della procedura guidata.  I comandi di SharePoint sono metodi che possono essere utilizzati dalle estensioni di Visual Studio per chiamare le API nel modello a oggetti del server SharePoint.  Per ulteriori informazioni, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Utilizzo di parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.  
  
-   Creazione di un nuovo file con estensione snk in ogni nuova istanza di progetto Site Column.  Questo file viene utilizzato per firmare l'output del progetto in modo che l'assembly della soluzione SharePoint possa essere distribuito nella Global Assembly Cache.  
  
-   Debug e test della procedura guidata.  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, il codice e altri file di questa procedura dettagliata all'indirizzo seguente:  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Prerequisiti  
 Per eseguire questa procedura dettagliata, è prima necessario creare la soluzione SiteColumnProjectItem completando quanto descritto in [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Per completare la procedura dettagliata, nel computer di sviluppo devono inoltre essere disponibili i componenti seguenti:  
  
-   Edizioni supportate di Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Il Visual Studio SDK.  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'elemento di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Procedure guidate per modelli di progetto e di elemento in Visual Studio.  Per ulteriori informazioni, vedere [Procedura: utilizzare procedure guidate con modelli di progetto](~/extensibility/how-to-use-wizards-with-project-templates.md) e l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
-   Colonne del sito in SharePoint.  Per ulteriori informazioni, vedere [Colonne](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a> Informazioni sui componenti della procedura guidata  
 La procedura guidata dimostrata in questa procedura dettagliata contiene diversi componenti.  Tali componenti sono descritti nella tabella seguente.  
  
|Componente|Descrizione|  
|----------------|-----------------|  
|Implementazione della procedura guidata|Si tratta di una classe, denominata `SiteColumnProjectWizard`, che implementa l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Questa interfaccia definisce i metodi chiamati da Visual Studio all'avvio e al termine della procedura guidata e in determinati momenti durante l'esecuzione.|  
|Interfaccia utente della creazione guidata|Si tratta di una finestra basata su WPF, denominata `WizardWindow`.  Questa finestra comprende due controlli utente, denominati `Page1` e `Page2`.  Tali controlli utente rappresentano le due pagine della procedura guidata.<br /><br /> In questa procedura dettagliata, il metodo <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> dell'implementazione della procedura guidata ne visualizza l'interfaccia utente.|  
|Modello dati della procedura guidata|Si tratta di una classe intermedia, denominata `SiteColumnWizardModel`, che fornisce un livello tra l'interfaccia utente e l'implementazione della procedura guidata.  Questo esempio utilizza tale classe per consentire la separazione dell'implementazione e dell'interfaccia utente; la classe non è un componente richiesto di tutte le procedure guidate.<br /><br /> In questa procedura dettagliata, l'implementazione della procedura guidata passa un oggetto `SiteColumnWizardModel` alla finestra della procedura guidata quando viene visualizzata la relativa interfaccia utente.  Nell'interfaccia utente della procedura guidata vengono utilizzati i metodi di questo oggetto per salvare i valori dei controlli nell'interfaccia utente e per effettuare operazioni quali la verifica della validità dell'URL del sito di input.  Al termine della proceduta guidata da parte dell'utente, l'implementazione della procedura utilizza l'oggetto `SiteColumnWizardModel` per determinare lo stato finale dell'interfaccia utente.|  
|Responsabile firmatario del progetto|Si tratta di una classe di supporto, denominata `ProjectSigningManager`, utilizzata dall'implementazione della procedura guidata per creare un nuovo file key.snk in ciascuna nuova istanza del progetto.|  
|Comandi di SharePoint|Si tratta dei metodi utilizzati dal modello dati della procedura guidata per effettuare chiamate nel sito di SharePoint locale durante l'esecuzione della procedura guidata.  Poiché i comandi di SharePoint devono essere destinati a .NET Framework 3.5, questi comandi vengono implementati in un assembly diverso dal resto del codice della procedura guidata.|  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata, è necessario aggiungere diversi progetti alla soluzione SiteColumnProjectItem creata in [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
-   Un progetto WPF.  È quindi necessario implementare l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> e definire l'interfaccia utente della procedura guidata in questo progetto.  
  
-   Un progetto Libreria di classi che definisce i comandi di SharePoint.  Questo progetto deve essere destinato a .NET Framework 3.5.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto WPF  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], aprire la soluzione SiteColumnProjectItem.  
  
2.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione **SiteColumnProjectItem**, scegliere **Aggiungi** e quindi scegliere **Nuovo Progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic il nodo della soluzione viene visualizzato solo quando la casella di controllo **Mostra sempre soluzione** è selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
3.  Nella parte superiore della finestra di dialogo **Aggiungi nuovo progetto**, assicurarsi che **.NET Framework 4.5** sia selezionato nell'elenco delle versioni di.NET Framework.  
  
4.  Espandere il nodo **Visual C\#** o il nodo **Visual Basic** e selezionare il nodo **Windows**.  
  
5.  Nell'elenco dei modelli di progetto, scegliere **Libreria di controlli utente WPF**, denominare il progetto **ProjectTemplateWizard**, e quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ProjectTemplateWizard** alla soluzione e apre il file predefinito UserControl1.xaml.  
  
6.  Eliminare il file UserControl1.xaml dal progetto.  
  
#### Per creare il progetto di comandi di SharePoint  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo soluzione SiteColumnProjectItem, scegliere **Aggiungi** e quindi scegliere **Nuovo progetto**.  
  
2.  Nella parte superiore della finestra di dialogo **Aggiungi nuovo progetto**, scegliere **.NET Framework 3.5** nell'elenco delle versioni di.NET Framework.  
  
3.  Espandere il nodo **Visual C\#** o il nodo  **Visual Basic** e quindi selezionare il nodo **Windows**.  
  
4.  Scegliere il modello di progetto **Libreria di classi**, denominare il progetto **SharePointCommands**quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **SharePointCommands** alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione dei progetti  
 Prima di creare la procedura guidata, è obbligatorio aggiungere ai progetti alcuni file di codice e i riferimenti all'assembly.  
  
#### Per configurare il progetto di procedura guidata  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto **ProjectTemplateWizard** e quindi scegliere **Proprietà**.  
  
2.  In **Creazione progetti**, scegliere la scheda **Applicazione** per un progetto Visual c\# o la scheda **Compila** per un progetto Visual Basic.  
  
3.  Assicurarsi che il framework di destinazione sia impostato su .NET Framework 4.5, non .NET Framework 4.5 Client Profile.  
  
     Per ulteriori informazioni, vedere [Procedura: destinare una versione di .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Aprire il menu di scelta rapida per il progetto **ProjectTemplateWizard** , scegliere **Aggiungi** e quindi selezionare **Nuovo elemento**.  
  
5.  Selezionare l'elemento **Finestra \(WPF\)**, denominare l'elemento **WizardWindow**, quindi scegliere il pulsante **Aggiungi**.  
  
6.  Aggiungere due elementi **Controllo utente \(WPF\)** al progetto e denominarli **Page1** e **Page2**.  
  
7.  Aggiungere nel progetto quattro file di codice ed assegnargli i nomi seguenti:  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Aprire il menu di scelta rapida per il nodo del progetto **ProjectTemplateWizard**, quindi scegliere **Aggiungi Riferimento**.  
  
9. Espandere il nodo **Assembly**, selezionare il nodo **Estensioni** quindi selezionare le caselle di controllo accanto agli assembly seguenti:  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Scegliere il pulsante **OK** per aggiungere gli assembly al progetto.  
  
11. In **Esplora soluzioni**, nella cartella **Riferimenti** per il progetto **ProjectTemplateWizard** , scegliere **EnvDTE**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic la cartella **Riferimenti** viene visualizzata solo quando la casella di controllo **Mostra sempre soluzione** è selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
12. Nella finestra **Proprietà**, modificare il valore della proprietà **Incorpora tipi di interoperabilità** in **False**.  
  
13. Se si sta sviluppando un progetto Visual Basic, importare lo spazio dei nomi ProjectTemplateWizard nel progetto utilizzando **Creazione progetti**.  
  
     Per ulteriori informazioni, vedere [Procedura: aggiungere o rimuovere spazi dei nomi importati &#40;Visual Basic&#41;](~/ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### Per configurare il progetto SharePointCommands  
  
1.  In **Esplora soluzioni**, scegliere il nodo del progetto **SharePointCommands**.  
  
2.  Sulla barra dei menu scegliere **Progetto**,  **Aggiungi elemento esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi elemento esistente** individuare la cartella in cui sono contenuti i file di codice per il progetto ProjectTemplateWizard, quindi scegliere il file di codice **CommandIds** .  
  
4.  Scegliere la freccia accanto al pulsante **Aggiungi** quindi scegliere l'opzione **Aggiungi come collegamento** nel menu visualizzato.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il file di codice al progetto **SharePointCommands** come un collegamento.  Il file di codice si trova nel progetto **ProjectTemplateWizard**, ma il codice nei file è compilato anche nel progetto **SharePointCommands**.  
  
5.  Nel progetto **SharePointCommands** aggiungere un altro file di codice denominato Commands.  
  
6.  Scegliere il progetto SharePointCommands quindi, nella barra dei menu, scegliere **Progetto**, **Aggiungi riferimento**.  
  
7.  Espandere il nodo **Assembly**, selezionare il nodo **Estensioni** quindi selezionare le caselle di controllo accanto agli assembly seguenti:  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Scegliere il pulsante **OK** per aggiungere gli assembly al progetto.  
  
## Creazione del modello di procedura guidata, del responsabile firmatario e degli ID per i comandi di SharePoint  
 Aggiungere il codice al progetto ProjectTemplateWizard per implementare i componenti seguenti nell'esempio:  
  
-   ID per i comandi di SharePoint.  Queste stringhe identificano i comandi di SharePoint utilizzati dalla procedura guidata.  Più avanti in questa procedura dettagliata si aggiungerà codice al progetto SharePointCommands per implementare i comandi.  
  
-   Modello dati della procedura guidata.  
  
-   Responsabile firmatario del progetto.  
  
 Per ulteriori informazioni su questi componenti, vedere [Informazioni sui componenti della procedura guidata](#wizardcomponents).  
  
#### Per definire gli ID per i comandi di SharePoint  
  
1.  Nel progetto ProjectTemplateWizard, aprire il file di codice CommandIds, quindi sostituire l'intero contenuto del file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/commandids.vb#5)]  
  
#### Per creare il modello di procedura guidata  
  
1.  Aprire il file di codice SiteColumnWizardModel e sostituire l'intero contenuto del file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]  
  
#### Per creare il responsabile firmatario del progetto  
  
1.  Aprire il file di codice ProjectSigningManager e quindi sostituire l'intero contenuto del file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/projectsigningmanager.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/projectsigningmanager.vb#8)]  
  
## Creazione dell'interfaccia utente della procedura guidata  
 Aggiungere contenuto XAML per definire l'interfaccia utente della finestra della procedura guidata e i due controlli utente che forniscono l'interfaccia utente per le pagine della procedura guidata, quindi aggiungere codice per definire il comportamento della finestra e dei controlli utente.  La procedura guidata creata è simile a quella predefinita per progetti SharePoint in Visual Studio.  
  
> [!NOTE]  
>  Nei passaggi seguenti il progetto includerà degli errori di compilazione dopo l'aggiunta di contenuto XAML o di codice al progetto.  che scompariranno quando si aggiunge codice nei passaggi successivi.  
  
#### Per creare l'interfaccia utente della finestra della procedura guidata  
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file WizardWindow.xaml quindi scegliere **Apri** per aprire la finestra nella finestra di progettazione.  
  
2.  Nella visualizzazione XAML della finestra di progettazione sostituire il codice XAML corrente con quello riportato di seguito.  Il codice XAML definisce un'interfaccia utente che include un'intestazione, un <xref:System.Windows.Controls.Grid> contenente le pagine della procedura guidata e i pulsanti di navigazione nella parte inferiore della finestra.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  La finestra creata in questo XAML è derivata dalla classe di base <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>.  Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, si consiglia di derivare la finestra di dialogo da questa classe per far sì che lo stile sia coerente con le altre finestre di dialogo di Visual Studio ed evitare problemi che potrebbero altrimenti verificarsi con le finestre di dialogo modali.  Per ulteriori informazioni, vedere [Creazione e gestione di finestre di dialogo modale](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Se si sviluppa un progetto di Visual Basic, rimuovere lo spazio dei nomi `ProjectTemplateWizard` dal nome della classe `WizardWindow` nell'attributo `x:Class` dell'elemento `Window`.  Questo elemento si trova nella prima riga del codice XAML.  Al termine, la prima riga dovrebbe essere simile al seguente esempio.  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Aprire il file code\-behind per il file WizardWindow.xaml.  
  
5.  Sostituire il contenuto di questo file, fatta eccezione per le dichiarazioni `using` all'inizio del file, con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml.cs#4)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/wizardwindow.xaml.vb#4)]  
  
#### Per creare l'interfaccia utente della prima pagina della procedura guidata  
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file Page1.xaml quindi scegliere **Apri** per aprire il controllo utente nella finestra di progettazione.  
  
2.  Nella visualizzazione XAML della finestra di progettazione sostituire il codice XAML corrente con quello riportato di seguito.  Il codice XAML definisce un'interfaccia utente che include una casella di testo in cui gli utenti possono immettere l'url dei siti locali da utilizzare per il debug.  L'interfaccia utente include inoltre i pulsanti di opzione con cui gli utenti possono specificare se il progetto è in modalità sandbox.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml#11)]  
  
3.  Se si sviluppa un progetto di Visual Basic, rimuovere lo spazio dei nomi `ProjectTemplateWizard` dal nome della classe `Page1` nell'attributo `x:Class` dell'elemento `UserControl`.  Lo spazio dei nomi si trova nella prima riga del codice XAML.  Al termine, la prima riga dovrebbe essere simile a quella seguente.  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Sostituire il contenuto del file Page1.xaml, fatta eccezione per le dichiarazioni `using` all'inizio del file, con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml.cs#2)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page1.xaml.vb#2)]  
  
#### Per creare l'interfaccia utente della seconda pagina della procedura guidata  
  
1.  Nel progetto ProjectTemplateWizard, aprire il menu di scelta rapida per il file Page2.xaml quindi scegliere **Apri**.  
  
     Il controllo utente verrà visualizzato nella finestra di progettazione.  
  
2.  Nella visualizzazione XAML, sostituire il codice XAML corrente con il codice XAML seguente.  Il codice XAML definisce un'interfaccia utente che comprende un elenco a discesa per la scelta del tipo di base della colonna del sito, una casella combinata per specificare un gruppo incorporato o personalizzato in cui visualizzare la colonna del sito nella raccolta e una casella di testo per specificare il nome della colonna del sito.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml#12)]  
  
3.  Se si sviluppa un progetto di Visual Basic, rimuovere lo spazio dei nomi `ProjectTemplateWizard` dal nome della classe `Page2` nell'attributo `x:Class` dell'elemento `UserControl`.  Lo spazio dei nomi si trova nella prima riga del codice XAML.  Al termine, la prima riga dovrebbe essere simile a quella seguente.  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Sostituire il contenuto del file code\-behind per il file Page2.xaml, fatta eccezione per le dichiarazioni `using` all'inizio del file, con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml.cs#3)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page2.xaml.vb#3)]  
  
## Implementazione della procedura guidata  
 Definire la funzionalità principale della procedura guidata implementando l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Questa interfaccia definisce i metodi chiamati da Visual Studio all'avvio e al termine della procedura guidata e in determinati momenti durante l'esecuzione.  
  
#### Per implementare la procedura guidata  
  
1.  Nel progetto ProjectTemplateWizard aprire il file di codice SiteColumnProjectWizard.  
  
2.  Sostituire tutto il contenuto del file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]  
  
## Creazione dei comandi SharePoint  
 Creare due comandi personalizzati che eseguono una chiamata nel modello a oggetti del server SharePoint.  Un comando determina se l'URL del sito digitato dall'utente nella procedura guidata è valido.  L'altro comando ottiene tutti tipi di campo dal sito di SharePoint specificato in modo che gli utenti possano selezionare quale utilizzare come base per la nuova colonna del sito.  
  
#### Per definire i comandi di SharePoint  
  
1.  Nel progetto **SharePointCommands** aprire il file di codice Commands.  
  
2.  Sostituire tutto il contenuto del file con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/sharepointcommands/commands.cs#9)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/sharepointcommands/commands.vb#9)]  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per la procedura guidata si trova nel progetto.  Compilare il progetto assicurandosi che tale operazione venga eseguita correttamente.  
  
#### Per compilare il progetto  
  
1.  Nella barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
## Rimozione del file key.snk dal modello del progetto  
 In [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), il modello del progetto creato contiene un file key.snk utilizzato per firmare ogni istanza del progetto Site Column.  Questo file key.snk non è più necessario poiché la procedura guidata genera ora un nuovo file key.snk per ogni progetto.  Rimuovere il file key.snk dal modello del progetto e rimuovere i riferimenti a questo file.  
  
#### Per rimuovere il file key.snk dal modello del progetto  
  
1.  In **Esplora soluzioni** sotto il nodo **SiteColumnProjectTemplate**, aprire il menu di scelta rapida del file **key.snk**, quindi scegliere **Elimina**.  
  
2.  Nella finestra di dialogo di conferma che verrà visualizzata scegliere il pulsante **OK**.  
  
3.  Nel nodo **SiteColumnProjectTemplate**, aprire il file SiteColumnProjectTemplate.vstemplate e rimuovere il seguente elemento.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Salvare e chiudere il file.  
  
5.  Nel nodo **SiteColumnProjectTemplate**, aprire il file ProjectTemplate.csproj o ProjectTemplate.vbproj, quindi eliminare il seguente elemento `PropertyGroup` da esso.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Rimuovere l'elemento `None` seguente.  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Salvare e chiudere il file.  
  
## Associazione della procedura guidata al modello di progetto  
 Dopo avere implementato la procedura guidata, è necessario associarla al modello di progetto **Site Column**.  A tale scopo, è necessario eseguire tre procedure:  
  
1.  Firmare l'assembly della procedura guidata con un nome sicuro.  
  
2.  Ottenere il token di chiave pubblica per l'assembly della procedura guidata.  
  
3.  Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il modello di progetto **Site Column**.  
  
#### Per firmare l'assembly della procedura guidata con un nome sicuro  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida del progetto **ProjectTemplateWizard**, quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Firma** selezionare la casella di controllo **Firma assembly**.  
  
3.  Nell'elenco **Scegli un file chiave con nome sicuro** scegliere **\<Nuova...\>**.  
  
4.  Nella finestra di dialogo **Crea chiave con nome sicuro** immettere un nome per il nuovo file di chiave, deselezionare la casella di controllo **Proteggi file di chiave con una password**, quindi scegliere il pulsante **OK**.  
  
5.  Aprire il menu di scelta rapida del progetto **ProjectTemplateWizard** e scegliere **Compila** per creare il file ProjectTemplateWizard.dll.  
  
#### Per ottenere il token di chiave pubblica per l'assembly della procedura guidata  
  
1.  Nel **Menu Start**, scegliere **Tutti i programmi**, scegliere **Microsoft Visual Studio**, scegliere **Strumenti di Visual Studio**, quindi scegliere **Prompt dei comandi per gli sviluppatori**.  
  
     Viene aperta una finestra Prompt dei comandi di Visual Studio.  
  
2.  Lanciare il seguente comando, sostituendo *PathToWizardAssembly* con il percorso completo dell'assembly ProjectTemplateWizard.dll compilato per il progetto ProjectTemplateWizard nel computer di sviluppo:  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Il token di chiave pubblica per l'assembly ProjectTemplateWizard.dll è scritto nella finestra del prompt dei comandi di Visual Studio.  
  
3.  Tenere aperta la finestra del prompt dei comandi di Visual Studio.  Il token di chiave pubblica sarà necessario durante la procedura seguente.  
  
#### Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate  
  
1.  In **Esplora soluzioni** espandere il nodo del progetto **SiteColumnProjectTemplate** e aprire il file SiteColumnProjectTemplate.vstemplate.  
  
2.  Alla fine del file, aggiungere l'elemento `WizardExtension` seguente tra i tag `</TemplateContent>` e `</VSTemplate>`.  Sostituire il valore *your token* dell'attributo `PublicKeyToken` con il token di chiave pubblica ottenuto nella procedura precedente.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Per ulteriori informazioni sull'elemento `WizardExtension`, vedere [Elemento WizardExtension &#40;modelli di Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Salvare e chiudere il file.  
  
## Aggiunta di parametri sostituibili al file Elements.xml nel modello di progetto  
 Aggiungere diversi parametri sostituibili al file Elements.xml nel progetto SiteColumnProjectTemplate.  Questi parametri vengono inizializzati nel metodo `RunStarted` della classe `SiteColumnProjectWizard` definita in precedenza.  Quando un utente crea un progetto Site Column, questi parametri nel file Elements.xml nel nuovo progetto vengono sostituiti automaticamente da Visual Studio con i valori specificati nella procedura guidata.  
  
 Un parametro sostituibile è un token che inizia e termina con il segno di dollaro \($\).  Oltre a definire i propri parametri sostituibili, è possibile utilizzare parametri predefiniti, definiti e inizializzati dal sistema del progetto di SharePoint.  Per ulteriori informazioni, vedere [Parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### Per aggiungere parametri sostituibili al file Elements.xml  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Elements.xml con il codice XML seguente.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Il nuovo XML modifica i valori degli attributi `Name`, `DisplayName`, `Type` e `Group` in parametri sostituibili personalizzati.  
  
2.  Salvare e chiudere il file.  
  
## Aggiunta della procedura guidata al pacchetto VSIX  
 Per distribuire la procedura guidata con il pacchetto VSIX che contiene il modello di progetto Site Column, aggiungere riferimenti al progetto di procedura guidata e al progetto dei comandi di SharePoint nel file source.extension.vsixmanifest nel progetto VSIX.  
  
#### Per aggiungere la procedura guidata al pacchetto VSIX  
  
1.  In **Esplora soluzioni**, nel progetto **SiteColumnProjectItem**, aprire il menu di scelta rapida del file **source.extension.vsixmanifest**, quindi scegliere **Apri**.  
  
     Visual Studio consente di aprire il file nell'editor del manifesto.  
  
2.  Nella scheda **Assets** dell'editor, scegliere il pulsante **Nuovo**.  
  
     Verrà aperta la finestra di dialogo **Aggiungi Nuovo Asset**.  
  
3.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.Assembly**.  
  
4.  Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
5.  Nell'elenco **Progetto** scegliere **ProjectTemplateWizard**, quindi fare clic sul pulsante **OK**.  
  
6.  Nella scheda **Assets** dell'editor, scegliere nuovamente il pulsante **Nuovo**.  
  
     Verrà aperta la finestra di dialogo **Aggiungi Nuovo Asset**.  
  
7.  Nell'elenco **Tipo**, immettere **SharePoint.Commands.v4**.  
  
8.  Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
9. Nell'elenco **Progetto**, scegliere il progetto **SharePointCommands**, quindi scegliere il pulsante **OK**.  
  
10. Sulla barra dei menu, scegliere **Compila**, **Compila soluzione**, quindi assicurarsi che la soluzione verrà compilata correttamente.  
  
## Test della procedura guidata  
 È ora possibile eseguire il test della procedura guidata.  Avviare innanzitutto il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio.  Eseguire quindi il test della procedura guidata per il progetto Site Column nell'istanza sperimentale di Visual Studio.  Infine, compilare ed eseguire il progetto per verificare che la colonna del sito funzioni come previsto.  
  
#### Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali di amministratore e quindi aprire la soluzione SiteColumnProjectItem.  
  
2.  Nel progetto ProjectTemplateWizard aprire il file di codice SiteColumnProjectWizard, quindi aggiungere un punto di interruzione alla prima riga di codice nel metodo `RunStarted`.  
  
3.  Sulla barra dei menu, scegliere **Debug**, **Eccezioni**.  
  
4.  Nella finestra di dialogo **Eccezioni** assicurarsi che le caselle di controllo **Generata** e **Non gestita dall'utente** relative a **Eccezioni Common Language Runtime** siano deselezionate, quindi selezionare il pulsante **OK**.  
  
5.  Avviare il debug con il tasto **F5** o, sulla barra dei menu, scegliendo **Debug**, **Avvia Debug**.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Site Column\\1.0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per testare la procedura guidata in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **File**, **Nuovo**, quindi fare clic su **Progetto**.  
  
2.  Espandere il nodo **Visual C\#** o il nodo **Visual Basic** \(a seconda del linguaggio che il modello di progetto supporta\), espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
3.  Nell'elenco dei modelli di progetto, scegliere **Site Column**, denominare il progetto **SiteColumnWizardTest** e scegliere il pulsante **OK**.  
  
4.  Verificare che il codice nell'altra istanza di Visual Studio venga interrotto in corrispondenza del punto di interruzione impostato precedentemente nel metodo `RunStarted`.  
  
5.  Continuare il debug del progetto premendo il tasto **F5** o, sulla barra dei menu, scegliendo **Debug**, **Continua**.  
  
6.  In **Personalizzazione guidata SharePoint**, inserire l'URL del sito che si desidera utilizzare per il debug, quindi fare clic sul pulsante **Successivo**.  
  
7.  Nella seconda pagina di **Personalizzazione guidata SharePoint**, effettuare le seguenti selezioni:  
  
    -   Dall'elenco **Tipo**, scegliere **Boolean**.  
  
    -   Nell'elenco **Raggruppa**, scegliere **Colonne Sì\/No personalizzate**.  
  
    -   Nella casella **Nome**, immettere Colonna Sì\/No personale, quindi scegliere il pulsante **Fine**.  
  
     In **Esplora soluzioni**, un nuovo progetto verrà visualizzato e conterrà un elemento di progetto denominato **Field1** e nell'editor di Visual Studio viene aperto il file del progetto Elements.xml.  
  
8.  Verificare che il file Elements.xml contenga i valori specificati nella procedura guidata.  
  
#### Per eseguire il test della colonna del sito in SharePoint.  
  
1.  Nell'istanza sperimentale di Visual Studio premere il tasto F5.  
  
     La colonna del sito viene assemblata e distribuita al sito di SharePoint specificato nella proprietà **URL sito** del progetto.  Nel browser web viene visualizzata la pagina predefinita di questo sito.  
  
    > [!NOTE]  
    >  Se viene visualizzata la finestra di dialogo **Debug degli script disabilitato**, fare clic sul pulsante **Sì** per continuare il debug del progetto.  
  
2.  Dal menu **Impostazioni sito**, scegliere **Azioni sito**.  
  
3.  Nella pagina Impostazioni Sito, in **Raccolte**, scegliere il collegamento **Colonne del sito**.  
  
4.  Nell'elenco delle colonne del sito, verificare che un gruppo **Colonne Sì\/No personalizzate** contenga una colonna denominata **Colonna Sì\/No personale**, quindi chiudere il Web browser.  
  
## Pulizia del computer di sviluppo  
 Una volta terminato di eseguire il test dell'elemento di progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.  
  
#### Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco delle estensioni selezionare **Colonna del sito**, quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione e quindi scegliere il pulsante **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere l'istanza di Visual Studio e l'istanza nella quale CustomActionProjectItem è aperto.  
  
     Per ulteriori informazioni sulla distribuzione delle estensioni di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vedere [Distribuzione di estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
## Vedere anche  
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Procedura: utilizzare procedure guidate con modelli di progetto](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  