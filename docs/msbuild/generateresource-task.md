---
title: "GenerateResource Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateResource task"
  - "GenerateResource task [MSBuild]"
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GenerateResource Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Converte i file txt e resx \(formato di risorsa basato su XML\) in file resources binari di Common Language Runtime che è possibile incorporare in un eseguibile binario di runtime o compilare in assembly satellite.  Questa attività viene in genere utilizzata per convertire file txt o resx in file resources.  Dal punto di vista funzionale, l'attività `GenerateResource` è simile a [resgen.exe](../Topic/Resgen.exe%20\(Resource%20File%20Generator\).md).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `GenerateResource`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalInputs`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene input aggiuntivi per il controllo delle dipendenze eseguito da questa attività.  Ad esempio, in genere è opportuno inserire i file di progetto e di destinazioni in modo che se vengono aggiornati, tutte le risorse vengono rigenerate.|  
|`EnvironmentVariables`|Parametro `String[]` facoltativo.<br /><br /> Specifica una matrice di coppie nome\/valore di variabili di ambiente che devono essere passate al file resgen.exe generato, oltre al normale blocco di ambiente \(o all'esecuzione selettiva dell'override di tale blocco\).|  
|`ExcludedInputPaths`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica una matrice di elementi tramite i quali vengono indicati i percorsi dai quali gli input tracciati saranno ignorati durante la verifica dell'aggiornamento.|  
|`ExecuteAsTool`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, tlbimp.exe e aximp.exe vengono eseguiti dal framework di destinazione appropriato in modalità out\-of\-process per generare gli assembly wrapper necessari.  Questo parametro consente il multitargeting di `ResolveComReferences`.|  
|`FilesWritten`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene i nomi di tutti i file scritti su disco,  incluso, se presente, il file di cache.  Questo parametro è utile per le implementazioni di Clean.|  
|`MinimalRebuildFromTracking`|Parametro `Boolean` facoltativo.<br /><br /> Ottiene o imposta un'opzione che specifica se verrà utilizzata la compilazione incrementale tracciata.  Se `true`, viene abilitata la compilazione incrementale. In caso contrario, verrà forzata una ricompilazione.|  
|`NeverLockTypeAssemblies`|Parametro `Boolean` facoltativo.<br /><br /> Specifica il nome dei file generati, ad esempio i file resources.  Se non si specifica un nome, viene utilizzato il nome del file di input corrispondente e il file resources creato viene inserito nella directory contenente il file di input.|  
|`OutputResources`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il nome dei file generati, ad esempio i file resources.  Se non si specifica un nome, viene utilizzato il nome del file di input corrispondente e il file resources creato viene inserito nella directory contenente il file di input.|  
|`PublicClass`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, crea una classe di risorse fortemente tipizzata come classe pubblica.|  
|`References`|Parametro `String[]` facoltativo.<br /><br /> Specifica i riferimenti per il caricamento dei tipi nei file resx.  Gli elementi dei dati di questo tipo di file possono essere di tipo .NET.  Quando il file resx viene letto, deve essere risolto.  In genere, è possibile risolverlo correttamente utilizzando le regole di caricamento dei tipi standard.  Se in `References` vengono forniti assembly, questi avranno la precedenza.<br /><br /> Questo parametro non è obbligatorio per le risorse fortemente tipizzate.|  
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio resgen.exe.|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obbligatorio.<br /><br /> Specifica gli elementi da convertire.  Gli elementi passati a questo parametro devono avere una delle seguenti estensioni di file:<br /><br /> -   `.txt` \- Specifica l'estensione di un file di testo da convertire.  I file di testo possono contenere soltanto risorse di tipo stringa.<br />-   `.resx` \- Specifica l'estensione di un file di risorse basato su XML da convertire.<br />-   `.restext` \- Specifica lo stesso formato dell'estensione txt.  Questa diversa estensione è utile per distinguere in modo chiaro i file di origine contenenti risorse dagli altri file di origine del processo di compilazione.<br />-   `.resources` \- Specifica l'estensione di un file di risorse da convertire.|  
|`StateFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il percorso di un file di cache facoltativo utilizzato per rendere più rapido il controllo delle dipendenze dei collegamenti nei file di input resx.|  
|`StronglyTypedClassName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome della classe di risorse fortemente tipizzata.  Se questo parametro non è specificato, viene utilizzato il nome base del file di risorse.|  
|`StronglyTypedFilename`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file di origine.  Se questo parametro non è specificato, il nome della classe viene utilizzato come nome base e l'estensione viene determinata dal linguaggio.  Ad esempio: `MyClass.cs`.|  
|`StronglyTypedLanguage`|Parametro `String` facoltativo.<br /><br /> Specifica il linguaggio da utilizzare per la generazione dell'origine della classe per la risorsa fortemente tipizzata.  Questo parametro deve corrispondere esattamente a uno dei linguaggi utilizzati da CodeDomProvider,  Ad esempio, `VB` o `C#`.<br /><br /> Il passaggio di un valore a questo parametro determina la generazione di risorse fortemente tipizzate.|  
|`StronglyTypedManifestPrefix`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi delle risorse o il prefisso del manifesto da utilizzare nell'origine della classe generata per la risorsa fortemente tipizzata.|  
|`StronglyTypedNamespace`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi da utilizzare per l'origine della classe generata per la risorsa fortemente tipizzata.  Se questo parametro non è specificato, tutte le risorse fortemente tipizzate sono incluse nello spazio dei nomi globale.|  
|`TLogReadFiles`|Parametro di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene una matrice di elementi che rappresentano i log di rilevamento delle operazioni di lettura.|  
|`TLogWriteFiles`|Parametro di sola lettura <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Ottiene una matrice di elementi che rappresentano i log di rilevamento delle operazioni di scrittura.|  
|`ToolArchitecture`|Parametro [String](assetId:///String?qualifyHint=False&autoUpgrade=True) facoltativo.<br /><br /> Utilizzato per determinare se per generare ResGen.exe è necessario utilizzare Tracker.exe.<br /><br /> Deve essere analizzabile rispetto a un membro dell'enumerazione <xref:Microsoft.Build.Utilities.ExecutableType>.  Se `String.Empty`, viene utilizzata un'euristica per determinare un'architettura predefinita.  Deve essere analizzabile rispetto a un membro dell'enumerazione Microsoft.Build.Utilities.ExecutableType.|  
|`TrackerFrameworkPath`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica il percorso della posizione di .NET Framework appropriata contenente il file FileTracker.dll.<br /><br /> Se impostato, l'utente si assume la responsabilità di assicurarsi che il numero di bit del FileTracker.dll passato corrisponda al numero di bit del file ResGen.exe che si intende utilizzare.  Se non è impostato, tramite l'attività viene deciso il percorso adatto in base alla versione di .NET Framework corrente.|  
|`TrackerLogDirectory`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica la directory intermedia nella quale saranno inseriti i log di rilevamento generati dall'esecuzione di questa attività.|  
|`TrackerSdkPath`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica il percorso della posizione di Windows SDK appropriata contenente il file Tracker.exe.<br /><br /> Se impostato, l'utente si assume la responsabilità di assicurarsi che il numero di bit del file Tracker.exe passato corrisponda al numero di bit del file ResGen.exe che si intende utilizzare.  Se non è impostato, tramite l'attività viene deciso il percorso adatto in base alla versione corrente di Windows SDK.|  
|`TrackFileAccess`|Parametro [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) facoltativo.<br /><br /> Se true, la directory del file di input viene utilizzata per risolvere i percorsi di file relativi.|  
|`UseSourcePath`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, specifica che è necessario utilizzare la directory del file di input per risolvere i percorsi di file relativi.|  
  
## Note  
 Poiché i file resx possono contenere collegamenti ad altri file di risorse, non è sufficiente confrontare i timestamp dei file resx e resources per verificare se gli output sono aggiornati.  Al contrario, l'attività `GenerateResource` segue i collegamenti nei file resx e controlla al tempo stesso i timestamp dei file collegati.  Questo significa che in genere gli attributi `Inputs` e `Outputs` non devono essere utilizzati sulla destinazione che contiene l'attività `GenerateResource`. In tal modo, infatti, l'attività potrebbe essere ignorata quando invece dovrebbe essere eseguita.  
  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
 Se si utilizza MSBuild 4.0 come destinazione per progetti .NET 3.5, è possibile che la compilazione sulle risorse x86 non riesca.  Per risolvere questo problema, è possibile compilare la destinazione come assembly AnyCPU.  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `GenerateResource` viene utilizzata per generare file resources dai file specificati dalla raccolta di elementi `Resx`.  
  
```  
<GenerateResource  
    Sources="@(Resx)"  
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">  
    <Output  
        TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
 L'attività `GenerateResource` utilizza i \<LogicalName\> metadati di un \<EmbeddedResource\> elemento per assegnare un nome alla risorsa incorporata in un assembly.  
  
 Supponendo che l'assembly si chiami myAssembly, il codice seguente genera una risorsa incorporata con il nome unqualificatore.unarisorsa.risorse:  
  
```  
<ItemGroup>   <EmbeddedResource Include="myResource.resx">       <LogicalName>someQualifier.someResource.resources</LogicalName>   </EmbeddedResource></ItemGroup>  
```  
  
 Senza i metadati \<LogicalName\>, la risorsa sarebbe denominata myAssembly.myResource.resources.  Questo esempio si applica solo a Visual Basic e al processo di compilazione di Visual C\#.  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)