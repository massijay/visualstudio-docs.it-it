---
title: "Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1"
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
  - "elementi di progetto SharePoint, definizione dei propri tipi"
  - "elementi di progetto [sviluppo per SharePoint in Visual Studio], definizione dei propri tipi"
  - "progetti SharePoint, creazione di modelli personalizzati"
  - "sviluppo per SharePoint in Visual Studio, definizione di nuovi tipi di elemento di progetto"
ms.assetid: b53d48d7-cbf2-45c2-9537-06a6819be397
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 1
  I progetti SharePoint sono contenitori per uno o più elementi di progetto SharePoint.  È possibile estendere il sistema del progetto SharePoint in Visual Studio creando i propri tipi di elementi di progetto SharePoint per poi associarli a un modello di progetto.  In questa procedura dettagliata verrà illustrato come definire un tipo di elemento di progetto per creare una colonna del sito, quindi creare un modello di progetto che può essere utilizzato per creare un nuovo progetto contenente un elemento di progetto di colonna del sito.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un'estensione di Visual Studio che definisca un nuovo tipo di elemento di progetto SharePoint per una colonna del sito.  Il tipo di elemento di progetto include una semplice proprietà personalizzata visualizzata nella finestra **Proprietà**.  
  
-   Creazione di un modello di progetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] per l'elemento di progetto.  
  
-   Compilazione di un pacchetto [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extension \(VSIX\) per distribuire il modello di progetto e l'assembly dell'estensione.  
  
-   Debug e test dell'elemento di progetto.  
  
 Si tratta di una procedura dettagliata autonoma.  Dopo avere completato questa procedura dettagliata, è possibile migliorare l'elemento di progetto aggiungendo una procedura guidata al modello di progetto.  Per ulteriori informazioni, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
> [!NOTE]  
>  È possibile scaricare un esempio che contiene i progetti completati, il codice e altri file di questa procedura dettagliata all'indirizzo seguente: [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Prerequisiti  
 Per completare la procedura dettagliata, nel computer di sviluppo devono essere presenti i componenti elencati di seguito:  
  
-   Edizioni supportate di Microsoft Windows, SharePoint e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Campo [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  In questa procedura dettagliata viene utilizzato il modello **VSIX Project** di SDK per creare un pacchetto VSIX e distribuire l'elemento di progetto.  Per ulteriori informazioni, vedere [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Per completare la procedura dettagliata è consigliabile conoscere il concetto seguente:  
  
-   Colonne del sito in SharePoint.  Per ulteriori informazioni, vedere [Colonne](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
-   Modelli di progetto predefiniti di Visual Studio.  Per ulteriori informazioni, vedere [Creazione di un progetto e di modelli di elemento personalizzati in Visual Studio](../ide/creating-project-and-item-templates.md).  
  
## Creazione dei progetti  
 Per completare questa procedura dettagliata è necessario creare tre progetti:  
  
-   Un progetto VSIX.  Questo progetto consente di creare il pacchetto VSIX per distribuire l'elemento di progetto di colonna del sito e il modello di progetto.  
  
-   Progetto del modello di progetto.  Questo progetto consente di creare un modello di progetto che può essere utilizzato per creare un nuovo progetto SharePoint contenente l'elemento di progetto di colonna del sito.  
  
-   Un progetto di libreria di classi.  Questo progetto implementa un'estensione di Visual Studio che definisce il comportamento dell'elemento di progetto di colonna del sito.  
  
 Iniziare la procedura dettagliata creando i progetti.  
  
#### Per creare il progetto VSIX  
  
1.  Avviare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Nella barra dei menu, scegliere **File**, **Nuovo**, **Progetto**.  
  
3.  Nella parte superiore della finestra di dialogo **Nuovo progetto**, assicurarsi che **.NET Framework 4.5** sia selezionato nell'elenco delle versioni di .NET Framework.  
  
4.  Espandere i nodi **Visual C\#** o **Visual Basic** quindi scegliere il nodo **Estendibilità**.  
  
    > [!NOTE]  
    >  Il nodo **Estendibilità** è disponibile solo se si installa Visual Studio SDK.  Per ulteriori informazioni, vedere la sezione precedente relativa ai prerequisiti.  
  
5.  Nell'elenco di modelli di progetto, scegliere **Progetto VSIX**.  
  
6.  Nella casella **Nome**, inserire **SiteColumnProjectItem**, e quindi premere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **SiteColumnProjectItem** a **Esplora soluzioni**.  
  
#### Per creare il progetto di modello di progetto  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, e quindi scegliere **Nuovo progetto**.  
  
    > [!NOTE]  
    >  Nei progetti di Visual Basic, il nodo della soluzione viene visualizzato in **Esplora soluzioni** solo quando la casella di controllo **Mostra sempre soluzione** viene selezionata in [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Nella parte superiore della finestra di dialogo **Nuovo progetto**, assicurarsi che **.NET Framework 4.5** sia selezionato nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere il nodo **Visual C\#** o **Visual Basic** quindi scegliere il nodo **Estendibilità**.  
  
4.  Nella lista dei modelli di progetto, selezionare **Modello progetto C\#** oppure **Modello progetto Visual Basic**.  
  
5.  Nella casella **Nome**, inserire **SiteColumnProjectTemplate**, e quindi premere il pulsante **OK**.  
  
     Tramite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verrà aggiunto il progetto **SiteColumnProjectTemplate** alla soluzione.  
  
6.  Eliminare il file di codice Class1 dal progetto.  
  
7.  Se si è creato un progetto Visual Basic, eliminare anche i file seguenti dal progetto:  
  
    -   MyApplication.Designer.vb  
  
    -   MyApplication.myapp  
  
    -   Resources.Designer.vb  
  
    -   Resources.resx  
  
    -   Settings.Designer.vb  
  
    -   Settings.settings  
  
#### Per creare il progetto di estensione  
  
1.  In **Esplora soluzioni**, aprire il menu di scelta rapida per il nodo soluzione, scegliere **Aggiungi**, e quindi scegliere **Nuovo progetto**.  
  
2.  Nella parte superiore della finestra di dialogo **Nuovo progetto**, assicurarsi che **.NET Framework 4.5** sia selezionato nell'elenco delle versioni di .NET Framework.  
  
3.  Espandere i nodi **Visual Basic** o **Visual C\#**, selezionare il nodo **Windows** quindi scegliere il modello **Libreria di classi**.  
  
4.  Nella casella **Nome**, inserire **ProjectItemTypeDefinition** e quindi premere il pulsante **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] aggiunge il progetto **ProjectItemTypeDefinition** alla soluzione e apre il file di codice predefinito Class1.  
  
5.  Eliminare il file di codice Class1 dal progetto.  
  
## Configurazione del progetto di estensione  
 Aggiungere file di codice e riferimenti all'assembly per configurare il progetto di estensione.  
  
#### Per configurare il progetto  
  
1.  Nel progetto ProjectItemTypeDefinition aggiungere un nuovo file di codice denominato **SiteColumnProjectItemTypeProvider**.  
  
2.  Nella barra dei menu, scegliere **Progetto**, **Aggiungi riferimento**.  
  
3.  Nella finestra di dialogo **Gestione riferimenti \- ProjectItemTypeDefinition** espandere il nodo **Assemblies**, selezionare il nodo **Framework**, quindi selezionare la casella di controllo System.ComponentModel.Composition.  
  
4.  Scegliere il nodo **Estensioni**, selezionare la casella di controllo accanto a Microsoft.VisualStudio.SharePoint, quindi scegliere il pulsante **OK**.  
  
## Definizione del nuovo tipo di elemento di progetto SharePoint  
 Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> per definire il comportamento del nuovo tipo di elemento di progetto.  Implementare questa interfaccia tutte le volte che si desidera definire un nuovo tipo di elemento di progetto.  
  
#### Per definire il nuovo elemento di progetto SharePoint  
  
1.  Nel file di codice **SiteColumnProjectItemTypeProvider**, sostituire il codice predefinito con il codice seguente quindi salvare il file.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projectitemtypedefinition/sitecolumnprojectitemtypeprovider.vb#1)]  
  
## Creazione di un modello di progetto Visual Studio  
 Creando un modello di progetto, si abilitano altri sviluppatori a creare progetti SharePoint contenenti elementi di progetto di colonna del sito.  Un modello di progetto SharePoint include i file richiesti per tutti i progetti in Visual Studio, quali i file con estensione csproj o vbproj e vstemplate e i file specifici dei progetti SharePoint.  Per ulteriori informazioni, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 In questa procedura, viene creato un progetto SharePoint vuoto per generare i file specifici dei progetti SharePoint.  Quindi aggiungere tali file al progetto SiteColumnProjectTemplate in modo da includerli nel modello generato dal progetto.  Configurare anche il file di progetto SiteColumnProjectTemplate per specificare dove il modello del progetto viene visualizzato nella finestra di dialogo **Nuovo progetto**.  
  
#### Per creare i file per il modello di progetto  
  
1.  Avviare una seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenziali di amministratore.  
  
2.  Creare un nuovo progetto SharePoint 2010 vuoto denominato **BaseSharePointProject**.  
  
    > [!IMPORTANT]  
    >  In **Procedura guidata di personalizzazione SharePoint** non selezionare il pulsante di opzione **Implementa come soluzione farm**.  
  
3.  Aggiungere un elemento vuoto al progetto e denominare l'elemento **Field1**.  
  
4.  Salvare il progetto, quindi chiudere la seconda istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
5.  Nell'istanza di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con la soluzione SiteColumnProjectItem aperta, in **Esplora soluzioni**, aprire il menu di scelta rapida del nodo del progetto **SiteColumnProjectTemplate**, scegliere **Aggiungi**, quindi **Elemento esistente**.  
  
6.  Nella finestra di dialogo **Aggiungi elemento esistente** aprire l'elenco delle estensioni di file e selezionare **Tutti i file \(\*.\*\)**.  
  
7.  Nella directory che contiene il progetto BaseSharePointProject, selezionare il file key.snk quindi scegliere il pulsante **Aggiungi**.  
  
    > [!NOTE]  
    >  In questa procedura dettagliata, il modello di progetto creato utilizza lo stesso file key.snk per firmare ciascun progetto creato utilizzando il modello.  Per imparare come espandere questo esempio per creare un diverso file key.snk per ciascuna istanza di progetto, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
8.  Ripetere i passaggi da 5 a 8 per aggiungere i seguenti file dalle sottocartelle specificate nella directory BaseSharePointProject:  
  
    -   \\Field1\\Elements.xml  
  
    -   \\Field1\\SharePointProjectItem.spdata  
  
    -   \\Features\\Feature1\\Feature1.feature  
  
    -   \\Features\\Feature1\\Feature1.Template.xml  
  
    -   \\Package\\Package.package  
  
    -   \\Package\\Package.Template.xml  
  
     Aggiungere questi file direttamente al progetto SiteColumnProjectTemplate; non ricreare le sottocartelle Field1 Features o Package nel progetto.  Per ulteriori informazioni su questi file, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
#### Per configurare la modalità di individuazione del modello di progetto nella finestra di dialogo Nuovo progetto da parte degli sviluppatori  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo di progetto **SiteColumnProjectTemplate** e quindi scegliere **Scaricare progetto**.  Se viene chiesto di salvare le modifiche apportate a uno o più file, scegliere **Sì**.  
  
2.  Aprire nuovamente il nodo **SiteColumnProjectTemplate** e scegliere **Modifica SiteColumnProjectTemplate.csproj** o **Modifica SiteColumnProjectTemplate.vbproj**.  
  
3.  Nel file di progetto, Individuare l'elemento `VSTemplate` seguente.  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
    ```  
  
4.  Sostituire questo elemento con il seguente XML:  
  
    ```  
    <VSTemplate Include="SiteColumnProjectTemplate.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     L'elemento `OutputSubPath` specifica cartelle aggiuntive nel percorso in cui viene creato il modello di progetto quando si compila il progetto.  Le cartelle specificate qui assicurano che il modello di progetto sia disponibile solo quando i clienti aprono la finestra di dialogo **Nuovo progetto**, espandono il nodo **SharePoint**, e poi scelgono il nodo **2010**.  
  
5.  Salvare e chiudere il file.  
  
6.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto **SiteColumnProjectTemplate**, quindi scegliere **Ricarica progetto**.  
  
## Modifica dei file di modello di progetto  
 Nel progetto SiteColumnProjectTemplate, modificare i seguenti file per definire il comportamento del modello di progetto:  
  
-   AssemblyInfo.cs o AssemblyInfo.vb  
  
-   Elements.xml  
  
-   SharePointProjectItem.spdata  
  
-   Feature1.feature  
  
-   Package.package  
  
-   SiteColumnProjectTemplate.vstemplate  
  
-   ProjectTemplate.csproj o ProjectTemplate.vbproj  
  
 Nelle procedure seguenti verranno aggiunti parametri sostituibili ad alcuni dei file.  Un parametro sostituibile è un token che inizia e termina con il simbolo del dollaro \($\).  Quando un utente utilizza questo modello di progetto per creare un progetto, questi parametri nel nuovo progetto vengono sostituiti automaticamente da Visual Studio con valori specifici.  Per ulteriori informazioni, vedere [Parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
#### Per modificare il file AssemblyInfo.cs o AssemblyInfo.vb.  
  
1.  Nel progetto SiteColumnProjectTemplate, aprire il file AssemblyInfo.cs o AssemblyInfo.vb quindi aggiungere la seguente istruzione all'inizio di esso:  
  
    ```vb  
    Imports System.Security  
    ```  
  
    ```csharp  
    using System.Security;  
    ```  
  
     Se la proprietà **Soluzione in modalità sandbox** di un progetto SharePoint è impostata su **True**, Visual Studio aggiunge <xref:System.Security.AllowPartiallyTrustedCallersAttribute> al file di codice AssemblyInfo.  Tuttavia, il file di codice di AssemblyInfo nel modello del progetto non importa lo spazio di nomi <xref:System.Security> per impostazione predefinita.  È necessario aggiungere l'istruzione **using** o **Imports** per evitare errori di compilazione.  
  
2.  Salvare e chiudere il file.  
  
#### Per modificare il file Elements.xml  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Elements.xml con il codice XML seguente.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
          Name="$safeprojectname$"   
          DisplayName="$projectname$"   
          Type="Text"   
          Group="Custom Columns">  
      </Field>  
    </Elements>  
    ```  
  
     Il nuovo XML aggiunge un elemento `Field` che definisce il nome e il tipo di base della colonna del sito, nonché il gruppo in cui elencare la colonna del sito nella raccolta.  Per ulteriori informazioni sul contenuto di questo file, vedere [Schema di definizione di campo](http://go.microsoft.com/fwlink/?LinkId=184290).  
  
2.  Salvare e chiudere il file.  
  
#### Per modificare il file SharePointProjectItem.spdata  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file SharePointProjectItem.spdata con il codice XML seguente.  
  
    ```  
  
    <ProjectItem Type="Contoso.SiteColumn" DefaultFile="Elements.xml"   
                 xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">  
      <Files>  
        <ProjectItemFile Source="Elements.xml" Target="$safeprojectname$\" Type="ElementManifest" />  
      </Files>   
    </ProjectItem>  
    ```  
  
     Il nuovo XML apporta al file le modifiche seguenti:  
  
    -   Modifica l'attributo `Type` dell'elemento `ProjectItem` nella stessa stringa passata all'oggetto <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> nella definizione di elemento di progetto \(la classe `SiteColumnProjectItemTypeProvider` creata precedentemente in questa procedura dettagliata\).  
  
    -   Rimuove gli attributi `SupportedTrustLevels` e `SupportedDeploymentScopes` dall'elemento `ProjectItem`.  Questi valori di attributo non sono necessari perché i livelli di attendibilità e gli ambiti di distribuzione vengono specificati nella classe `SiteColumnProjectItemTypeProvider` nel progetto ProjectItemTypeDefinition.  
  
     Per ulteriori informazioni sul contenuto dei file spdata, vedere [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).  
  
2.  Salvare e chiudere il file.  
  
#### Per modificare il file Feature1.feature  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Feature1.feature con il codice XML seguente.  
  
    ```  
  
    <feature xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="$guid4$" featureId="$guid4$"   
             imageUrl="" solutionId="00000000-0000-0000-0000-000000000000" title="Site Column Feature1" version=""  
             deploymentPath="$SharePoint.Project.FileNameWithoutExtension$_$SharePoint.Feature.FileNameWithoutExtension$"  
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/FeatureModel">  
      <projectItems>  
        <projectItemReference itemId="$guid2$" />  
      </projectItems>  
    </feature>  
    ```  
  
     Il nuovo XML apporta al file le modifiche seguenti:  
  
    -   Modifica i valori degli attributi `Id` e `featureId` dell'elemento `feature` in `$guid4$`.  
  
    -   Modifica i valori dell'attributo `itemId` dell'elemento `projectItemReference` in `$guid2$`.  
  
     Per ulteriori informazioni sui file con estensione feature, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Salvare e chiudere il file.  
  
#### Per modificare il file Package.package  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file Package.package con il codice XML seguente.  
  
    ```  
  
    <package xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0"   
             Id="$guid3$" solutionId="$guid3$" resetWebServer="false" name="$safeprojectname$"   
             xmlns="http://schemas.microsoft.com/VisualStudio/2008/SharePointTools/PackageModel">  
      <features>  
        <featureReference itemId="$guid4$" />  
      </features>  
    </package>  
    ```  
  
     Il nuovo XML apporta al file le modifiche seguenti:  
  
    -   Modifica i valori degli attributi `Id` e `solutionId` dell'elemento `package` in `$guid3$`.  
  
    -   Modifica i valori dell'attributo `itemId` dell'elemento `featureReference` in `$guid4$`.  
  
     Per ulteriori informazioni sui file con estensione package, vedere [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
2.  Salvare e chiudere il file.  
  
#### Per modificare il file SiteColumnProjectTemplate.vstemplate  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file SiteColumnProjectTemplate.vstemplate con una delle seguenti sezioni del file XML.  
  
    -   Se si sta creando un modello di progetto Visual C\#, utilizzare il seguente XML.  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>CSharp</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.csproj" File="ProjectTemplate.csproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
    -   Se si sta creando un modello di progetto Visual Basic, utilizzare il seguente XML.  
  
    ```  
  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Project">  
      <TemplateData>  
        <Name>Site Column</Name>  
        <Description>Creates a new site column in SharePoint</Description>  
        <FrameworkVersion>3.5</FrameworkVersion>  
        <ProjectType>VisualBasic</ProjectType>  
        <CreateNewFolder>true</CreateNewFolder>  
        <CreateInPlace>true</CreateInPlace>  
        <ProvideDefaultName>true</ProvideDefaultName>  
        <DefaultName>SiteColumn</DefaultName>  
        <LocationField>Enabled</LocationField>  
        <EnableLocationBrowseButton>true</EnableLocationBrowseButton>  
        <PromptForSaveOnCreation>true</PromptForSaveOnCreation>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <Icon>SiteColumnProjectTemplate.ico</Icon>  
        <SortOrder>1000</SortOrder>  
      </TemplateData>  
      <TemplateContent>  
        <Project TargetFileName="SharePointProject1.vbproj" File="ProjectTemplate.vbproj" ReplaceParameters="true">  
          <ProjectItem ReplaceParameters="true" TargetFileName="My Project\AssemblyInfo.vb">AssemblyInfo.vb</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.feature">Feature1.feature</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Features\Feature1\Feature1.Template.xml">Feature1.template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.package">Package.package</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Package\Package.Template.xml">Package.Template.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\SharePointProjectItem.spdata">SharePointProjectItem.spdata</ProjectItem>  
          <ProjectItem ReplaceParameters="true" TargetFileName="Field1\Elements.xml" OpenInEditor="true">Elements.xml</ProjectItem>  
          <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
        </Project>  
      </TemplateContent>  
    </VSTemplate>  
    ```  
  
     Il nuovo XML apporta al file le modifiche seguenti:  
  
    -   Imposta l'elemento `Name` al valore **Colonna del sito**. \(Questo nome viene visualizzato nella finestra di dialogo **Nuovo progetto**\).  
  
    -   Aggiunge gli elementi `ProjectItem` per ciascuno dei file inclusi in ogni istanza del progetto.  
  
    -   Utilizza lo spazio dei nomi "http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005".  Altri file di progetto in questa soluzione utilizzano lo spazio dei nomi "di http:\/\/schemas.microsoft.com\/developer\/msbuild\/2003".  Di conseguenza, verranno generati messaggi di avviso XML Schema, ma è possibile ignorarli in questa procedura dettagliata.  
  
     Per ulteriori informazioni sul contenuto dei file vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
2.  Salvare e chiudere il file.  
  
#### Per modificare il file ProjectTemplate.csproj o ProjectTemplate.vbproj  
  
1.  Nel progetto SiteColumnProjectTemplate, sostituire il contenuto del file ProjectTemplate.csproj o ProjectTemplate.vbproj con una delle seguenti sezioni di file XML.  
  
    -   Se si sta creando un modello di progetto Visual C\#, utilizzare il seguente XML.  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <AppDesignerFolder>Properties</AppDesignerFolder>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{14822709-B5A1-4724-98CA-57A101D1B079};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Web" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="Properties\AssemblyInfo.cs" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
    1.  Se si sta creando un modello di progetto Visual Basic, utilizzare il seguente XML.  
  
    ```  
  
    <Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
        <ProductVersion>  
        </ProductVersion>  
        <SchemaVersion>  
        </SchemaVersion>  
        <ProjectGuid>{$guid1$}</ProjectGuid>  
        <OutputType>Library</OutputType>  
        <RootNamespace>$safeprojectname$</RootNamespace>  
        <AssemblyName>$safeprojectname$</AssemblyName>  
        <TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
        <FileAlignment>512</FileAlignment>  
        <ProjectTypeGuids>{BB1F664B-9266-4fd6-B973-E1E44974B511};{D59BE175-2ED0-4C54-BE3D-CDAA9F3214C8};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        <OptionExplicit>On</OptionExplicit>  
        <OptionCompare>Binary</OptionCompare>  
        <OptionStrict>Off</OptionStrict>  
        <OptionInfer>On</OptionInfer>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <OutputPath>bin\Debug\</OutputPath>  
        <WarningLevel>4</WarningLevel>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <DebugType>pdbonly</DebugType>  
        <DefineDebug>false</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
      </PropertyGroup>  
      <PropertyGroup>  
        <SignAssembly>true</SignAssembly>  
        <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="System" />  
        <Reference Include="System.Core" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Data.DataSetExtensions" />  
        <Reference Include="System.Xml" />  
        <Reference Include="System.Xml.Linq" />  
        <Reference Include="Microsoft.SharePoint" />  
        <Reference Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Import Include="Microsoft.VisualBasic" />  
        <Import Include="System" />  
        <Import Include="System.Collections" />  
        <Import Include="System.Collections.Generic" />  
        <Import Include="System.Data" />  
        <Import Include="System.Diagnostics" />  
        <Import Include="System.Linq" />  
        <Import Include="System.Xml.Linq" />  
        <Import Include="Microsoft.SharePoint" />  
        <Import Include="Microsoft.SharePoint.Security" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="My Project\AssemblyInfo.vb" />  
      </ItemGroup>  
      <ItemGroup>  
        <AppDesigner Include="My Project\" />  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.feature">  
          <FeatureId>{$guid4$}</FeatureId>  
        </None>  
        <None Include="Field1\SharePointProjectItem.spdata">  
          <SharePointProjectItemId>{$guid2$}</SharePointProjectItemId>  
        </None>  
        <None Include="key.snk" />  
        <None Include="Package\Package.package">  
          <PackageId>{$guid3$}</PackageId>  
        </None>  
        <None Include="Package\Package.Template.xml">  
          <DependentUpon>Package.package</DependentUpon>  
        </None>  
      </ItemGroup>  
      <ItemGroup>  
        <None Include="Features\Feature1\Feature1.Template.xml">  
          <DependentUpon>Feature1.feature</DependentUpon>  
        </None>  
        <None Include="Field1\Elements.xml" />  
      </ItemGroup>  
      <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />  
      <Import Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v10.0\SharePointTools\Microsoft.VisualStudio.SharePoint.targets" />  
    </Project>  
    ```  
  
     Il nuovo XML apporta al file le modifiche seguenti:  
  
    -   Usa l'elemento `TargetFrameworkVersion` per specificare il .NET Framework 3.5, non 4.5.  
  
    -   Aggiunge gli elementi `SignAssembly` e `AssemblyOriginatorKeyFile` per firmare l'output del progetto.  
  
    -   Aggiunge nuovi elementi `Reference` per i riferimenti all'assembly utilizzati dai progetti SharePoint.  
  
    -   Aggiunge elementi per ciascuno dei file predefiniti nel progetto, quali Elements.xml e SharePointProjectItem.spdata.  
  
2.  Salvare e chiudere il file.  
  
## Creazione di un pacchetto VSIX per distribuire il modello di progetto  
 Per distribuire l'estensione, utilizzare il progetto VSIX nella soluzione **SiteColumnProjectItem** per creare un pacchetto VSIX.  Anzitutto, configurare il pacchetto VSIX modificando il file source.extension.vsixmanifest incluso nel progetto VSIX.  Successivamente, creare il pacchetto VSIX compilando la soluzione.  
  
#### Per configurare e creare il pacchetto VSIX  
  
1.  In **Esplora soluzioni** nel progetto **SiteColumnProjectItem**, aprire il file source.extension.vsixmanifest nell'editor di manifesto.  
  
     Il file source.extension.vsixmanifest è la base del file extension.vsixmanifest che tutti i pacchetti VSIX richiedono.  Per ulteriori informazioni su questo file, vedere [Informazioni di riferimento sullo schema dell'estensione VSIX](http://msdn.microsoft.com/it-it/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Nella casella **Nome prodotto** digitare **Site Column**.  
  
3.  Nella casella **Autore**, inserire **Contoso**.  
  
4.  Nella casella **Descrizione**, digitare **Progetto SharePoint per creare colonne del sito**.  
  
5.  Scegliere la scheda **Asset** quindi scegliere il pulsante **Nuovo**.  
  
     Verrà aperta la finestra di dialogo **Aggiungi Nuovo Asset**.  
  
6.  Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.ProjectTemplate**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `ProjectTemplate` del file extension.vsixmanifest.  Questo elemento identifica la sottocartella nel pacchetto VSIX che contiene il modello di progetto.  Per ulteriori informazioni, vedere [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/87add64c-9dcd-495f-8815-209dab182cb1).  
  
7.  Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
8.  Nell'elenco **Progetto** scegliere **SiteColumnProjectTemplate**, quindi fare clic sul pulsante **OK**.  
  
9. Scegliere ancora il pulsante **Nuovo**.  
  
     Verrà aperta la finestra di dialogo **Aggiungi Nuovo Asset**.  
  
10. Nell'elenco **Tipo**, scegliere **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Questo valore corrisponde all'elemento `MefComponent` del file extension.vsixmanifest.  Questo elemento specifica il nome di un assembly dell'estensione nel pacchetto VSIX.  Per ulteriori informazioni, vedere [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/it-it/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
11. Nell'elenco **Origine**, scegliere **Un progetto nella soluzione corrente**.  
  
12. Nell'elenco **Progetto** scegliere **ProjectItemTypeDefinition**, quindi fare clic sul pulsante **OK**.  
  
13. Sulla barra dei menu, scegliere **Compila**, **Compila soluzione**, quindi assicurarsi che il progetto venga compilato correttamente.  
  
## Esecuzione del test del modello di progetto  
 È ora possibile eseguire il test del modello di progetto.  Avviare innanzitutto il debug della soluzione SiteColumnProjectItem nell'istanza sperimentale di Visual Studio.  Eseguire quindi il test del progetto **Site Column** nell'istanza sperimentale di Visual Studio.  Infine, compilare ed eseguire il progetto SharePoint per verificare che la colonna del sito funzioni come previsto.  
  
#### Per avviare il debug della soluzione  
  
1.  Riavviare Visual Studio con credenziali di amministratore e quindi aprire la soluzione SiteColumnProjectItem.  
  
2.  Nel file di codice SiteColumnProjectItemTypeProvider, aggiungere un punto di interruzione alla prima riga di codice nel metodo `InitializeType` quindi premere **F5** per avviare il debug.  
  
     In Visual Studio i file di estensione vengono installati in %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Site Column\\1.0 e viene avviata un'istanza sperimentale di Visual Studio.  L'elemento del progetto verrà testato in questa istanza di Visual Studio.  
  
#### Per eseguire il test del progetto in Visual Studio  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **File**, **Nuovo**, quindi fare clic su **Progetto**.  
  
2.  Espandere il nodo **Visual C\#** o **Visual Basic** \(a seconda del linguaggio che il modello di progetto supporta\), espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
3.  Nell'elenco dei modelli di progetto, scegliere il modello **Colonna del sito**.  
  
4.  Nella casella **Nome** immettere **SiteColumnTest** e quindi scegliere il pulsante **OK**.  
  
     In **Esplora soluzioni** verrà visualizzato un nuovo elemento di progetto denominato **Field1**.  
  
5.  Verificare che il codice nell'altra istanza di Visual Studio si interrompa nel punto di interruzione impostato precedentemente nel metodo `InitializeType` quindi premere **F5** per continuare il debug del progetto.  
  
6.  In **Esplora soluzioni**, selezionare il nodo **Field1** quindi premere **F4**.  
  
     Viene aperta la finestra **Proprietà**.  
  
7.  Verificare che la proprietà **Proprietà esempio** venga visualizzata nell'elenco di proprietà.  
  
#### Per eseguire il test della colonna del sito in SharePoint.  
  
1.  In **Esplora soluzioni** scegliere il nodo **SiteColumnTest**.  
  
2.  Nella finestra **Proprietà** fare clic sulla casella di testo accanto alla proprietà **URL sito** e digitare **http:\/\/localhost**.  
  
     Questo passaggio consente di specificare il sito di SharePoint locale sul computer di sviluppo da utilizzare per il debug.  
  
    > [!NOTE]  
    >  La proprietà **URL sito** è vuota per impostazione predefinita, poiché il modello di progetto Site Column non fornisce una procedura guidata per la raccolta di tale valore alla creazione del progetto.  Per imparare come aggiungere una procedura guidata che richieda allo sviluppatore tale valore e configuri la proprietà nel nuovo progetto, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
3.  Premere il tasto **F5**.  
  
     La colonna del sito viene assemblata e distribuita al sito di SharePoint specificato dalla proprietà **URL sito** del progetto.  Nel browser web viene visualizzata la pagina predefinita di questo sito.  
  
    > [!NOTE]  
    >  Se viene visualizzata la finestra di dialogo **Debug degli script disabilitato**, fare clic sul pulsante **Sì** per continuare il debug del progetto.  
  
4.  Dal menu **Impostazioni sito**, scegliere **Azioni sito**.  
  
5.  Nella pagina **Impostazioni sito**, nella lista **Raccolte**, scegliere il link **Colonne del sito**.  
  
6.  Nell'elenco delle colonne del sito, verificare che un gruppo **Colonne personalizzate** contenga una colonna denominata **SiteColumnTest**.  
  
7.  Chiudere il browser web.  
  
## Pulizia del computer di sviluppo  
 Una volta terminato di eseguire il test del progetto, rimuovere il modello di progetto dall'istanza sperimentale di Visual Studio.  
  
#### Per pulire il computer di sviluppo  
  
1.  Nell'istanza sperimentale di Visual Studio, nella barra del menu, scegliere **Strumenti**, **Estensioni e aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco delle estensioni selezionare l'estensione **Colonna del sito**, quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione.  
  
4.  Selezionare il pulsante **Chiudi** per completare la disinstallazione.  
  
5.  Chiudere entrambe le istanze di Visual Studio, ovvero quella sperimentale e l'istanza in cui è aperta la soluzione SiteColumnProjectItem.  
  
## Passaggi successivi  
 Dopo avere completato questa procedura dettagliata, è possibile aggiungere una procedura guidata al modello di progetto.  Quando un utente crea un progetto Site Column, tramite la procedura guidata viene richiesto all'utente l'URL del sito da utilizzare per il debug e di indicare se la nuova soluzione è in modalità sandbox, quindi la procedura guidata configurerà il nuovo progetto con le informazioni specificate.  Tramite la procedura guidata vengono inoltre raccolte informazioni sulla colonna del sito \(ad esempio il tipo di base e il gruppo in cui elencare la colonna nella raccolta di colonne del sito\) e queste informazioni vengono aggiunte al file Elements.xml nel nuovo progetto.  Per ulteriori informazioni, vedere [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## Vedere anche  
 [Procedura dettagliata: Creazione di un elemento di progetto Colonna del sito con un modello di progetto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  