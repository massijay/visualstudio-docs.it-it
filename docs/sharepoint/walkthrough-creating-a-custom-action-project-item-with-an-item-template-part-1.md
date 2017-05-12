---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1"
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
  - "SharePoint project items, creating custom templates"
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 41ed9c1c-4239-4d80-934b-975fde744288
caps.latest.revision: 152
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 151
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1
  Il sistema di progetto SharePoint può essere esteso in Visual Studio creando tipi di elemento di progetto personalizzati.  In questa procedura dettagliata, si creerà un elemento di progetto che può essere aggiunto a un progetto SharePoint per creare un'azione personalizzata in un sito di SharePoint.  L'azione personalizzata aggiunge una voce al menu **Azioni sito** del sito di SharePoint.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che definisca un nuovo tipo di elemento di progetto SharePoint per un'azione personalizzata.  Il nuovo tipo di elemento di progetto implementa numerose funzionalità personalizzate:  
  
    -   Un menu di scelta rapida utilizzato come punto di partenza per altre attività correlate all'elemento di progetto, ad esempio la visualizzazione di una finestra di progettazione per l'azione personalizzata in Visual Studio.  
  
    -   Codice che viene eseguito quando uno sviluppatore modifica alcune proprietà dell'elemento di progetto e il progetto in cui è contenuto.  
  
    -   Un'icona personalizzata viene visualizzata accanto all'elemento di progetto in **Esplora soluzioni**.  
  
-   Creazione di un modello di elemento di Visual Studio per l'elemento di progetto.  
  
-   Compilazione di un pacchetto Visual Studio Extension \(VSIX\) per distribuire il modello di elemento di progetto e l'assembly delle estensioni.  
  
-   Debug e test dell'elemento di progetto.  
  
 Si tratta di una procedura dettagliata autonoma.  Dopo avere completato questa procedura dettagliata, è possibile migliorare l'elemento di progetto aggiungendo una procedura guidata al modello di elemento.  Per ulteriori informazioni, vedere [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, il codice e altri file di questa procedura dettagliata all'indirizzo seguente:  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di Microsoft Windows, SharePoint e Visual Studio.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Campo [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'elemento di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere i concetti riportati di seguito:  
  
-   Azioni personalizzate in SharePoint.  Per ulteriori informazioni, vedere [Azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
-   Modelli di elemento in Visual Studio.  Per ulteriori informazioni, vedere [Creazione di un progetto e di modelli di elemento personalizzati in Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata è necessario creare tre progetti:  
  
-   Un progetto VSIX.  Questo progetto consente di creare il pacchetto VSIX per distribuire l'elemento di progetto SharePoint.  
  
-   Un progetto di modello di elemento.  Questo progetto consente di creare un modello di elemento che può essere utilizzato per aggiungere l'elemento di progetto SharePoint a un progetto SharePoint.  
  
-   Un progetto di libreria di classi.  Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento di progetto SharePoint.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu, scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Assicurarsi che nell'elenco nella parte superiore della finestra di dialogo **Nuovo progetto** sia selezionata l'opzione **.NET Framework 4.5**.  
  
4.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **Extensibility**.  
  
    > [!NOTE]  
    >  Il nodo **Extensibility** è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
5.  Selezione del modello **VSIX Project**.  
  
6.  Nella casella di testo **Nome** inserire **CustomActionProjectItem**, quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di aggiungere il progetto **CustomActionProjectItem** a **Esplora soluzioni**.  
  
#### Per creare il progetto di modello di elemento  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, e quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Assicurarsi che nell'elenco nella parte superiore della finestra di dialogo **Nuovo progetto** sia selezionata l'opzione **.NET Framework 4.5**.  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **Extensibility**.  
  
4.  Nell'elenco dei modelli di progetto, scegliere **Modello di elemento C\#** oppure **Modello di elemento Visual Basic**.  
  
5.  Nella casella di testo **Nome**, inserire **ItemTemplate**, quindi scegliere il pulsante **OK**.  
  
     Tramite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] il progetto **ItemTemplate** verrà aggiunto alla soluzione.  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, e quindi scegliere **Nuovo progetto**.  
  
2.  Assicurarsi che nell'elenco nella parte superiore della finestra di dialogo **Nuovo progetto** sia selezionata l'opzione **.NET Framework 4.5**.  
  
3.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C\#** o **Visual Basic**, scegliere il nodo **Windows** e quindi il modello di progetto **Libreria di classe**.  
  
4.  Nella casella di testo **Nome** inserire **ProjectItemDefinition**, quindi scegliere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ProjectItemDefinition** alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione del progetto di estensione  
 Prima di scrivere codice per definire il tipo di elemento di progetto SharePoint, è necessario aggiungere al progetto di estensione file di codice e riferimenti all'assembly.  
  
#### Per configurare il progetto  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ProjectItemDefinition**, scegliere **Aggiungi** e quindi scegliere **Nuovo elemento**.  
  
2.  Nell'elenco di elementi di progetto scegliere **File codice**.  
  
3.  Nella casella **Nome**, inserire il nome **CustomAction** con l'appropriata estensione del file e quindi scegliere il pulsante **Aggiungi**.  
  
4.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ProjectItemDefinition** e quindi scegliere **Aggiungi riferimento**.  
  
5.  Nella finestra di dialogo **Strumento di gestione dei riferimenti \- ProjectItemDefinition**, selezionare il nodo **Assembly** quindi scegliere il nodo **Framework**.  
  
6.  Spuntare le caselle di controllo accanto a ciascuno dei seguenti insiemi:  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
7.  Scegliere il nodo **Estensioni**, selezionare la casella di controllo accanto a Microsoft.VisualStudio.Sharepoint, quindi scegliere il pulsante **OK**.  
  
## Definizione del nuovo tipo di elemento di progetto SharePoint  
 Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> per definire il comportamento del nuovo tipo di elemento di progetto.  Implementare questa interfaccia tutte le volte che si desidera definire un nuovo tipo di elemento di progetto.  
  
#### Per definire il nuovo elemento di progetto SharePoint  
  
1.  Nel progetto ProjectItemDefinition aprire il file di codice CustomAction.  
  
2.  Sostituire il codice di questo file con il seguente.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/projectitemdefinition/customaction.vb#1)]  
  
## Creazione di un'icona per l'elemento di progetto in Esplora soluzioni  
 Quando si crea un elemento di progetto SharePoint personalizzato è possibile associare un'immagine \(icona o bitmap\) all'elemento di progetto.  Questa immagine viene visualizzata accanto all'elemento di progetto in **Esplora soluzioni**.  
  
 Nella procedura riportata di seguito viene creata un'icona per l'elemento di progetto e tale icona viene incorporata nell'assembly delle estensioni.  L'oggetto <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> della classe `CustomActionProjectItemTypeProvider` creata precedentemente fa riferimento all'icona.  
  
#### Per creare un'icona personalizzata per l'elemento di progetto  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ProjectItemDefinition** e scegliere **Aggiungi**, quindi fare clic su **Nuovo elemento...**.  
  
2.  Nell'elenco degli elementi di progetto, selezionare l'elemento **File icona**.  
  
    > [!NOTE]  
    >  Nei progetti Visual Basic è necessario fare clic sul nodo **Generale** per visualizzare l'elemento **File icona**.  
  
3.  Nella casella di testo **Nome**, inserire **CustomAction\_SolutionExplorer.ico**, quindi scegliere il pulsante **Aggiungi**.  
  
     La nuova icona viene aperta in **Editor immagini**.  
  
4.  Modificare la versione 16x16 del file icona in modo che la relativa progettazione sia facilmente riconoscibile, quindi salvarlo.  
  
5.  In **Esplora soluzioni**, scegliere **CustomAction\_SolutionExplorer.ico**.  
  
6.  Nella finestra **Properties**, scegliere la freccia accanto alla proprietà **Azione di compilazione**.  
  
7.  Nell'elenco visualizzato, scegliere **Risorsa incorporata**.  
  
## Verifica  
 In questa fase della procedura dettagliata, tutto il codice per l'elemento di progetto si trova nel progetto.  Compilare il progetto per verificare che tale operazione venga eseguita correttamente.  
  
#### Per compilare il progetto  
  
1.  Aprire il menu di scelta rapida per il progetto **ProjectItemDefinition**, quindi scegliere **Compila**.  
  
## Creazione di un modello di elemento di Visual Studio  
 Per consentire agli altri sviluppatori di utilizzare l'elemento di progetto è necessario creare un modello di progetto o di elemento.  Gli sviluppatori utilizzano questi modelli in Visual Studio per generare un'istanza dell'elemento di progetto creando un nuovo progetto o aggiungendo un elemento a un progetto esistente.  Per questa procedura dettagliata, utilizzare il progetto ItemTemplate per configurare l'elemento di progetto.  
  
#### Per creare il modello di elemento  
  
1.  Eliminare il file di codice Class1 dal progetto ItemTemplate.  
  
2.  Nel progetto ItemTemplate aprire il file ItemTemplate.vstemplate.  
  
3.  Sostituire il contenuto del file con il codice XML seguente, quindi salvare e chiudere il file.  
  
    > [!NOTE]  
    >  Il codice XML seguente è per un modello di elemento Visual C\#.  Se si crea un modello di elemento Visual Basic, sostituire il valore dell'elemento `ProjectType` con `VisualBasic`.  
  
    ```  
  
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>CustomAction</DefaultName>  
        <Name>Custom Action</Name>  
        <Description>SharePoint Custom Action by Contoso</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>1000</SortOrder>  
        <Icon>ItemTemplate.ico</Icon>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
      <TemplateContent>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>  
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Questo file consente di definire il contenuto e il comportamento del modello di elemento.  Per ulteriori informazioni sul contenuto di questo file, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
4.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ItemTemplate**, scegliere **Aggiungi**, e quindi scegliere **Nuovo elemento**.  
  
5.  Nella finestra di dialogo **Aggiungi nuovo elemento**, scegliere il modello **File di testo**.  
  
6.  Nella casella di testo **Nome** inserire **CustomAction.spdata**, quindi scegliere il pulsante **Aggiungi**.  
  
7.  Aggiungere il codice XML seguente al file CustomAction.spdata, quindi salvare e chiudere il file.  
  
    ```  
  
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"   
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />  
      </Files>  
    </ProjectItem>  
    ```  
  
     In questo file sono contenute informazioni sui file presenti nell'elemento di progetto.  L'attributo `Type` dell'elemento `ProjectItem` deve essere impostato sulla stessa stringa passata all'oggetto <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> nella definizione di elemento di progetto \(la classe `CustomActionProjectItemTypeProvider` creata precedentemente in questa procedura dettagliata\).  Per ulteriori informazioni sul contenuto dei file spdata, vedere [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
8.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ItemTemplate**, scegliere **Aggiungi**, e quindi scegliere **Nuovo elemento**.  
  
9. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il modello **XML file**.  
  
10. Nella casella di testo **Nome** inserire **Elements.xml**, quindi scegliere il pulsante **Aggiungi**.  
  
11. Sostituire il contenuto del file Elements.xml con il codice XML seguente, quindi salvare e chiudere il file.  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="Replace this with a GUID or some other unique string"  
                    GroupId="SiteActions"  
                    Location="Microsoft.SharePoint.StandardMenu"  
                    Sequence="1000"  
                    Title="Replace this with your title"  
                    Description="Replace this with your description" >  
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Questo file consente di definire un'azione personalizzata predefinita attraverso cui viene creata una voce nel menu **Azioni sito** del sito di SharePoint.  Quando un utente sceglie l'elemento menu, l'URL specificato nell'elemento `UrlAction` viene aperto nel browser web.  Per ulteriori informazioni sugli elementi XML che è possibile utilizzare per definire un'azione personalizzata, vedere [Definizioni di un'azione personalizzata](http://go.microsoft.com/fwlink/?LinkId=177801).  
  
12. Facoltativamente, aprire il file ItemTemplate.ico e modificarlo in modo da poterlo riconoscere.  Questa icona verrà visualizzata accanto all'elemento di progetto nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
13. In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ItemTemplate**, quindi scegliere **Scarica progetto**.  
  
14. Aprire nuovamente il menu di scelta rapida del progetto **ItemTemplate**, quindi scegliere **Modifica ItemTemplate.csproj** o **Modifica ItemTemplate.vbproj**.  
  
15. Individuare l'elemento `VSTemplate` seguente nel file di progetto.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
    ```  
  
16. Sostituire l'elemento `VSTemplate` con il codice XML seguente, quindi salvare e chiudere il file.  
  
    ```  
    <VSTemplate Include="ItemTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     L'elemento `OutputSubPath` specifica cartelle aggiuntive nel percorso in cui viene creato il modello di elemento quando si compila il progetto.  Le cartelle qui specificate assicurano che il modello sarà disponibile solo quando viene aperta la finestra di dialogo **Aggiungi nuovo elemento**, aperto il nodo **SharePoint**, e quindi scelto il nodo **2010**.  
  
17. In **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto **ItemTemplate**, quindi scegliere **Ricarica progetto**.  
  
## Creazione di un pacchetto VSIX per distribuire l'elemento di progetto  
 Per distribuire l'estensione, utilizzare il progetto VSIX nella soluzione per creare un pacchetto VSIX.  Anzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX.  Successivamente, creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il file **source.extension.vsixmanifest** nel progetto CustomActionProjectItem, quindi scegliere **Apri**.  
  
     Visual Studio consente di aprire il file nell'editor del manifesto.  Il file source.extension.vsixmanifest è la base del file extension.vsixmanifest che tutti i pacchetti VSIX richiedono.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto**, inserire **Custom Action Project Item**.  
  
3.  Nella casella **Autore**, inserire **Contoso**.  
  
4.  Nella casella **Descrizione**, inserire **A SharePoint project item that represents a custom action**.  
  
5.  Nella scheda **Assets**, scegliere il pulsante **Nuovo**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo Asset**.  
  
6.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.ItemTemplate**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `ItemTemplate` del file extension.vsixmanifest.  Questo elemento consente di identificare la sottocartella nel pacchetto VSIX che contiene il modello degli elementi del progetto.  Per ulteriori informazioni, vedere [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
7.  Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Progetto**, scegliere **ItemTemplate**, quindi scegliere il pulsante **OK** .  
  
9. Nella scheda **Asset**, scegliere nuovamente il pulsante **Nuovo**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo Asset**.  
  
10. Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MefComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
12. Nell'elenco **Progetto**, scegliere **ProjectItemDefinition**.  
  
13. Scegliere il pulsante **OK**.  
  
14. Sulla barra dei menu, scegliere **Compila**, **Compila soluzione**, quindi assicurarsi che il progetto venga compilato correttamente.  
  
15. Verificare che la cartella di output della compilazione per il progetto CustomActionProjectItem contenga il file CustomActionProjectItem.vsix.  
  
     Per impostazione predefinita, la cartella di output di compilazione è ..\\bin\\Debug sotto la cartella che contiene il progetto CustomActionProjectItem.  
  
## Test dell'elemento di progetto  
 È ora possibile testare l'elemento di progetto.  Avviare innanzitutto il debug della soluzione CustomActionProjectItem nell'istanza sperimentale di Visual Studio.  Testare quindi l'elemento di progetto **Azione personalizzata** in un progetto SharePoint nell'istanza sperimentale di Visual Studio.  Infine, compilare ed eseguire il progetto SharePoint per verificare che l'azione personalizzata funzioni come previsto.  
  
#### Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con i privilegi di amministratore, quindi aprire la soluzione CustomActionProjectItem.  
  
2.  Aprire il file codice CustomAction, quindi aggiungere un breakpoint alla prima riga di codice nel metodo `InitializeType`.  
  
3.  Premere il tasto **F5** per avviare il debug.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile%\\Dati applicazione\\Locale\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Custom Action Project Item\\1.0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per testare l'elemento di progetto in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **File**, **Nuovo**, quindi fare clic su **Progetto**.  
  
2.  Espandere **Visual C\#** o **Visual Basic** \(a seconda del linguaggio che il modello elemento supporta\), espandere **SharePoint**, quindi scegliere il nodo **2010**.  
  
3.  Nell'elenco dei modelli di progetto fare clic su **Progetto SharePoint 2010**.  
  
4.  Nella casella **Nome**, inserire **CustomActionTest**, quindi scegliere il pulsante **OK**.  
  
5.  In **Personalizzazione guidata SharePoint**, inserire l'URL del sito che si desidera utilizzare per il debug, quindi fare clic sul pulsante **Fine**.  
  
6.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo progetto, scegliere **Aggiungi**, quindi scegliere **Nuovo elemento**.  
  
7.  Nella finestra di dialogo **Aggiungi nuovo elemento**, scegliere il nodo **2010** sotto il nodo **SharePoint**.  
  
     Verificare che l'elemento **Azione personalizzata** sia visualizzato nell'elenco di elementi di progetto.  
  
8.  Selezionare l'elemento **Azione personalizzata**, quindi scegliere il pulsante **Aggiungi**.  
  
     Visual Studio aggiunge un elemento al progetto che viene chiamato **CustomAction1** e apre il file Elements.xml nell'editor.  
  
9. Verificare che il codice nell'altra istanza di Visual Studio venga interrotto in corrispondenza del punto di interruzione impostato precedentemente nel metodo `InitializeType`.  
  
10. Premere il tasto **F5** per continuare il debug del progetto.  
  
11. Nell'istanza sperimentale di Visual Studio, in **Esplora soluzioni**, aprire menu di scelta rapida per il nodo **CustomAction1**, quindi scegliere **Visualizza finestra di progettazione azione personalizzata**.  
  
12. Verificare che venga visualizzata una finestra di messaggio, quindi scegliere il pulsante **OK**.  
  
     Questo menu di scelta rapida può essere utilizzato per fornire opzioni o comandi aggiuntivi agli sviluppatori, ad esempio per visualizzare una finestra di progettazione per l'azione personalizzata.  
  
13. Sulla barra dei menu, scegliere **Visualizza**, **Output**.  
  
     Verrà aperta la finestra **Output**.  
  
14. In **Esplora soluzioni**, aprire il menu di scelta rapida per l'elemento **CustomAction1** e quindi impostare il nome su **MyCustomAction**.  
  
     Nella finestra **Output** verrà visualizzato un messaggio di conferma.  Questo messaggio è scritto dal gestore eventi <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> definito nella classe `CustomActionProjectItemTypeProvider`.  Questo e altri eventi dell'elemento di progetto possono essere gestiti per implementare il comportamento personalizzato quando lo sviluppatore modifica l'elemento di progetto.  
  
#### Per testare l'azione personalizzata in SharePoint  
  
1.  Nell'istanza sperimentale di Visual Studio aprire il file Elements.xml che è figlio dell'elemento di progetto **MyCustomAction**.  
  
2.  Nel file Elements.xml, apportare le seguenti modifiche e salvare il file:  
  
    -   Nell'elemento `CustomAction`, impostare l'attributo `Id` su un GUID o su un'altra stringa univoca come illustrato nel seguente esempio:  
  
        ```  
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"  
        ```  
  
    -   Nell'elemento `CustomAction`, impostare l'attributo `Title` come mostrato nell'esempio seguente:  
  
        ```  
        Title="SharePoint Developer Center"  
        ```  
  
    -   Nell'elemento `CustomAction`, impostare l'attributo `Description` come mostrato nell'esempio seguente:  
  
        ```  
        Description="Opens the SharePoint Developer Center Web site."  
        ```  
  
    -   Nell'elemento `UrlAction`, impostare l'attributo `Url` come mostrato nell'esempio seguente:  
  
        ```  
        Url="http://msdn.microsoft.com/sharepoint/default.aspx"  
        ```  
  
3.  Premere il tasto F5.  
  
     L'azione personalizzata viene assemblata e distribuita al sito di SharePoint specificato nella proprietà **URL sito** del progetto.  Nel browser web viene visualizzata la pagina predefinita di questo sito.  
  
    > [!NOTE]  
    >  Se viene visualizzata la finestra di dialogo **Debug degli script disabilitato**, fare clic sul pulsante **Sì** per continuare il debug del progetto.  
  
4.  Nel menu **Azioni del sito**, scegliere **Centro per sviluppatori di SharePoint**, verificare che il browser apra il sito Web http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx, quindi chiudere il browser web.  
  
## Pulizia del computer di sviluppo  
 Dopo aver completato il test dell'elemento di progetto, rimuovere il modello di elemento di progetto dall'istanza sperimentale di Visual Studio.  
  
#### Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco delle estensioni, scegliere **Custom Action Project Item**, e quindi fare clic sul pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere il pulsante **Riavvia ora** per completare la disinstallazione.  
  
5.  Chiudere l'istanza di Visual Studio e l'istanza nella quale CustomActionProjectItem è aperto.  
  
## Passaggi successivi  
 Dopo avere completato questa procedura dettagliata, è possibile aggiungere una procedura guidata al modello di elemento.  Quando un utente aggiunge un elemento di progetto di azione personalizzata a un progetto SharePoint, la procedura guidata raccoglie informazioni sull'azione personalizzata \(come ad esempio il percorso e l'URL a cui passare quando l'azione viene scelta\) e aggiunge al file Elements.xml nel nuovo elemento di progetto.  Per ulteriori informazioni, vedere [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
## Vedere anche  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  