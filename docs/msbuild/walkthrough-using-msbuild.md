---
title: "Procedura dettagliata: utilizzo di MSBuild | Microsoft Docs"
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
  - "MSBuild, esercitazione"
ms.assetid: b8a8b866-bb07-4abf-b9ec-0b40d281c310
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura dettagliata: utilizzo di MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild è la piattaforma di compilazione per Microsoft e Visual Studio. Questa procedura dettagliata illustra i blocchi predefiniti di MSBuild e viene illustrato come scrivere, modificare ed eseguire il debug di progetti MSBuild. Si apprenderà:  
  
-   Creazione e modifica di un file di progetto.  
  
-   Procedura: utilizzare le proprietà di compilazione  
  
-   Come utilizzare gli elementi di compilazione.  
  
 È possibile eseguire MSBuild da Visual Studio o dalla finestra di comando. In questa procedura dettagliata, si crea un file di progetto MSBuild in Visual Studio. Modificare il file di progetto in Visual Studio e utilizzare una finestra di comando per compilare il progetto ed esaminare i risultati.  
  
## <a name="creating-an-msbuild-project"></a>Creazione di un progetto MSBuild  
 Il sistema di progetto Visual Studio è basato su MSBuild. Questo rende facile creare un nuovo file di progetto in Visual Studio. In questa sezione è creare un file di progetto Visual c#. È possibile scegliere di creare un file di progetto Visual Basic. Nel contesto di questa procedura dettagliata, la differenza tra i due file di progetto è trascurabili.  
  
#### <a name="to-create-a-project-file"></a>Per creare un file di progetto  
  
1.  Aprire Visual Studio.  
  
2.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
3.  Nel **Nuovo progetto** la finestra di dialogo, selezionare Visual c# tipo di progetto e quindi selezionare il **applicazione Windows Form** modello. Nel **nome** digitare `BuildApp`. Immettere un **percorso** per la soluzione, ad esempio, `D:\`. Accettare le impostazioni predefinite per **Crea directory per soluzione** (selezionata), **aggiungere al controllo del codice sorgente** (non selezionato), e **Nome soluzione** (`BuildApp`).  
  
     Fare clic su **OK** per creare il file di progetto.  
  
## <a name="examining-the-project-file"></a>Esaminare il File di progetto  
 Nella sezione precedente, è utilizzato Visual Studio per creare un file di progetto Visual c#. Il file di progetto viene rappresentato in **Esplora** dal nodo di progetto denominato BuildApp. È possibile utilizzare l'editor di codice di Visual Studio per esaminare il file di progetto.  
  
#### <a name="to-examine-the-project-file"></a>Per esaminare il file di progetto  
  
1.  In **Esplora**, fare clic sul nodo di progetto BuildApp.  
  
2.  Nel **proprietà** browser, si noti che il **File di progetto** proprietà è BuildApp. Tutti i file di progetto vengono denominati con il suffisso "proj". Se è stato creato un progetto Visual Basic, il nome di file di progetto sarebbe BuildApp.  
  
3.  Pulsante destro del mouse sul nodo del progetto, quindi fare clic su **Scarica progetto**.  
  
4.  Fare nuovamente clic sul nodo del progetto, quindi fare clic su **Modifica BuildApp**.  
  
     Il file di progetto viene visualizzato nell'editor di codice.  
  
## <a name="targets-and-tasks"></a>Destinazioni e attività  
 File di progetto sono file in formato XML con il nodo radice [progetto](../msbuild/project-element-msbuild.md).  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<Project ToolsVersion="12.0" DefaultTargets="Build"  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 È necessario specificare lo spazio dei nomi xmlns nell'elemento di progetto.  
  
 L'operazione di compilazione di un'applicazione viene eseguita con [destinazione](../msbuild/target-element-msbuild.md) e [attività](../msbuild/task-element-msbuild.md) elementi.  
  
-   Un'attività è la più piccola unità di lavoro, in altre parole, il "atom" di una compilazione. Le attività sono componenti eseguibili indipendenti che potrebbero essere input e output. Non sono presenti attività definita nel file di progetto o fare riferimento a attualmente. Aggiungere attività al file di progetto nelle sezioni seguenti. Per ulteriori informazioni, vedere il [attività](../msbuild/msbuild-tasks.md) argomento.  
  
-   Una destinazione è una sequenza denominata di attività. Esistono due destinazioni alla fine del file di progetto che attualmente sono racchiusi tra i commenti HTML: BeforeBuild e AfterBuild.  
  
    ```  
    <Target Name="BeforeBuild">  
    </Target>  
    <Target Name="AfterBuild">  
    </Target>  
    ```  
  
     Per ulteriori informazioni, vedere il [destinazioni](../msbuild/msbuild-targets.md) argomento.  
  
 Il nodo del progetto ha un attributo DefaultTargets facoltativo che consente di selezionare la destinazione predefinita per compilare, in questo caso Build.  
  
```  
<Project ToolsVersion="12.0" DefaultTargets="Build" ...  
```  
  
 La destinazione di compilazione non è definita nel file di progetto. Al contrario, viene importato dal file Microsoft.CSharp.targets usando la [importazione](../msbuild/import-element-msbuild.md) elemento.  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 I file importati vengono inseriti in modo efficace nel file di progetto quando viene fatto riferimento.  
  
 Tiene traccia delle destinazioni di una compilazione di MSBuild e garantisce che ogni destinazione venga compilata non più di una volta.  
  
## <a name="adding-a-target-and-a-task"></a>Aggiunta di una destinazione e un'attività  
 Aggiungere una destinazione per il file di progetto. Aggiungere un'attività di destinazione che visualizza un messaggio.  
  
#### <a name="to-add-a-target-and-a-task"></a>Per aggiungere una destinazione e un'attività  
  
1.  Aggiungere le righe seguenti al file di progetto, subito dopo l'istruzione Import:  
  
    ```  
    <Target Name="HelloWorld">  
    </Target>  
    ```  
  
     Verrà creata una destinazione denominata HelloWorld. Si noti che è necessario il supporto Intellisense durante la modifica del file di progetto.  
  
2.  Aggiungere righe alla destinazione HelloWorld in modo che la sezione risulta è simile al seguente:  
  
    ```  
    <Target Name="HelloWorld">  
      <Message Text="Hello"></Message>  <Message Text="World"></Message>  
    </Target>  
    ```  
  
3.  Salvare il file di progetto.  
  
 L'attività Message è una delle tante attività che viene fornito con MSBuild. Per un elenco completo delle attività disponibili e informazioni sull'utilizzo, vedere [riferimenti alle attività](../msbuild/msbuild-task-reference.md).  
  
 L'attività Message accetta il valore di stringa dell'attributo di testo come input e lo visualizza nella periferica di output. La destinazione HelloWorld esegue l'attività Message due volte: prima di tutto per visualizzare "Hello" e quindi di visualizzare "World".  
  
## <a name="building-the-target"></a>Compilazione di destinazione  
 Eseguire MSBuild dal **Prompt dei comandi di Visual Studio** per compilare la destinazione HelloWorld definita in precedenza. Utilizzare l'opzione della riga di comando /target o /t. per selezionare la destinazione.  
  
> [!NOTE]
>  Si farà riferimento a di **Prompt dei comandi di Visual Studio** come il **finestra di comando** nelle sezioni seguenti.  
  
#### <a name="to-build-the-target"></a>Per compilare la destinazione  
  
1.  Fare clic su **avviare**, quindi fare clic su **tutti i programmi**. Individuare e selezionare il **Prompt dei comandi di Visual Studio** nel **Visual Studio Tools** cartella.  
  
2.  Al prompt dei comandi, passare alla cartella contenente il file di progetto, in questo caso, D:\BuildApp\BuildApp.  
  
3.  Eseguire msbuild con /t: HelloWorld l'opzione di comando. Consente di selezionare e compila la destinazione HelloWorld:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output di **finestra di comando**. Dovrebbe essere due righe "Hello" e "World":  
  
    ```  
    Hello  
    World  
    ```  
  
> [!NOTE]
>  Se viene visualizzato invece `The target "HelloWorld" does not exist in the project` quindi probabilmente salvare il file di progetto nell'editor di codice. Salvare il file e riprovare.  
  
 Se si passa alternativamente tra l'editor di codice e la finestra di comando, è possibile modificare il file di progetto e visualizzare rapidamente i risultati.  
  
> [!NOTE]
>  Se si esegue msbuild senza l'opzione di comando /t, msbuild compila la destinazione specificata dall'attributo DefaultTarget dell'elemento di progetto, in questo caso "Build". Verrà compilata l'applicazione Windows Form BuildApp.exe.  
  
## <a name="build-properties"></a>Proprietà di compilazione  
 Proprietà di compilazione sono coppie nome-valore che determinano la compilazione. Diverse proprietà di compilazione sono già definite nella parte superiore del file di progetto:  
  
```  
<PropertyGroup>  
...  
  <ProductVersion>10.0.11107</ProductVersion>  
  <SchemaVersion>2.0</SchemaVersion>  
  <ProjectGuid>{30E3C9D5-FD86-4691-A331-80EA5BA7E571}</ProjectGuid>  
  <OutputType>WinExe</OutputType>  
...  
</PropertyGroup>  
```  
  
 Tutte le proprietà sono elementi figlio degli elementi PropertyGroup. Il nome della proprietà è il nome dell'elemento figlio e il valore della proprietà è l'elemento di testo dell'elemento figlio. Di seguito è riportato un esempio:  
  
```  
<TargetFrameworkVersion>v12.0</TargetFrameworkVersion>  
```  
  
 definisce la proprietà denominata TargetFrameworkVersion, assegnandogli il valore della stringa "v 12.0".  
  
 Compilare le proprietà possono essere ridefinite in qualsiasi momento. Se  
  
```  
<TargetFrameworkVersion>v3.5</TargetFrameworkVersion>  
```  
  
 viene visualizzata in un secondo momento nel file di progetto o in un file importato in un secondo momento nel file di progetto, TargetFrameworkVersion assume il nuovo valore "v 3.5".  
  
## <a name="examining-a-property-value"></a>Esame di un valore di proprietà  
 Per ottenere il valore di una proprietà, utilizzare la sintassi seguente, dove PropertyName è il nome della proprietà:  
  
```  
$(PropertyName)  
```  
  
 Utilizzare questa sintassi per esaminare alcune delle proprietà nel file di progetto.  
  
#### <a name="to-examine-a-property-value"></a>Per esaminare un valore di proprietà  
  
1.  Nell'editor di codice, sostituire la destinazione HelloWorld con questo codice:  
  
    ```  
    <Target Name="HelloWorld">  
      <Message Text="Configuration is $(Configuration)" />  
      <Message Text="MSBuildToolsPath is $(MSBuildToolsPath)" />  
    </Target>  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output. Dovrebbe essere queste due righe (la versione di .NET Framework può variare):  
  
    ```  
    Configuration is Debug  
    MSBuildToolsPath is C:\Program Files\MSBuild\12.0\bin  
    ```  
  
> [!NOTE]
>  Se queste righe non è visibile, probabilmente salvare il file di progetto nell'editor di codice. Salvare il file e riprovare.  
  
### <a name="conditional-properties"></a>Proprietà condizionale  
 Molte proprietà come configurazione vengono definite in modo condizionale, vale a dire l'attributo di condizione viene visualizzato nell'elemento property. Proprietà condizionale sono state definite o ridefinita solo se la condizione restituisce "true". Si noti che alle proprietà non definite viene assegnato il valore predefinito di una stringa vuota. Di seguito è riportato un esempio:  
  
```  
<Configuration   Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 significa "Se la proprietà di configurazione non è ancora stata definita, definirlo e assegnargli il valore 'Debug'".  
  
 Quasi tutti gli elementi di MSBuild possono avere un attributo Condition. Per ulteriori informazioni sull'utilizzo dell'attributo Condition, vedere [condizioni](../msbuild/msbuild-conditions.md).  
  
### <a name="reserved-properties"></a>Proprietà riservate  
 In MSBuild alcuni nomi di proprietà sono riservati per archiviare le informazioni relative al file di progetto e ai file binari di MSBuild. MSBuildToolsPath è riportato un esempio di proprietà riservata. Proprietà riservate viene fatto riferimento con la notazione $ come qualsiasi altra proprietà. Per ulteriori informazioni, vedere [procedura: fare riferimento al nome o percorso del File di progetto](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) e [MSBuild riservate e proprietà note](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
### <a name="environment-variables"></a>Variabili di ambiente  
 È possibile fare riferimento le variabili di ambiente nel file di progetto come proprietà di compilazione. Ad esempio, per utilizzare la variabile di ambiente PATH nel file di progetto, utilizzare $(percorso). Se il progetto contiene una definizione di proprietà con lo stesso nome di una variabile di ambiente, la proprietà del progetto sostituisce il valore della variabile di ambiente. Per ulteriori informazioni, vedere [procedura: utilizzare le variabili di ambiente in una Build di](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md).  
  
## <a name="setting-properties-from-the-command-line"></a>Impostazione delle proprietà dalla riga di comando  
 Le proprietà possono essere definite dalla riga di comando tramite l'opzione della riga di comando /property o/p. I valori di proprietà ricevuti dalla riga di comando eseguire l'override di valori di proprietà impostati nelle variabili di ambiente e i file di progetto.  
  
#### <a name="to-set-a-property-value-from-the-command-line"></a>Per impostare un valore della proprietà dalla riga di comando  
  
1.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld /p:Configuration=Release  
    ```  
  
2.  Esaminare l'output. Verrà visualizzata la seguente riga:  
  
    ```  
    Configuration is Release.  
    ```  
  
 MSBuild crea la proprietà di configurazione e assegna il valore "Rilascio".  
  
## <a name="special-characters"></a>Caratteri speciali  
 Alcuni caratteri hanno un significato speciale nei file di progetto MSBuild. Sono esempi di questi caratteri punto e virgola (;) e l'asterisco (*). Per utilizzare questi caratteri speciali come valori letterali in un file di progetto, è necessario specificarli tramite la sintassi % xx, dove xx rappresenta il valore ASCII esadecimale del carattere.  
  
 Modificare l'attività messaggio per visualizzare il valore della proprietà di configurazione con caratteri speciali per renderlo più leggibile.  
  
#### <a name="to-use-special-characters-in-the-message-task"></a>Utilizzare caratteri speciali nell'attività Message  
  
1.  Nell'editor di codice, sostituire entrambe le attività di messaggio con la riga seguente:  
  
    ```  
    <Message Text="%24(Configuration) is %22$(Configuration)%22" />  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output. Verrà visualizzata la seguente riga:  
  
    ```  
    $(Configuration) is "Debug"  
    ```  
  
 Per ulteriori informazioni, vedere [caratteri speciali di MSBuild](../msbuild/msbuild-special-characters.md).  
  
## <a name="build-items"></a>Gli elementi di compilazione  
 Un elemento è costituito da informazioni, in genere un nome file, che viene utilizzato come input per il sistema di compilazione. Ad esempio, una raccolta di elementi che rappresentano i file di origine può essere passata a un'attività denominata Compile per compilarle in un assembly.  
  
 Tutti gli elementi sono elementi figlio degli elementi ItemGroup. Il nome dell'elemento è il nome dell'elemento figlio e il valore dell'elemento è il valore dell'attributo Include dell'elemento figlio. I valori degli elementi con lo stesso nome vengono raccolti in tipi di elemento di tale nome.  Di seguito è riportato un esempio:  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs" />  
    <Compile Include="Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 definisce un gruppo di elementi contenente due elementi. Il tipo di elemento di compilazione dispone di due valori: "Program.cs" e "Properties \ AssemblyInfo.cs".  
  
 Il codice seguente crea lo stesso tipo di elemento dichiarando entrambi i file in un unico attributo Include, separati da un punto e virgola.  
  
```  
<ItemGroup>  
    <Compile Include="Program.cs;Properties\AssemblyInfo.cs" />  
</ItemGroup>  
```  
  
 Per ulteriori informazioni, vedere [elementi](../msbuild/msbuild-items.md).  
  
> [!NOTE]
>  Percorsi dei file sono relativo alla cartella contenente il file di progetto MSBuild.  
  
## <a name="examining-item-type-values"></a>Esaminare i valori di tipo di elemento  
 Per ottenere i valori di un tipo di elemento, utilizzare la sintassi seguente, dove ItemType è il nome del tipo di elemento:  
  
```  
@(ItemType)  
```  
  
 Utilizzare questa sintassi per esaminare il tipo di elemento di compilazione nel file di progetto.  
  
#### <a name="to-examine-item-type-values"></a>Per esaminare i valori di tipo di elemento  
  
1.  Nell'editor di codice, sostituire l'attività di destinazione HelloWorld con questo codice:  
  
    ```  
    <Target Name="HelloWorld">  
      <Message Text="Compile item type contains @(Compile)" />  
    </Target>  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output. Verrà visualizzata la riga lunga:  
  
    ```  
    Compile item type contains Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs  
    ```  
  
 Per impostazione predefinita, i valori di un tipo di elemento sono separati da punti e virgola.  
  
 Per modificare il separatore di un tipo di elemento, utilizzare la sintassi seguente, dove ItemType è il tipo di elemento e Separator è una stringa di uno o più caratteri di separazione:  
  
```  
@(ItemType, Separator)  
```  
  
 Modificare l'attività messaggio per l'utilizzo ritorni a capo e avanzamento riga (% 0A %0d) per visualizzare compilazione elementi uno per riga.  
  
#### <a name="to-display-item-type-values-one-per-line"></a>Per visualizzare il tipo di elemento valori uno per riga  
  
1.  Nell'editor di codice, sostituire l'attività Message con la riga seguente:  
  
    ```  
    <Message Text="Compile item type contains @(Compile, '%0A%0D')" />  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
     `msbuild buildapp.csproj /t:HelloWorld`  
  
4.  Esaminare l'output. Dovrebbe essere le seguenti righe:  
  
    ```  
    Compile item type contains Form1.cs  
    Form1.Designer.cs  
    Program.cs  
    Properties\AssemblyInfo.cs  
    Properties\Resources.Designer.cs  
    Properties\Settings.Designer.cs  
    ```  
  
### <a name="include-exclude-and-wildcards"></a>Includere, escludere e i caratteri jolly  
 È possibile utilizzare i caratteri jolly "*","\*\*", e "?" con l'attributo di inclusione per aggiungere elementi a un tipo di elemento. Di seguito è riportato un esempio:  
  
```  
<Photos Include="images\*.jpeg" />  
```  
  
 Aggiunge tutti i file con estensione "JPEG" nella cartella immagini per il tipo di elemento di foto, mentre  
  
```  
<Photos Include="images\**.jpeg" />  
```  
  
 Aggiunge tutti i file con estensione "JPEG" nella cartella immagini e le relative sottocartelle, al tipo di elemento di foto. Per ulteriori esempi, vedere [procedura: selezionare i file da compilare](../msbuild/how-to-select-the-files-to-build.md).  
  
 Si noti che sono dichiarati gli elementi vengono aggiunti al tipo di elemento. Di seguito è riportato un esempio:  
  
```  
<Photos Include="images\*.jpeg" />  
<Photos Include="images\*.gif" />  
```  
  
 Crea un tipo di elemento denominato Photo contenente tutti i file nella cartella delle immagini con estensione "JPEG" o "gif". Ciò equivale alla riga seguente:  
  
```  
<Photos Include="images\*.jpeg;images\*.gif" />  
```  
  
 È possibile escludere un elemento da un tipo di elemento con l'attributo Exclude. Di seguito è riportato un esempio:  
  
```  
<Compile Include="*.cs" Exclude="*Designer*">  
```  
  
 Aggiunge tutti i file con estensione"cs" all'elemento di compilazione digitare, ad eccezione di file i cui nomi contengono la stringa "Designer". Per ulteriori esempi, vedere [procedura: escludere file dalla compilazione](../msbuild/how-to-exclude-files-from-the-build.md).  
  
 L'attributo Exclude influisce solo sugli elementi aggiunti dall'attributo Include nell'elemento item che li contiene entrambi. Di seguito è riportato un esempio:  
  
```  
<Compile Include="*.cs" />  
<Compile Include="*.res" Exclude="Form1.cs">  
```  
  
 non escludere il file Form1. cs, aggiunto nell'elemento item precedente.  
  
##### <a name="to-include-and-exclude-items"></a>Per includere ed escludere elementi  
  
1.  Nell'editor di codice, sostituire l'attività Message con la riga seguente:  
  
    ```  
    <Message Text="Compile item type contains @(XFiles)" />  
    ```  
  
2.  Aggiungere questo gruppo di articoli immediatamente dopo l'elemento di importazione:  
  
    ```  
    <ItemGroup>  
       <XFiles Include="*.cs;properties/*.resx" Exclude="*Designer*" />  
    </ItemGroup>  
    ```  
  
3.  Salvare il file di progetto.  
  
4.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
5.  Esaminare l'output. Verrà visualizzata la seguente riga:  
  
    ```  
    Compile item type contains Form1.cs;Program.cs;Properties/Resources.resx  
    ```  
  
## <a name="item-metadata"></a>Metadati dell'elemento  
 Gli elementi possono contenere metadati oltre alle informazioni raccolte dagli attributi Include ed Exclude. Questo metadati possono essere utilizzati dalle attività che richiedono ulteriori informazioni sugli elementi più semplicemente il valore dell'elemento.  
  
 Metadati dell'elemento sono dichiarato nel file di progetto mediante la creazione di un elemento con il nome dei metadati come elemento figlio dell'elemento. Un elemento può avere zero o più valori di metadati. Ad esempio, l'elemento CSFile seguente contiene i metadati delle impostazioni cultura con un valore di "Fr":  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs">  
        <Culture>Fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
 Per ottenere il valore dei metadati di un tipo di elemento, utilizzare la sintassi seguente, dove ItemType è il nome del tipo di elemento e MetaDataName è il nome dei metadati:  
  
```  
%(ItemType.MetaDataName)  
```  
  
#### <a name="to-examine-item-metadata"></a>Per esaminare i metadati di elemento  
  
1.  Nell'editor di codice, sostituire l'attività Message con la riga seguente:  
  
    ```  
    <Message Text="Compile.DependentUpon: %(Compile.DependentUpon)" />  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output. Dovrebbe essere le seguenti righe:  
  
    ```  
    Compile.DependentUpon:  
    Compile.DependentUpon: Form1.cs  
    Compile.DependentUpon: Resources.resx  
    Compile.DependentUpon: Settings.settings  
    ```  
  
 Si noti come la frase "DependentUpon" viene visualizzato più volte. L'utilizzo di metadati con questa sintassi all'interno di una destinazione provoca "batch". Ciò significa che le attività all'interno della destinazione vengono eseguite una volta per ogni valore univoco dei metadati. Questo è l'equivalente di script MSBuild comuni ciclo"for" programmazione costrutto. Per ulteriori informazioni, vedere [batch](../msbuild/msbuild-batching.md).  
  
### <a name="well-known-metadata"></a>Metadati noti  
 Ogni volta che un elemento viene aggiunto a un elenco di elementi, tale elemento vengono assegnati metadati noti. Ad esempio, % (FileName) restituisce il nome del file di qualsiasi elemento. Per un elenco completo di tutti i metadati noti, vedere [Well-Known metadati dell'elemento](../msbuild/msbuild-well-known-item-metadata.md).  
  
##### <a name="to-examine-well-known-metadata"></a>Per esaminare i metadati noti  
  
1.  Nell'editor di codice, sostituire l'attività Message con la riga seguente:  
  
    ```  
    <Message Text="Compile Filename: %(Compile.Filename)" />  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output. Dovrebbe essere le seguenti righe:  
  
    ```  
    Compile Filename: Form1  
    Compile Filename: Form1.Designer  
    Compile Filename: Program  
    Compile Filename: AssemblyInfo  
    Compile Filename: Resources.Designer  
    Compile Filename: Settings.Designer  
    ```  
  
 Confrontando i due esempi precedenti, è possibile visualizzare anche se non tutti gli elementi nel tipo di elemento di compilazione sono metadati DependentUpon, tutti gli elementi presentano metadati noti Filename.  
  
### <a name="metadata-transformations"></a>Trasformazioni dei metadati  
 Elenchi di elementi possono essere trasformati in nuovi elenchi di elementi. Per trasformare un elenco di elementi, utilizzare la sintassi seguente, dove ItemType è il nome del tipo di elemento e MetadataName è il nome dei metadati:  
  
```  
@(ItemType -> '%(MetadataName)')  
```  
  
 Ad esempio, un elenco di elementi dei file di origine può essere trasformato in una raccolta di file oggetto utilizzando un'espressione come `@(SourceFiles -> '%(Filename).obj')`. Per ulteriori informazioni, vedere [Trasforma](../msbuild/msbuild-transforms.md).  
  
##### <a name="to-transform-items-using-metadata"></a>Per trasformare gli elementi utilizzando i metadati  
  
1.  Nell'editor di codice, sostituire l'attività Message con la riga seguente:  
  
    ```  
    <Message Text="Backup files: @(Compile->'%(filename).bak')" />  
    ```  
  
2.  Salvare il file di progetto.  
  
3.  Dal **finestra di comando**, immettere ed eseguire la seguente riga:  
  
    ```  
    msbuild buildapp.csproj /t:HelloWorld  
    ```  
  
4.  Esaminare l'output. Verrà visualizzata la seguente riga:  
  
    ```  
    Backup files: Form1.bak;Form1.Designer.bak;Program.bak;AssemblyInfo.bak;Resources.Designer.bak;Settings.Designer.bak  
    ```  
  
 Si noti che i metadati espressi in questa sintassi non determina l'invio in batch.  
  
## <a name="whats-next"></a>Argomenti successivi  
 Per informazioni su come creare un passaggio di un file di progetto semplice alla volta, provare il [procedura dettagliata: creazione di un File di progetto MSBuild da zero](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
## <a name="see-also"></a>Vedere anche
[Cenni preliminari su MSBuild](../msbuild/msbuild1.md)  
 [Riferimenti di MSBuild](../msbuild/msbuild-reference.md)