---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2"
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
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  Dopo avere definito un tipo di elemento di progetto SharePoint personalizzato e averlo associato a un modello di elemento in Visual Studio, è anche possibile fornire una procedura guidata per il modello.  È possibile utilizzare la procedura guidata per raccogliere informazioni dagli utenti quando utilizzano il modello per aggiungere una nuova istanza dell'elemento di progetto a un progetto.  Le informazioni raccolte possono essere utilizzate per inizializzare l'elemento di progetto.  
  
 In questa procedura dettagliata verrà aggiunta una procedura guidata all'elemento di progetto Azione personalizzata illustrato in [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  Quando un utente aggiunge un elemento di progetto azione personalizzata a un progetto SharePoint, la procedura guidata vengono raccolte informazioni sull'azione personalizzata \(ad esempio la posizione e l'url da passare quando un utente finale si sceglie\) e queste informazioni nel file Elements.xml nel nuovo elemento di progetto.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di una procedura guidata per un tipo di elemento di progetto SharePoint personalizzato associato a un modello di elemento.  
  
-   Definizione di un'interfaccia utente della procedura guidata personalizzata simile a quella delle procedure guidate predefinite per gli elementi di progetto SharePoint in Visual Studio.  
  
-   Utilizzo di parametri sostituibili per inizializzare i file di progetto SharePoint con i dati raccolti nella procedura guidata.  
  
-   Debug e test della procedura guidata.  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, il codice e altri file di questa procedura dettagliata dal seguente percorso: [File di progetto per le procedure dettagliate di estensibilità degli strumenti di SharePoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Prerequisiti  
 Per eseguire questa procedura dettagliata, è prima necessario creare la soluzione CustomActionProjectItem completando quanto descritto in [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Per completare la procedura dettagliata, nel computer di sviluppo devono inoltre essere disponibili i componenti seguenti:  
  
-   Edizioni supportate di Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio SDK.  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'elemento di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Procedure guidate per modelli di progetto e di elemento in Visual Studio.  Per ulteriori informazioni, vedere [Procedura: utilizzare procedure guidate con modelli di progetto](~/extensibility/how-to-use-wizards-with-project-templates.md) e l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
-   Azioni personalizzate in SharePoint.  Per ulteriori informazioni, vedere l'articolo relativo all'[azione personalizzata](http://go.microsoft.com/fwlink/?LinkID=177800) \(la pagina potrebbe essere in inglese\).  
  
## Creazione del progetto di procedura guidata  
 Per completare questa procedura dettagliata, è necessario aggiungere un progetto alla soluzione CustomActionProjectItem creata in [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  È quindi necessario implementare l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> e definire l'interfaccia utente della procedura guidata in questo progetto.  
  
#### Per creare il progetto di procedura guidata  
  
1.  In Visual Studio, aprire la soluzione CustomActionProjectItem  
  
2.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo della soluzione, scegliere **Aggiungi**quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
3.  Nella finestra di dialogo **Nuovo progetto**, espandere i nodi **Visual Basic** o **Visual C\#** quindi selezionare il nodo **Finestre**.  
  
4.  Nella parte superiore della finestra di dialogo **Nuovo progetto**, assicurarsi che **.NET Framework 4.5** sia selezionato nell'elenco delle versioni di.NET Framework.  
  
5.  Scegliere il modello di progetto **Libreria di controlli utente WPF**, denominare il progetto **ItemTemplateWizard**quindi scegliere il pulsante **OK**.  
  
     Tramite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto **ItemTemplateWizard** verrà aggiunto alla soluzione.  
  
6.  Eliminare l'elemento UserControl1 dal progetto.  
  
## Configurazione del progetto di procedura guidata  
 Prima di creare la procedura guidata, è necessario aggiungere una finestra di Windows Presentation Foundation \(WPF\), un file di codice e riferimenti al progetto.  
  
#### Per configurare il progetto di procedura guidata  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida nel nodo del progetto **ItemTemplateWizard** quindi scegliere **Proprietà**.  
  
2.  In **Progettazione progetti**, assicurarsi che il framework di destinazione sia impostato su .NET Framework 4,5.  
  
     Per i progetti visual C\#, è possibile impostare questo valore sulla scheda **Application**.  Per i progetti di Visual Basic., è possibile impostare questo valore sulla scheda **Compilazione**.  Per ulteriori informazioni, vedere [Procedura: destinare una versione di .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  Nel progetto **ItemTemplateWizard**, aggiungere un elemento **Finestra \(WPF\)** al progetto e denominarlo l'elemento **WizardWindow**.  
  
4.  Aggiungere due file di codice denominato CustomActionWizard e stringhe.  
  
5.  Aprire il menu di scelta rapida del progetto **ItemTemplateWizard** quindi scegliere **Aggiungi riferimento**.  
  
6.  Nella finestra di dialogo **Gestione riferimenti \- ItemTemplateWizard**, nel nodo **Assembly**, selezionare il nodo **Estensioni**.  
  
7.  Selezionare le caselle di controllo accanto ai seguenti assembly e quindi scegliere il pulsante **OK** :  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  In **Esplora soluzioni**, nella cartella **Riferimenti** per il progetto ItemTemplateWizard, selezionare il riferimento **EnvDTE**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic la cartella **Riferimenti** viene visualizzata solo quando la casella di controllo **Mostra sempre soluzione** è selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
9. Nella finestra **Proprietà**, modificare il valore della proprietà **Incorpora tipi di interoperabilità** a **False**.  
  
## Definizione del percorso e delle stringhe ID predefiniti per le azioni personalizzate  
 Per ogni azione personalizzata sono disponibili un percorso e un ID specificati negli attributi `GroupID` e `Location` dell'elemento `CustomAction` nel file Elements.xml.  In questo passaggio vengono definite alcune delle stringhe valide per questi attributi nel progetto ItemTemplateWizard.  Dopo avere completato questa procedura dettagliata, le stringhe vengono scritte nel file Elements.xml nell'elemento di progetto azione personalizzata quando gli utenti specificano un percorso e un ID nella procedura guidata.  
  
 Per semplicità, in questo esempio è supportato solo un subset degli ID e dei percorsi predefiniti disponibili.  Per un elenco completo, vedere [ID e percorsi predefiniti delle azioni personalizzate](http://go.microsoft.com/fwlink/?LinkId=181964) \(la pagina potrebbe essere in inglese\).  
  
#### Per definire il percorso e le stringhe ID predefiniti  
  
1.  aperto.  
  
2.  Nel progetto **ItemTemplateWizard**, sostituire il codice nel file di codice delle stringhe con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## Creazione dell'interfaccia utente della procedura guidata  
 Aggiungere codice XAML per definire l'Interfaccia utente della procedura guidata e aggiungere codice per associare alcuni controlli nella procedura guidata alle stringhe ID.  La procedura guidata creata è simile a quella predefinita per i progetti SharePoint in Visual Studio.  
  
#### Per creare l'interfaccia utente della procedura guidata  
  
1.  Nel progetto **ItemTemplateWizard**, aprire il menu di scelta rapida per il file **WizardWindow.xaml** quindi scegliere **Apri** per aprire la finestra nella finestra di progettazione.  
  
2.  In visualizzazione XAML, sostituire l'oggetto corrente XAML con il codice XAML seguente.  Il codice XAML definisce un'interfaccia utente che include un'intestazione, controlli per specificare il comportamento dell'azione predefinita e i pulsanti di navigazione nella parte inferiore della finestra.  
  
    > [!NOTE]  
    >  Il progetto presenterà alcuni errori di compilazione dopo aver aggiunto questo codice.  che scompariranno quando si aggiunge codice nei passaggi successivi.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  La finestra creata in questo codice XAML viene derivata dalla classe base <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>.  Quando si aggiunge una finestra di dialogo WPF personalizzata a Visual Studio, è consigliabile deriva la finestra di dialogo da questa classe per far sì che lo stile coerente con altre finestre di dialogo in Visual Studio e per evitare problemi che possono verificarsi nelle finestre di dialogo modale.  Per ulteriori informazioni, vedere [Creazione e gestione di finestre di dialogo modale](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Se si sviluppa un progetto di Visual Basic., rimuovere lo spazio dei nomi `ItemTemplateWizard` il nome della classe `WizardWindow` nell'attributo `x:Class` di elemento `Window`.  Questo elemento è la prima riga del codice XAML.  Al termine, la prima riga dovrebbe essere simile al seguente:  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Nel file code\-behind per il file WizardWindow.xaml, sostituire il codice corrente con il codice seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## Implementazione della procedura guidata  
 Definire le funzionalità della procedura guidata implementando l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
#### Per implementare la procedura guidata  
  
1.  Nel progetto **ItemTemplateWizard**, aprire il file di codice **CustomActionWizard** quindi sostituire il codice corrente nel file con il codice seguente:  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per la procedura guidata si trova nel progetto.  Compilare il progetto assicurandosi che tale operazione venga eseguita correttamente.  
  
#### Per compilare il progetto  
  
1.  Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
## Associazione della procedura guidata al modello di elemento  
 Dopo avere implementato la procedura guidata, è necessario associarla al modello di elemento **Azione personalizzata** completando tre passaggi principali:  
  
1.  Firmare l'assembly della procedura guidata con un nome sicuro.  
  
2.  Ottenere il token di chiave pubblica per l'assembly della procedura guidata.  
  
3.  Aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate per il modello di elemento **Azione personalizzata**.  
  
#### Per firmare l'assembly della procedura guidata con un nome sicuro  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida nel nodo del progetto **ItemTemplateWizard** quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Firma** selezionare la casella di controllo **Firma assembly**.  
  
3.  Nell'elenco **Scegli un file chiave con nome sicuro**, scegliere **\<New...\>**.  
  
4.  Nella finestra di dialogo **Crea chiave con nome sicuro**, nome, deselezionare la casella di controllo **Proteggi file di chiave con una password** quindi scegliere il pulsante **OK**.  
  
5.  Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**.  
  
#### Per ottenere il token di chiave pubblica per l'assembly della procedura guidata  
  
1.  In una finestra del prompt dei comandi di Visual Studio, eseguire il comando seguente, sostituendo *PathToWizardAssembly* con il percorso completo dell'assembly ItemTemplateWizard.dll compilato per il progetto ItemTemplateWizard nel computer di sviluppo.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Il token di chiave pubblica per l'assembly ItemTemplateWizard.dll è scritto nella finestra del prompt dei comandi di Visual Studio.  
  
2.  Tenere aperta la finestra del prompt dei comandi di Visual Studio.  Il token di chiave pubblica sarà necessario per completare la procedura successiva.  
  
#### Per aggiungere un riferimento all'assembly della procedura guidata nel file con estensione vstemplate  
  
1.  In **Esplora soluzioni**, espandere il nodo del progetto **ItemTemplate** quindi aprire il file ItemTemplate.vstemplate.  
  
2.  Alla fine del file, aggiungere l'elemento `WizardExtension` seguente tra i tag `</TemplateContent>` e `</VSTemplate>`.  Sostituire il valore *YourToken* l'attributo `PublicKeyToken` con il token di chiave pubblica ottenuto nella procedura precedente.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Per ulteriori informazioni sull'elemento `WizardExtension`, vedere [Elemento WizardExtension &#40;modelli di Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Salvare e chiudere il file.  
  
## Aggiunta di parametri sostituibili al file Elements.xml nel modello di elemento  
 Aggiungere diversi parametri sostituibili al file Elements.xml nel progetto ItemTemplate.  Questi parametri vengono inizializzati nel metodo `PopulateReplacementDictionary` della classe `CustomActionWizard` definita in precedenza.  Quando un utente aggiunge un elemento di progetto Azione personalizzata a un progetto, questi parametri nel file Elements.xml nel nuovo elemento di progetto vengono sostituiti automaticamente da Visual Studio con i valori specificati nella procedura guidata.  
  
 Un parametro sostituibile è un token che inizia e termina con il segno di dollaro \($\).  Oltre a definire i propri parametri sostituibili, è possibile utilizzare parametri predefiniti che il sistema di progetto SharePoint definisce e inizializzato.  Per ulteriori informazioni, vedere [Parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### Per aggiungere parametri sostituibili al file Elements.xml  
  
1.  Nel progetto ItemTemplate, sostituire il contenuto del file Elements.xml con il codice XML seguente.  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Tramite il nuovo codice XML i valori degli attributi `Id`, `GroupId`, `Location`, `Description` e `Url` vengono modificati in parametri sostituibili.  
  
2.  Salvare e chiudere il file.  
  
## Aggiunta della procedura guidata al pacchetto VSIX  
 Nel file source.extension.vsixmanifest nel progetto VSIX, aggiungere un riferimento al progetto di procedura guidata in modo che venga distribuito con il pacchetto VSIX che contiene l'elemento di progetto.  
  
#### Per aggiungere la procedura guidata al pacchetto VSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida nel file **source.extension.vsixmanifest** il progetto CustomActionProjectItem quindi scegliere **Apri** per aprirlo nell'editor del manifesto.  
  
2.  Nell'editor del manifesto, scegliere la scheda **Asset**, quindi scegliere il pulsante **Nuova**.  
  
     La finestra di dialogo **Aggiungi nuovo asset** visualizzato.  
  
3.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.Assembly**.  
  
4.  Nell'elenco **Alimentazione**, scegliere **Progetto nella soluzione corrente**.  
  
5.  Nell'elenco **Project**, scegliere **ItemTemplateWizard**quindi scegliere il pulsante **OK**.  
  
6.  Sulla barra dei menu, scegliere **Compilazione**, **Compila soluzione**quindi assicurarsi che la soluzione venga compilato senza errori.  
  
## Test della procedura guidata  
 È ora possibile eseguire il test della procedura guidata.  Innanzitutto, avviare il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio.  Esaminare quindi la procedura guidata per l'elemento di progetto azione personalizzata in un progetto SharePoint nell'istanza sperimentale di Visual Studio.  Infine, compilare ed eseguire il progetto SharePoint per verificare che l'azione personalizzata funzioni come previsto.  
  
#### Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali amministrative e aprire la soluzione CustomActionProjectItem.  
  
2.  Nel progetto ItemTemplateWizard, aprire il file di codice CustomActionWizard e aggiungere un punto di interruzione alla prima riga di codice nel metodo `RunStarted`.  
  
3.  Sulla barra dei menu, scegliere **Debug**, **Eccezioni**.  
  
4.  Nella finestra di dialogo **Eccezioni**, verificare che le caselle di controllo **Non gestita dall'utente** e **Generata** per **Eccezioni comuni di runtime per le lingue** siano deselezionate e quindi scegliere il pulsante **OK**.  
  
5.  Avviare il debug scegliendo il tasto F5, o, sulla barra dei menu, scegliente **Debug**, **Avvia debug**.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile% \\ AppData \\ local \\ Microsoft \\ VisualStudio \\ 11.0Exp \\ extensions \\ Contoso \\ elemento di progetto \\ 1,0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per testare la procedura guidata in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Il file**, **Nuova**, **Project**.  
  
2.  Espandere il nodo **Visual Basic** o **Visual C\#** \(a seconda del linguaggio che il modello di elemento supporta\), espandere il nodo **SharePoint** quindi selezionare il nodo **2010**.  
  
3.  Nell'elenco di modelli di progetto, scegliere **Progetto SharePoint 2010**, denominare il progetto **CustomActionWizardTest**quindi scegliere il pulsante **OK**.  
  
4.  In **Personalizzazione guidata SharePoint**, immettere l'url del sito che si desidera utilizzare per il debug e quindi scegliere il pulsante **Fine**.  
  
5.  In **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto, scegliere **Aggiungi**quindi scegliere **Nuovo elemento**.  
  
6.  Nella finestra di dialogo **Aggiungi nuovo elemento \- CustomItemWizardTest**, espandere il nodo **SharePoint** quindi espandere il nodo **2010**.  
  
7.  Nell'elenco di elementi di progetto, selezionare l'elemento **Azione personalizzata** quindi scegliere il pulsante **Aggiungi**.  
  
8.  Verificare che il codice nell'altra istanza di Visual Studio venga interrotto in corrispondenza del punto di interruzione impostato precedentemente nel metodo `RunStarted`.  
  
9. Continuare a eseguire il debug del progetto scegliendo il tasto F5 o, sulla barra dei menu, scegliente **Debug**, **Continua**.  
  
     Viene visualizzata la Personalizzazione guidata SharePoint.  
  
10. In **Percorso**, scegliere il pulsante di opzione **Modifica elenco**.  
  
11. Nell'elenco **ID gruppo**, scegliere **Comunicazioni**.  
  
12. Nella casella **Titolo**, immettere **Centro per sviluppatori SharePoint**.  
  
13. Nella casella **Descrizione**, immettere **Aprire il sito Web del Centro per sviluppatori di SharePoint**.  
  
14. Nella casella **URL**, immettere **http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx**quindi scegliere il pulsante **Fine**.  
  
     lo isual studio viene aggiunto un elemento denominato **CustomAction1** al progetto e aprire il file Elements.xml nell'editor.  Verificare che il file Elements.xml contenga i valori specificati nella procedura guidata.  
  
#### Per testare l'azione personalizzata in SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio, scegliere il tasto F5 o, sulla barra dei menu, scegliere **Debug**, **Avvia debug**.  
  
     L'azione personalizzata viene assemblata e distribuita al sito di SharePoint specificato dalla proprietà **URL sito** del progetto e il browser viene visualizzata la pagina predefinita di questo sito.  
  
    > [!NOTE]  
    >  Se la finestra di dialogo **Debug degli script disabilitato** viene visualizzato, scegliere il pulsante **Sì**.  
  
2.  Nell'area degli elenchi del sito di SharePoint, scegliere il collegamento **Attività**.  
  
     La pagina **Attività \- Tutte le attività** viene visualizzata.  
  
3.  Nella scheda **Strumenti elenco** della barra multifunzione, scegliere la scheda **Elenco** quindi, nel gruppo **Impostazioni**, scegliere **Impostazioni elenco**.  
  
     La pagina **Impostazioni elenco** viene visualizzata.  
  
4.  In **Comunicazioni** e dirette nella parte superiore della pagina, scegliere il collegamento **Centro per sviluppatori SharePoint**, verificare che il browser aprire il sito Web http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx e quindi chiudere il browser.  
  
## Pulizia del computer di sviluppo  
 Dopo aver completato il test dell'elemento di progetto, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.  
  
#### Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, sulla barra dei menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     La finestra di dialogo **Estensioni e aggiornamenti** viene aperto.  
  
2.  Nell'elenco di estensioni selezionare, l'estensione **Elemento di progetto azione personalizzata** quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo, scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione e quindi scegliere il pulsante **Riavvia ora** per completare la disinstallazione.  
  
4.  Chiudere entrambe le istanze di Visual Studio \(l'istanza sperimentale e l'istanza di Visual Studio in cui la soluzione CustomActionProjectItem è aperta\).  
  
## Vedere anche  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Procedura: utilizzare procedure guidate con modelli di progetto](~/extensibility/how-to-use-wizards-with-project-templates.md)   
 [Impostare come valore predefinito percorsi di un'azione personalizzata e gli ID](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  