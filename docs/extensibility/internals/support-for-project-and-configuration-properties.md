---
title: "Supporto per il progetto e le propriet&#224; di configurazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "proprietà del progetto, supporto con Visual Studio SDK"
  - "proprietà di configurazione suppporting con Visual Studio SDK"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Supporto per il progetto e le propriet&#224; di configurazione
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il **proprietà** finestra il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato \(IDE\) può visualizzare le proprietà di progetto e la configurazione. È possibile fornire una pagina delle proprietà per il proprio tipo di progetto in modo che l'utente può impostare le proprietà dell'applicazione.  
  
 Selezionando un nodo di progetto in **Esplora** e quindi fare clic su **proprietà** sul **progetto** menu, è possibile aprire una finestra di dialogo che include le proprietà di progetto e la configurazione. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], e tipi derivati da questi linguaggi, questa finestra di dialogo viene visualizzata come una pagina a schede in progetto di [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md). Per ulteriori informazioni, vedere [non incluso nella Build: procedura dettagliata: esposizione di progetto e le proprietà di configurazione \(c\#\)](http://msdn.microsoft.com/it-it/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Il Framework di pacchetto gestiti per i progetti \(MPFProj\) fornisce le classi di supporto per la creazione e gestione di nuovo sistema di progetto. È possibile trovare l'origine istruzioni di compilazione e di codice in [MPF per i progetti di Visual Studio 2013 \-](http://mpfproj12.codeplex.com/).  
  
## Persistenza del progetto e le proprietà di configurazione  
 Proprietà progetto e di configurazione sono persistenti in un file di progetto che è un'estensione di file associato al tipo di progetto, ad esempio, con estensione csproj, vbproj e .myproj. Progetti di linguaggio, in genere, utilizzare un file di modello per generare il file di progetto. Tuttavia, esistono effettivamente diversi modi per associare tipi di progetto e modelli. Per ulteriori informazioni, vedere [NIB: modelli di Visual Studio](http://msdn.microsoft.com/it-it/141fccaa-d68f-4155-822b-27f35dd94041) e [Descrizione del modello Directory \(. File VSDIR\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Proprietà progetto e di configurazione vengono create aggiungendo elementi al file di modello. Queste proprietà sono quindi disponibili per qualsiasi progetto creato utilizzando il tipo di progetto che utilizza il modello.[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetti e la MPFProj utilizzano entrambi il [non incluso nella Build: Cenni preliminari su MSBuild](http://msdn.microsoft.com/it-it/b588fd73-a45b-4706-908f-cc131bccfbde) schema per i file di modello. Tali file hanno una sezione PropertyGroup per ogni configurazione. Le proprietà dei progetti in genere vengono mantenute nella prima sezione PropertyGroup, che dispone di un argomento Configuration impostato su una stringa null.  
  
 Il codice seguente viene illustrato l'inizio di un file di progetto MSBuild base.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 In questo file di progetto `<Name>` e `<SchemaVersion>` sono proprietà del progetto, e `<Optimize>` è una proprietà di configurazione.  
  
 È responsabilità del progetto per rendere persistenti le proprietà di progetto e la configurazione del file di progetto.  
  
> [!NOTE]
>  Un progetto può ottimizzare la persistenza persistenti solo valori di proprietà diversi dai valori predefiniti.  
  
## Supporto per il progetto e le proprietà di configurazione  
 La `Microsoft.VisualStudio.Package.SettingsPage` classe implementa pagine delle proprietà di progetto e la configurazione. L'implementazione predefinita di `SettingsPage` offre proprietà pubbliche di un utente in una griglia delle proprietà generiche. Il `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` metodo consente di selezionare le classi derivate da `SettingsPage` per griglie di proprietà di progetto. Il `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` metodo consente di selezionare le classi derivate da `SettingsPage` per griglie di proprietà di configurazione. Il tipo di progetto deve eseguire l'override di questi metodi per selezionare le pagine delle proprietà appropriate.  
  
 La `SettingsPage` classe e la `Microsoft.VisualStudio.Package.ProjectNode` classe offrono questi metodi per rendere persistenti le proprietà di progetto e la configurazione:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` e `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` rendere persistenti le proprietà del progetto.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` e `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` rendere persistenti le proprietà di configurazione.  
  
    > [!NOTE]
    >  Le implementazioni di `Microsoft.VisualStudio.Package.SettingsPage` e `Microsoft.VisualStudio.Package.ProjectNode` classi utilizzano il `Microsoft.Build.BuildEngine` i metodi per ottenere e impostare le proprietà di progetto e la configurazione dal file di progetto \(MSBuild\).  
  
 La classe di derivazione `SettingsPage` deve implementare `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` e `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` per rendere persistenti le proprietà di configurazione di progetto o del file di progetto.  
  
## ProvideObjectAttribute e il percorso del Registro di sistema  
 Le classi derivate da `SettingsPage` sono progettati per essere condivisi tra i package VS. Per rendere possibile per un pacchetto Visual Studio creare una classe derivata da `SettingsPage`, aggiungere un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a una classe derivata da `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Il pacchetto Visual Studio a cui è associato l'attributo non è rilevante. Quando viene registrato un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], viene registrato l'id di classe \(CLSID\) di qualsiasi oggetto che può essere creato in modo che una chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> crearla.  
  
 Il percorso del Registro di sistema di un oggetto che può essere creato è determinato dalla combinazione <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la parola, CLSID e il guid del tipo di oggetto. Se `MyProjectPropertyPage` classe dispone di un guid di {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} e il UserRegistryRoot è HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, il percorso del Registro di sistema sarà HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723}.  
  
## Layout e gli attributi di proprietà di configurazione e un progetto  
 Il <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, e <xref:System.ComponentModel.DescriptionAttribute> attributi determinano il layout, assegnazione di etichette e la descrizione delle proprietà di progetto e la configurazione in una pagina delle proprietà generiche. Questi attributi determinare la categoria, il nome visualizzato e descrizione dell'opzione, rispettivamente.  
  
> [!NOTE]
>  Attributi equivalenti, SRCategory, LocDisplayName e SRDescription, utilizzare risorse di tipo stringa per la localizzazione e sono definiti in [MPF per i progetti di Visual Studio 2013 \-](http://mpfproj12.codeplex.com/).  
  
 Si consideri il frammento di codice riportato di seguito.  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 Il `MyConfigProp` proprietà di configurazione viene visualizzato nella pagina delle proprietà di configurazione come **cartella proprietà di configurazione** della categoria, **categoria My**. Se l'opzione è selezionata, la descrizione, **Descrizione My**, viene visualizzato nel riquadro Descrizione.  
  
## Vedere anche  
 [Non incluso nella Build: procedura dettagliata: esposizione di progetto e le proprietà di configurazione \(c\#\)](http://msdn.microsoft.com/it-it/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Aggiunta e rimozione di pagine delle proprietà](../../extensibility/adding-and-removing-property-pages.md)   
 [Stato di un pacchetto VSPackage](/visual-cpp/misc/vspackage-state)   
 [Progetti](../../extensibility/internals/projects.md)   
 [NIB: Modelli di Visual Studio](http://msdn.microsoft.com/it-it/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Descrizione del modello Directory \(. File VSDIR\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)