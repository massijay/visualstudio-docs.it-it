---
title: "Creazione di un sistema di progetto di base, parte 1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "scrittura di un sistema di progetto"
  - "sistema di progetto"
  - "esercitazione"
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 47
caps.handback.revision: 47
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un sistema di progetto di base, parte 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare i file di codice sorgente e altre risorse. I progetti vengono visualizzati come figli delle soluzioni di **Esplora**. Progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente e creare riferimenti a servizi Web, database e altre risorse.  
  
 I progetti sono definiti nei file di progetto, ad esempio un file con estensione csproj per un progetto Visual c\#. È possibile creare un proprio tipo di progetto che ha il proprio estensione nome file del progetto. Per altre informazioni sui tipi di progetto, vedere [Tipi di progetto](../extensibility/internals/project-types.md).  
  
> [!NOTE]
>  Se è necessario estendere Visual Studio con un tipo di progetto personalizzati, è consigliabile sfruttare il [sistema del progetto di Visual Studio](https://github.com/Microsoft/VSProjectSystem) che presenta numerosi vantaggi rispetto alla creazione di un sistema di progetto da zero:  
>   
>  -   Caricamento di più semplice.  Anche un sistema di progetto di base richiede decine di migliaia di righe di codice.  Sfruttando CPS riduce i costi di caricamento di un numero ridotto prima che si è pronti per personalizzarlo secondo le proprie esigenze.  
> -   Maggiore semplicità di manutenzione.  Sfruttando CPS, è sufficiente mantenere i propri scenari.  Gestire la manutenzione di tutta l'infrastruttura di sistema di progetto.  
>   
>  Se si desidera destinate alle versioni di Visual Studio precedente a Visual Studio 2013, non sarà in grado di sfruttare CPS in un'estensione di Visual Studio.  In tal caso, questa procedura dettagliata è un ottimo strumento per iniziare.  
  
 Questa procedura dettagliata viene illustrato come creare un tipo di progetto che ha il .myproj di estensione nome file progetto. Questa procedura dettagliata acquisisce dal sistema di progetto Visual c\# esistente.  
  
> [!NOTE]
>  Per un esempio end\-to\-end di un sistema di progetto linguaggio completo, vedere Approfondimenti esempio IronPython in [Esempi di VSSDK](../misc/vssdk-samples.md).  
  
 Questa procedura dettagliata illustra come eseguire queste attività:  
  
-   Creare un tipo di progetto di base.  
  
-   Creare un modello di progetto di base.  
  
-   Registrare il modello di progetto con Visual Studio.  
  
-   Creare un'istanza del progetto, aprire il **Nuovo progetto** la finestra di dialogo e quindi utilizzando il modello.  
  
-   Creare una factory di progetto per il sistema del progetto.  
  
-   Creare un nodo di progetto per il sistema di progetto.  
  
-   Aggiungere icone personalizzate per il sistema del progetto.  
  
-   Implementare la sostituzione dei parametri di modello di base.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 È inoltre necessario scaricare il codice sorgente per il [Managed Package Framework per progetti](http://mpfproj12.codeplex.com/). Estrarre il file in una posizione accessibile per la soluzione che si intende creare.  
  
## Creazione di un tipo di progetto di base  
 Creare un progetto VSIX c\# denominato **SimpleProject**. \(**File, nuovo, progetto** e quindi **pacchetto Visual Studio c\#, estendibilità,**\). Aggiungere un modello di elemento di progetto Package Visual Studio \(in Esplora soluzioni fare clic sul nodo del progetto e selezionare **Aggiungi \/ nuovo elemento**, quindi passare alla **estendibilità \/ pacchetto di Visual Studio**\). Nome del file **SimpleProjectPackage**.  
  
## Creazione di un modello di progetto di base  
 A questo punto, è possibile modificare questa base su VSPackage per implementare il nuovo tipo di progetto .myproj. Per creare un progetto basato sul tipo di progetto .myproj, deve conoscere quali file, risorse e riferimenti da aggiungere al nuovo progetto di Visual Studio. Per fornire queste informazioni, inserire i file di progetto in una cartella di modello di progetto. Quando un utente utilizza il progetto .myproj per creare un progetto, i file vengono copiati nel nuovo progetto.  
  
#### Per creare un modello di progetto di base  
  
1.  Aggiungere al progetto, uno sotto le altre tre cartelle: **Templates\\Projects\\SimpleProject**. \(In **Esplora**, fare doppio clic su di **SimpleProject** nodo di progetto, scegliere **Aggiungi**, e quindi fare clic su **nuova cartella**. Denominare la cartella `Templates`. Nel **modelli** cartella, aggiungere una cartella denominata `Projects`. Nel **progetti** cartella, aggiungere una cartella denominata `SimpleProject`.\)  
  
2.  Nel **Projects\\SimpleProject** cartella aggiungere un file di icona denominato `SimpleProject.ico`. Quando fa clic su **Aggiungi**, verrà aperto l'editor di icona.  
  
3.  Rendere l'icona distinti. Questa icona verrà visualizzata nel **Nuovo progetto** la finestra di dialogo più avanti nella procedura dettagliata.  
  
     ![Icona Progetto semplice](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4.  L'icona di salvare e chiudere l'editor delle icone.  
  
5.  Nel **Projects\\SimpleProject** cartella, aggiungere un **classe** elemento denominato `Program.cs`.  
  
6.  Sostituire il codice esistente con le righe seguenti.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  Questo non è il formato finale del codice Program.cs. verranno gestiti con i parametri di sostituzione in un passaggio successivo. È possibile visualizzare errori di compilazione, ma fino a quando il file **BuildAction** è **contenuto**, dovrebbe essere possibile compilare ed eseguire il progetto come al solito.  
  
1.  Salvare il file.  
  
2.  Copiare il file AssemblyInfo.cs dal **proprietà** cartella per il **Projects\\SimpleProject** cartella.  
  
3.  Nel **Projects\\SimpleProject** cartella aggiungere un file XML denominato `SimpleProject.myproj`.  
  
    > [!NOTE]
    >  L'estensione per tutti i progetti di questo tipo è .myproj. Se si desidera modificarlo, è necessario modificarlo ovunque che viene menzionato nella procedura dettagliata.  
  
4.  Sostituire il contenuto esistente con le righe seguenti.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
        <SchemaVersion>2.0</SchemaVersion>  
        <ProjectGuid></ProjectGuid>  
        <OutputType>Exe</OutputType>  
        <RootNamespace>MyRootNamespace</RootNamespace>  
        <AssemblyName>MyAssemblyName</AssemblyName>  
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        <DebugSymbols>true</DebugSymbols>  
        <OutputPath>bin\Debug\</OutputPath>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
        <DebugSymbols>false</DebugSymbols>  
        <OutputPath>bin\Release\</OutputPath>  
      </PropertyGroup>  
      <ItemGroup>  
        <Reference Include="mscorlib" />  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
        <Reference Include="System.Xml" />  
      </ItemGroup>  
      <ItemGroup>  
        <Compile Include="AssemblyInfo.cs">  
          <SubType>Code</SubType>  
        </Compile>  
        <Compile Include="Program.cs">  
          <SubType>Code</SubType>  
        </Compile>  
      </ItemGroup>  
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />  
    </Project>  
    ```  
  
5.  Salvare il file.  
  
6.  Nel **proprietà** finestra, impostare il **azione di compilazione** AssemblyInfo.cs, Program.cs, SimpleProject.ico e SimpleProject.myproj per **contenuto**, e impostare i relativi **Includi in VSIX** proprietà **True**.  
  
 Questo modello di progetto viene descritto un progetto Visual c\# base con una configurazione di Debug e una configurazione di rilascio. Il progetto include due file di origine, AssemblyInfo.cs e Program.cs e numerosi assembly che i riferimenti. Quando viene creato un progetto dal modello, il valore ProjectGuid viene automaticamente sostituito da un nuovo GUID.  
  
 In **Esplora**, espansa della **modelli** cartella deve apparire come segue:  
  
 Modelli  
  
 Progetti  
  
 SimpleProject  
  
 AssemblyInfo.cs  
  
 Program.cs  
  
 SimpleProject.ico  
  
 SimpleProject.myproj  
  
## Creazione di una Factory di progetto di base  
 È necessario indicare a Visual Studio il percorso della cartella del modello di progetto. A tale scopo, aggiungere un attributo alla classe che implementa la factory del progetto in modo che il percorso del modello viene scritto nel Registro di sistema quando viene compilato il VSPackage VSPackage. Iniziare creando una factory di progetto di base che è identificata da una factory del progetto GUID. Utilizzare il <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo per collegare la factory del progetto per la classe SimpleProjectPackage.  
  
#### Per creare una factory di progetto di base  
  
1.  Aprire SimpleProjectPackageGuids.cs nell'editor di codice.  
  
2.  Creare i GUID per la factory del progetto \(nel **strumenti** menu, fare clic su **Crea GUID**\), o utilizzare quello nell'esempio seguente. Aggiungere i GUID per la classe SimpleProjectPackageGuids. I GUID devono essere in formato GUID e forma di stringa. Il codice risultante dovrebbe assomigliare all'esempio seguente.  
  
    ```  
    static class SimpleProjectPackageGuids  
    {  
        public const string guidSimpleProjectPkgString =   
            "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
        public const string guidSimpleProjectCmdSetString =   
            "72c23e1d-f389-410a-b5f1-c938303f1391";  
        public const string guidSimpleProjectFactoryString =   
            "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
        public static readonly Guid guidSimpleProjectCmdSet =   
            new Guid(guidSimpleProjectCmdSetString);  
        public static readonly Guid guidSimpleProjectFactory =   
            new Guid(guidSimpleProjectFactoryString);  
    }  
    ```  
  
3.  Aggiungere una classe all'inizio **SimpleProject** cartella denominata `SimpleProjectFactory.cs`.  
  
4.  Aggiungere le seguenti istruzioni using:  
  
    ```  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Aggiungere un attributo Guid per la classe SimpleProjectFactory. Il valore dell'attributo è la factory del progetto nuovo GUID.  
  
    ```  
    [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
    class SimpleProjectFactory  
    {  
    }  
    ```  
  
 È ora possibile registrare il modello di progetto.  
  
#### Per registrare il modello di progetto  
  
1.  In SimpleProjectPackage.cs, aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> attributo alla classe SimpleProjectPackage, come indicato di seguito.  
  
    ```  
    [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
        @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
    [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
    public sealed class SimpleProjectPackage : Package  
    ```  
  
2.  Ricompilare la soluzione e verificare che venga compilato senza errori.  
  
     La ricompilazione registra il modello di progetto.  
  
 I parametri `defaultProjectExtension` e `possibleProjectExtensions` sono impostate per l'estensione del file di progetto \(.myproj\). Il `projectTemplatesDirectory` parametro è impostato per il percorso relativo della cartella dei modelli. Durante la compilazione, questo percorso verrà convertito in una compilazione completa e aggiunta al Registro di sistema per registrare il sistema del progetto.  
  
## La registrazione del modello di test  
 Registrazione modello indica Visual Studio il percorso della cartella del modello di progetto in modo che Visual Studio è possibile visualizzare il nome del modello e l'icona nel **Nuovo progetto** la finestra di dialogo.  
  
#### Per verificare la registrazione di modello  
  
1.  Premere F5 per avviare il debug di un'istanza sperimentale di Visual Studio.  
  
2.  Nell'istanza sperimentale, creare un nuovo progetto del tipo di progetto appena creato. Nel **Nuovo progetto** nella finestra di dialogo dovrebbe essere **SimpleProject** in **modelli installati**.  
  
 Ora si dispone di una factory del progetto che è registrata. Tuttavia, non è ancora crea un progetto. Il pacchetto del progetto e la factory di progetto utilizzati insieme per creare e inizializzare un progetto.  
  
## Aggiungere il codice gestito Framework pacchetto  
 Implementare la connessione tra il pacchetto del progetto e la factory del progetto.  
  
-   Importare i file di codice sorgente per Framework pacchetto gestito.  
  
    1.  Scaricare il progetto SimpleProject \(in **Esplora**, selezionare il nodo del progetto e scegliere il menu di scelta rapida **Scarica progetto**.\) e aprire il file di progetto nell'editor XML.  
  
    2.  Aggiungere i blocchi seguenti al file di progetto \(di sotto i blocchi \< Import \>\). Impostare ProjectBasePath sul percorso del file ProjectBase.files nel codice gestito Framework pacchetto che appena scaricato. Potrebbe essere necessario aggiungere il percorso di una barra rovesciata. In caso contrario, il progetto potrebbe non riuscire a trovare il codice gestito Framework pacchetto.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        >  Non dimenticare la barra rovesciata alla fine del percorso.  
  
    3.  Ricaricare il progetto.  
  
    4.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
        -   Microsoft.VisualStudio.Designer.Interfaces \(in \< installazione VSSDK \> \\VisualStudioIntegration\\Common\\Assemblies\\v2.0\)  
  
        -   WindowsBase  
  
        -   Microsoft.Build.Tasks.v4.0  
  
#### Per inizializzare la factory del progetto  
  
1.  Aggiungere il codice seguente nel file SimpleProjectPackage.cs `using` istruzione.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2.  Derivare la `SimpleProjectPackage` classe `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3.  Registrare la factory del progetto. Aggiungere la riga seguente per il `SimpleProjectPackage.Initialize` metodo subito dopo `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4.  Implementare la proprietà astratta `ProductUserContext`:  
  
    ```c#  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5.  In SimpleProjectFactory.cs, aggiungere la seguente `using` istruzione dopo esistente `using` istruzioni.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6.  Derivare la `SimpleProjectFactory` classe `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7.  Aggiungere il seguente metodo fittizio per la `SimpleProjectFactory` classe. Questo metodo viene implementato in una sezione successiva.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8.  Aggiungere il seguente campo e costruttore la `SimpleProjectFactory` classe. Questo `SimpleProjectPackage` riferimento viene memorizzata nella cache in un campo privato, in modo che può essere utilizzato nell'impostazione di un provider di servizi.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Ricompilare la soluzione e verificare che venga compilato senza errori.  
  
## L'implementazione della Factory progetto di test  
 Verificare se viene chiamato il costruttore per l'implementazione di factory del progetto.  
  
#### Per testare l'implementazione della factory progetto  
  
1.  Nel file SimpleProjectFactory.cs, impostare un punto di interruzione nella riga seguente di `SimpleProjectFactory` costruttore.  
  
    ```  
    this.package = package;  
    ```  
  
2.  Premere F5 per avviare un'istanza sperimentale di Visual Studio.  
  
3.  Nell'istanza sperimentale, iniziare a creare un nuovo progetto. Nel **Nuovo progetto** nella finestra di dialogo SimpleProject il tipo di progetto e quindi fare clic su **OK**. L'esecuzione verrà interrotta in corrispondenza del punto di interruzione.  
  
4.  Rimuovere il punto di interruzione e interrompere il debug. Poiché un nodo di progetto non è stato ancora creato, il codice di creazione del progetto ancora genera eccezioni.  
  
## Estensione della classe di nodo di progetto  
 A questo punto è possibile implementare la `SimpleProjectNode` classe che deriva dalla `ProjectNode` classe. La `ProjectNode` classe di base gestisce le attività seguenti della creazione del progetto:  
  
-   Copia il file di modello di progetto, SimpleProject.myproj, nuova cartella di progetto. La copia è stata rinominata in base al nome immesso nella **Nuovo progetto** la finestra di dialogo. Il `ProjectGuid` valore della proprietà viene sostituito da un nuovo GUID.  
  
-   Consente di scorrere gli elementi di MSBuild del file di modello di progetto, SimpleProject.myproj e Cerca `Compile` elementi. Per ogni `Compile` file di destinazione, viene copiato nella nuova cartella di progetto.  
  
 Derivata `SimpleProjectNode` classe gestisce queste attività:  
  
-   Abilita le icone per i nodi di progetto e file in **Esplora** può essere creato o selezionato.  
  
-   Consente sostituzioni di parametro di modello di progetto aggiuntivi specificare.  
  
#### Per estendere la classe di nodo di progetto  
  
1.  
  
2.  Aggiungere una classe denominata `SimpleProjectNode.cs`.  
  
3.  Sostituire il codice esistente con il codice seguente.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Project;  
  
    namespace SimpleProject  
    {  
        public class SimpleProjectNode : ProjectNode  
        {  
            private SimpleProjectPackage package;  
  
            public SimpleProjectNode(SimpleProjectPackage package)  
            {  
                this.package = package;  
            }  
            public override Guid ProjectGuid  
            {  
                get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
            }  
            public override string ProjectType  
            {  
                get { return "SimpleProjectType"; }  
            }  
  
            public override void AddFileFromTemplate(  
                string source, string target)  
            {  
                this.FileTemplateProcessor.UntokenFile(source, target);  
                this.FileTemplateProcessor.Reset();  
            }  
        }  
    }  
    ```  
  
 Questo `SimpleProjectNode` l'implementazione della classe dispone di questi metodi sottoposti a override:  
  
-   `ProjectGuid`, che restituisce la factory del progetto GUID.  
  
-   `ProjectType`, che restituisce il nome localizzato del tipo di progetto.  
  
-   `AddFileFromTemplate`, che consente di copiare i file selezionati dalla cartella di modello per il progetto di destinazione. Inoltre, questo metodo viene implementato in una sezione successiva.  
  
 Il `SimpleProjectNode` costruttore, come il `SimpleProjectFactory` costruttore, memorizza nella cache un `SimpleProjectPackage` riferimento in un campo privato per un utilizzo successivo.  
  
 Per la connessione di `SimpleProjectFactory` classe per il `SimpleProjectNode` \(classe\), è necessario creare un'istanza di un nuovo `SimpleProjectNode` nel `SimpleProjectFactory.CreateProject` \(metodo\) e memorizzarlo nella cache in un campo privato per un utilizzo successivo.  
  
#### Per connettere la classe factory di progetto e la classe del nodo  
  
1.  Aggiungere il codice seguente nel file SimpleProjectFactory.cs `using` istruzione:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2.  Sostituire il `SimpleProjectFactory.CreateProject` metodo utilizzando il codice seguente.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3.  Ricompilare la soluzione e verificare che venga compilato senza errori.  
  
## La classe del nodo di progetto di test  
 La factory del progetto per verificare se crea una gerarchia del progetto di test.  
  
#### Per testare la classe del nodo di progetto  
  
1.  Premere F5 per avviare il debug. Nell'istanza sperimentale, creare un nuovo SimpleProject.  
  
2.  Visual Studio deve chiamare la factory del progetto per creare un progetto.  
  
3.  Chiudere l'istanza sperimentale di Visual Studio.  
  
## Aggiunta di un'icona di nodo di progetto personalizzato  
 L'icona del nodo di progetto nella sezione precedente è un'icona predefinita. È possibile impostarlo su un'icona personalizzata.  
  
#### Per aggiungere un'icona di nodo di progetto personalizzato  
  
1.  Nel **risorse** cartella, aggiungere un file bitmap denominato SimpleProjectNode.bmp.  
  
2.  Nel **proprietà** windows, ridurre la bitmap di 16x16 pixel. Rendere la bitmap distinti.  
  
     ![Comando Progetto semplice](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3.  Nel **proprietà** finestra, modifica il **azione di compilazione** della bitmap a **risorsa incorporata**.  
  
4.  In SimpleProjectNode.cs, aggiungere la seguente `using` istruzioni:  
  
    ```  
    using System.Drawing;  
    using System.Windows.Forms;  
    ```  
  
5.  Aggiungere il seguente campo statico e un costruttore di `SimpleProjectNode` \(classe\).  
  
    ```  
    private static ImageList imageList;  
  
    static SimpleProjectNode()  
    {  
        imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
    }  
    ```  
  
6.  Aggiungere la proprietà seguente all'inizio della `SimpleProjectNode` classe.  
  
    ```  
    internal static int imageIndex;  
       public override int ImageIndex  
       {  
           get { return imageIndex; }  
       }  
    ```  
  
7.  Sostituire il costruttore di istanza con il codice seguente.  
  
    ```  
    public SimpleProjectNode(SimpleProjectPackage package)  
    {  
        this.package = package;  
  
        imageIndex = this.ImageHandler.ImageList.Images.Count;  
  
        foreach (Image img in imageList.Images)  
        {  
            this.ImageHandler.AddImage(img);  
        }  
    }  
    ```  
  
 Durante la costruzione statica, `SimpleProjectNode` Recupera la bitmap di nodo di progetto dalle risorse di manifesto dell'assembly e lo memorizza in un campo privato per un utilizzo successivo. Si noti la sintassi di <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> percorso dell'immagine. Per visualizzare i nomi delle risorse di manifesto incorporate in un assembly, utilizzare il <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metodo. Quando questo metodo viene applicato per il `SimpleProject` assembly, i risultati dovrebbero essere come segue:  
  
-   SimpleProject.Resources.resources  
  
-   VisualStudio.Project.resources  
  
-   SimpleProject.VSPackage.resources  
  
-   Resources.imagelis.bmp  
  
-   Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
-   Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
-   SimpleProject.Resources.SimpleProjectNode.bmp  
  
 Durante la costruzione dell'istanza, la `ProjectNode` classe carica Resources.imagelis.bmp, in cui sono incorporate bitmap di 16x16 comunemente utilizzate da Resources\\imagelis.bmp. Questo elenco bitmap viene reso disponibile a `SimpleProjectNode` come ImageHandler.ImageList.`SimpleProjectNode` Accoda la bitmap di nodo di progetto all'elenco. L'offset della bitmap di nodo di progetto nell'elenco delle immagini viene memorizzato nella cache per un utilizzo successivo come valore della popolazione `ImageIndex` proprietà. Visual Studio utilizza questa proprietà per determinare quali bitmap da visualizzare come icona di nodo del progetto.  
  
## L'icona di nodo di progetto personalizzati di test  
 Testare la factory del progetto per verificare se crea una gerarchia del progetto con icona di nodo di progetto personalizzato.  
  
#### Per testare l'icona di nodo di progetto personalizzato  
  
1.  Avviare il debug e creare un nuovo SimpleProject nell'istanza sperimentale.  
  
2.  Nel progetto appena creato, si noti che SimpleProjectNode.bmp è utilizzata come icona di nodo del progetto.  
  
     ![Progetto semplice, nuovo nodo di progetto](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3.  Aprire Program.cs nell'editor di codice. Verrà visualizzato il codice sorgente che è simile al seguente codice.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
  
    namespace $nameSpace$  
    {  
        public class $className$  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Si noti che i parametri del modello $nameSpace$ e $ $className non dispongono di valori nuovi. Si apprenderà come implementare la sostituzione dei parametri di modello nella sezione successiva.  
  
## Sostituendo i parametri del modello  
 In una sezione precedente, è registrati il modello di progetto in Visual Studio mediante la `ProvideProjectFactory` attributo. Registrare il percorso della cartella modelli in questo modo consente di attivare la sostituzione dei parametri di modello di base viene sottoposto a override ed espandendo la `ProjectNode.AddFileFromTemplate` classe. Per altre informazioni, vedere [Nuova generazione progetto: Dietro le quinte, parte 2](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md).  
  
 A questo punto aggiungere il codice di sostituzione per la `AddFileFromTemplate` classe.  
  
#### Per sostituire i parametri di modello  
  
1.  Aggiungere il codice seguente nel file SimpleProjectNode.cs `using` istruzione.  
  
    ```  
    using System.IO;  
    ```  
  
2.  Sostituire il `AddFileFromTemplate` metodo utilizzando il codice seguente.  
  
    ```  
    public override void AddFileFromTemplate(  
        string source, string target)  
    {  
        string nameSpace =   
            this.FileTemplateProcessor.GetFileNamespace(target, this);  
        string className = Path.GetFileNameWithoutExtension(target);  
  
        this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);  
        this.FileTemplateProcessor.AddReplace("$className$", className);  
  
        this.FileTemplateProcessor.UntokenFile(source, target);  
        this.FileTemplateProcessor.Reset();  
    }  
    ```  
  
3.  Impostare un punto di interruzione nel metodo subito dopo il `className` istruzione di assegnazione.  
  
 Le istruzioni di assegnazione determinano i valori accettabili per uno spazio dei nomi e un nuovo nome di classe. I due `ProjectNode.FileTemplateProcessor.AddReplace` chiamate al metodo sostituire i valori di parametro corrispondente del modello utilizzando i nuovi valori.  
  
## La sostituzione dei parametri di modello di test  
 È ora possibile testare la sostituzione dei parametri di modello.  
  
#### Per testare la sostituzione dei parametri di modello  
  
1.  Avviare il debug e creare un nuovo SimpleProject nell'istanza sperimentale.  
  
2.  L'esecuzione viene arrestata nel punto di interruzione di `AddFileFromTemplate` metodo.  
  
3.  Esaminare i valori per il `nameSpace` e `className` i parametri.  
  
    -   `nameSpace` viene assegnato il valore dell'elemento \< RootNamespace \> nel file del modello di progetto \\Templates\\Projects\\SimpleProject\\SimpleProject.myproj. In questo caso, il valore è "MyRootNamespace".  
  
    -   `className` viene assegnato il valore del nome file sorgente della classe, senza l'estensione del nome file. In questo caso, il primo file da copiare nella cartella di destinazione è AssemblyInfo.cs; Pertanto, il valore di className è "AssemblyInfo".  
  
4.  Rimuovere il punto di interruzione e premere F5 per continuare l'esecuzione.  
  
     Visual Studio deve completare la creazione di un progetto.  
  
5.  Aprire Program.cs nell'editor di codice. Verrà visualizzato il codice sorgente che è simile al seguente codice.  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace MyRootNamespace  
    {  
        public class Program  
        {  
            static void Main(string[] args)  
            {  
                Console.WriteLine("Hello VSX!!!");  
                Console.ReadKey();  
            }  
        }  
    }  
    ```  
  
     Si noti che lo spazio dei nomi è ora "MyRootNamespace" e il nome della classe è ora "Programma".  
  
6.  Avviare il debug del progetto. Il nuovo progetto deve compilare, eseguire e visualizzare "Hello VSX." Nella finestra della console.  
  
     ![Comando Progetto semplice](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
 La procedura è stata completata. È stato implementato un sistema di base del progetto gestito.