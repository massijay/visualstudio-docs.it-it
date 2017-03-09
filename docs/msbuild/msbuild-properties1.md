---
title: "Properties1 di MSBuild | Microsoft Docs"
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
  - "MSBuild, proprietà"
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
caps.latest.revision: 32
caps.handback.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Properties1 di MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le proprietà sono coppie nome-valore che possono essere utilizzate per configurare le compilazioni. Le proprietà sono utili per passare valori alle attività, la valutazione di condizioni e la memorizzazione di valori che si farà riferimento nel file di progetto.  
  
## <a name="defining-and-referencing-properties-in-a-project-file"></a>Definizione e fare riferimento alle proprietà in un File di progetto  
 Le proprietà vengono dichiarate tramite la creazione di un elemento con il nome della proprietà come figlio di un [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elemento. Ad esempio, il codice XML seguente viene creata una proprietà denominata `BuildDir` che ha un valore di `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 File di progetto, le proprietà vengono fatto riferimento utilizzando la sintassi $(`PropertyName`). Ad esempio, la proprietà nell'esempio precedente fa riferimento tramite $(BuildDir).  
  
 I valori delle proprietà possono essere modificati ridefinendo la proprietà. Il `BuildDir` proprietà può essere assegnato un nuovo valore utilizzando il codice XML:  
  
```  
<PropertyGroup>  
    <BuildDir>Alternate</BuildDir>  
</PropertyGroup>  
```  
  
 Le proprietà vengono valutate nell'ordine in cui appaiono nel file di progetto. Il nuovo valore per `BuildDir` deve essere dichiarato dopo che è assegnato il valore precedente.  
  
## <a name="reserved-properties"></a>Proprietà riservate  
 In MSBuild alcuni nomi di proprietà sono riservati per archiviare le informazioni relative al file di progetto e ai file binari di MSBuild. Queste proprietà vengono fatto riferimento utilizzando la notazione $, esattamente come qualsiasi altra proprietà. Ad esempio, $ (MSBuildProjectFile) restituisce il nome file completo del file di progetto, inclusa l'estensione di nome file.  
  
 Per ulteriori informazioni, vedere [procedura: fare riferimento al nome o percorso del File di progetto](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md) e [MSBuild riservate e proprietà note](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="environment-properties"></a>Proprietà di ambiente  
 È possibile fare riferimento le variabili di ambiente nel file di progetto così come si fa riferimento la proprietà riservata. Ad esempio, per usare il `PATH` variabile di ambiente nel file di progetto, utilizzare $(percorso). Se il progetto contiene una definizione di proprietà con lo stesso nome di una proprietà di ambiente, la proprietà del progetto sostituisce il valore della variabile di ambiente.  
  
 A ogni progetto MSBuild è associato un blocco di ambiente isolato: nel relativo blocco personalizzato sono visualizzate solo le letture e le scritture.  Tramite MSBuild vengono lette le variabili di ambiente solo durante l'inizializzazione della raccolta di proprietà, prima che il file di progetto venga valutato o compilato. Successivamente, le proprietà dell'ambiente sono statiche, cioè ciascuno strumento generato inizia con gli stessi nomi e valori.  
  
 Per ottenere il valore corrente delle variabili di ambiente all'interno di uno strumento generato, utilizzare il [funzioni di proprietà](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable. Il metodo consigliato, tuttavia, è utilizzare il parametro dell'attività <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>. Le proprietà dell'ambiente impostate in questa matrice di stringhe possono essere passate allo strumento generato senza influire sulle variabili di ambiente del sistema.  
  
> [!TIP]
>  Non tutte le variabili di ambiente vengono lette per diventare proprietà iniziali. Qualsiasi variabile di ambiente il cui nome non è un nome di proprietà di MSBuild valido, ad esempio "386", viene ignorata.  
  
 Per ulteriori informazioni, vedere [procedura: utilizzare le variabili di ambiente in una Build di](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md).  
  
## <a name="registry-properties"></a>Proprietà del Registro di sistema  
 È possibile leggere valori del Registro di sistema utilizzando la sintassi seguente, dove `Hive` è l'hive del Registro di sistema (ad esempio HKEY_LOCAL_MACHINE), `Key` è il nome della chiave, `SubKey` è il nome della sottochiave e `Value` è il valore della sottochiave.  
  
```  
$(registry:Hive\MyKey\MySubKey@Value)  
```  
  
 Per ottenere il valore predefinito della sottochiave, omettere il `Value`.  
  
```  
$(registry:Hive\MyKey\MySubKey)  
```  
  
 Questo valore del Registro di sistema può essere utilizzato per inizializzare una proprietà di compilazione. Ad esempio, per creare una proprietà di compilazione che rappresenta la home page di Visual Studio web browser, utilizzare questo codice:  
  
```  
<PropertyGroup>  
  <VisualStudioWebBrowserHomePage>  
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\12.0\WebBrowser@HomePage)  
  </VisualStudioWebBrowserHomePage>  
<PropertyGroup>  
```  
  
## <a name="global-properties"></a>Proprietà globali  
 MSBuild consente di impostare le proprietà della riga di comando utilizzando il **/property** (o **/p**) passare. Questi valori di proprietà globale ignorare i valori delle proprietà impostate nel file di progetto. Include le proprietà di ambiente, ma non include le proprietà riservate, non possono essere modificate.  
  
 Nell'esempio seguente imposta globale `Configuration` proprietà `DEBUG`.  
  
```  
msbuild.exe MyProj.proj /p:Configuration=DEBUG  
```  
  
 Proprietà globali possono essere impostate o modificate per i progetti figlio in una compilazione con più progetti mediante l'utilizzo di `Properties` attributo dell'attività di MSBuild. Per ulteriori informazioni, vedere [attività MSBuild](../msbuild/msbuild-task.md).  
  
 Se si specifica una proprietà utilizzando l'attributo `TreatAsLocalProperty` in un tag di progetto, con il valore di quella proprietà globale non verrà sovrascritto il valore della proprietà impostata nel file di progetto. Per ulteriori informazioni, vedere [elemento Project (MSBuild)](../msbuild/project-element-msbuild.md) e [procedura: compilare gli stessi file di origine con opzioni diverse](../Topic/How%20to:%20Build%20the%20Same%20Source%20Files%20with%20Different%20Options.md).  
  
## <a name="property-functions"></a>Funzioni delle proprietà  
 A partire da .NET Framework versione 4 è possibile utilizzare funzioni delle proprietà per valutare gli script MSBuild. È possibile leggere l'ora di sistema, confrontare le stringhe, corrispondenza per espressioni regolari ed eseguire molte altre azioni all'interno dello script di compilazione senza utilizzare le attività di MSBuild.  
  
 È possibile utilizzare i metodi stringa (istanza) consente di operare su qualsiasi valore della proprietà e chiamare i metodi statici di molte classi di sistema. Ad esempio, è possibile impostare una proprietà di compilazione sulla data corrente come indicato di seguito.  
  
```  
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>  
```  
  
 Per ulteriori informazioni e un elenco di funzioni di proprietà, vedere [funzioni di proprietà](../msbuild/property-functions.md).  
  
## <a name="creating-properties-during-execution"></a>Creazione di proprietà durante l'esecuzione  
 Proprietà di fuori `Target` elementi vengono assegnati valori durante la fase di valutazione di una compilazione. Durante la fase di esecuzione successiva, le proprietà possono essere create o modificate come indicato di seguito:  
  
-   Una proprietà può essere generata da qualsiasi attività. Per creare una proprietà, il [attività](../msbuild/task-element-msbuild.md) elemento deve disporre di un elemento figlio [Output](../msbuild/output-element-msbuild.md) elemento che dispone di un `PropertyName` attributo.  
  
-   Una proprietà può essere generata dal [CreateProperty](../msbuild/createproperty-task.md) attività. Questo utilizzo è deprecato.  
  
-   A partire da .NET Framework 3.5, `Target` possono contenere elementi `PropertyGroup` elementi che possono contenere dichiarazioni di proprietà.  
  
## <a name="storing-xml-in-properties"></a>Archiviazione XML nella finestra delle proprietà  
 Le proprietà possono contenere contenuto XML arbitrario, che possono essere utili durante il passaggio di valori alle attività o la visualizzazione delle informazioni di registrazione. Nell'esempio seguente il `ConfigTemplate` proprietà, che ha un valore che contiene XML e altre proprietà riferimenti. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sostituisce i riferimenti di proprietà utilizzando i valori delle rispettive proprietà. Vengono assegnati i valori delle proprietà nell'ordine in cui appaiono. Pertanto, in questo esempio, `$(MySupportedVersion)`, `$(MyRequiredVersion)`, e `$(MySafeMode)` dovrebbe già definiti.  
  
```  
  
<PropertyGroup>  
    <ConfigTemplate>  
        <Configuration>  
            <Startup>  
                <SupportedRuntime  
                    ImageVersion="$(MySupportedVersion)"  
                    Version="$(MySupportedVersion)"/>  
                <RequiredRuntime  
                    ImageVersion="$(MyRequiredVersion)  
                    Version="$(MyRequiredVersion)"  
                    SafeMode="$(MySafeMode)"/>  
            </Startup>  
        </Configuration>  
    </ConfigTemplate>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)  
 [MSBuild](../msbuild/msbuild1.md)  
 [Procedura: utilizzare variabili di ambiente in una compilazione](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md)   
 [Procedura: fare riferimento al nome o percorso del File di progetto](../Topic/How%20to:%20Reference%20the%20Name%20or%20Location%20of%20the%20Project%20File.md)   
 [Procedura: compilare gli stessi file di origine con opzioni diverse](../Topic/How%20to:%20Build%20the%20Same%20Source%20Files%20with%20Different%20Options.md)   
 [MSBuild proprietà riservate e note](../msbuild/msbuild-reserved-and-well-known-properties.md)   
 [Elemento Property (MSBuild)](../msbuild/property-element-msbuild.md)