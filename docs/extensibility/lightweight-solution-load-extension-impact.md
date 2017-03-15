---
title: Carico soluzione semplificata (LSL) | Documenti di Microsoft
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>Carico soluzione semplificata (LSL)

## <a name="background-information-on-lsl"></a>Informazioni generali su LSL

Carico soluzione semplice è una nuova funzionalità di Visual Studio 2017 che riduce significativamente il tempo di caricamento di soluzione, che consente di essere più produttivi rapidamente. Quando è necessario LSL è abilitato, Visual Studio non verrà completamente caricato progetti fino a quando non si inizia a utilizzarli.

LSL può influire sul estensioni di Visual Studio. Le cui funzionalità dipendono da un progetto da caricare le estensioni potrebbero non funzionare o funzionare nel modo corretto senza seguendo le istruzioni disponibili in questo documento.

Per ulteriori informazioni sugli LSL, utilizzare i collegamenti seguenti:

* [Blog del carico soluzione semplificata](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* Domande? È possibile contattare[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>Abilitare l'impostazione caricare i progetti in modalità "differito"

1. Chiudere qualsiasi soluzione attualmente aperta.
2. Passare a **strumenti** > **opzione** > **progetti e soluzioni** > **generale** pagina Impostazioni.
3. Controllare il **carico soluzione semplificata** casella per abilitare l'impostazione.

Quando viene aperta una soluzione con l'impostazione precedente attivata, l'IDE viene illustrata una visualizzazione normale dei progetti ma non sono stati caricati i progetti.

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>Differenze tra caricamento posticipato e carico normale dei progetti

Quando si apre una soluzione con carico soluzione Lightweight, progetti non vengono caricati. Per questi "progetti posticipati", viene creata una gerarchia di stub. Esplora soluzioni Mostra la vista prevista con le icone e i nomi dei progetti, sarà presente alcuna indicazione dell'interfaccia utente che alcuni o tutti i progetti sono in "modalità differita".

Con LSL abilitato, estensioni non è più probabile che i progetti necessari sono già completamente caricati quando viene attivata un'operazione. I chiamanti devono controllare se hanno una dipendenza caricata progetti. Se un'estensione richiede informazioni da un progetto posticipata, l'estensione per eseguire le operazioni seguenti:

1. Caricare i progetti in base alle esigenze.
2. Utilizzare il nuovo **area di lavoro API** per ottenere informazioni da un progetto posticipato senza caricamento.

Il nuovo **area di lavoro API** consentono alle estensioni ottenere informazioni, ad esempio il progetto di un file di origine e di tutti i file di origine per il progetto specificato da un progetto posticipato. In alcuni casi, è necessario caricare solo un set limitato di progetti. La scelta ottimale è un equilibrio tra la frequenza delle operazioni, facilità di approcci alternativi e soddisfazione degli utenti.

Tutti del progetto e carico soluzione correlati nella modalità LSL vengono ancora generati eventi. In questo modo i componenti ottenere il comportamento previsto da Visual Studio e si comportano esattamente come quando vengono caricati i progetti. Il caricamento del progetto correlati ridotto drasticamente tuttavia eseguite durante una soluzione aperta.

## <a name="ui-requirements-and-changes"></a>Le modifiche e i requisiti dell'interfaccia utente

L'interfaccia utente devono essere gestiti caricati e posticipati progetti come uguali. Questo significa che qualsiasi azione che può essere eseguita su un progetto caricato deve essere applicabile ai progetti differiti, con alcune eccezioni. Per facilitare lo svolgimento di questa funzionalità, sono state apportate modifiche di alcune API della piattaforma esistente, nonché l'introduzione di nuove API.

### <a name="expectations-for-ui"></a>Aspettative per l'interfaccia utente

1. Le funzionalità devono presentare che alcuna visual non differenze a seconda se i progetti vengono caricati o posticipati.
2. Qualsiasi elenco o enumerazione tramite i progetti della soluzione caricato deve includere progetti posticipati.
3. Le azioni disponibili rispetto a un progetto caricato dovrebbero essere disponibile rispetto a un progetto posticipato.
4. Funzionalità deve richiesta di caricamento progetto solo quando:
  * È l'interazione diretta dell'utente con una funzionalità. Non caricare preventivamente i progetti.
  * Un'azione "Ulteriori risultati" viene effettuata dall'utente. Per questa linea guida dell'interfaccia utente, vedere di seguito.
  * Nell'azione, è possibile utilizzare solo il progetto caricato completamente. Utilizzare LSL e API aperte di progetto ogni volta che è possibile inviare una richiesta di funzionalità richiesto quando non è presente la funzionalità.

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>Modifiche nella piattaforma API per unità dell'interfaccia utente

1. Nuove API sono disponibili per porre la soluzione se è stato aperto in modalità di caricamento della soluzione Lightweight e quanti progetti si trovano nello stato posticipato.
2. Nuovo evento è disponibile per quando vengono caricati tutti i progetti posticipati nella soluzione.
3. Nuove API sono disponibili per chiedere a un progetto se è stata rinviata.
4. Le API esistenti vengono aggiornate per includere progetti posticipati quando si richiede progetti caricati.
5. Le API esistenti vengono aggiornate in express la soluzione venga caricata completamente dopo l'apertura della soluzione.

### <a name="how-to-add-see-more-results-for-a-feature"></a>Procedura: aggiungere "Ulteriori risultati" per una funzionalità.

Funzionalità che esegue una query sul contenuto dei progetti è consigliabile valutare l'impatto di progetti posticipati. In alcune situazioni, funzionalità possono ottenere i risultati della query da LSL e le API dell'area di lavoro per un progetto posticipato. In altri casi, le limitazioni delle funzionalità di un richiedono dei progetti da caricare. Entrambi i casi deve fornire un nuovo movimento "Ulteriori risultati" che consente agli utenti di caricare completamente i progetti e ripetere la query. Questa azione Abilita le funzionalità offrire una migliore approssimazione quando sono presenti progetti posticipati offrendo all'utente un modo per ottenere il risultato perfetto quando i progetti sono effettivamente caricati.

L'algoritmo generale per la funzionalità deve essere:

### <a name="when-the-query-is-performed-over-a-single-project"></a>Quando viene eseguita la Query su un singolo progetto

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>Quando viene eseguita la Query tramite l'intera soluzione

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>Modifiche API

### <a name="new-api"></a>Nuova API

IVsSolution7.IsSolutionLoadDeferred (out bool posticipata)

Restituisce true se la soluzione corrente è stata caricata in modalità differita. Si noti che se la soluzione inizialmente è stata caricata in modalità differita, anche se tutti i progetti posticipati alla fine vengono caricati nella sessione corrente (a causa di movimenti esplicita dell'utente o forzata dalle operazioni), questa proprietà restituirà true.

__VSPROPID7. VSPROPID_DeferredProjectCount

Restituisce il numero di progetti attualmente in modalità differita. Questa proprietà sarà assegnato un valore compreso nell'intervallo [0, VSPROPID_ProjectCount].

__VSHPROPID9. VSHPROPID_IsDeferred

Restituisce true se una gerarchia di progetto si trova in stato di caricamento posticipato.

__VSENUMPROJFLAGS3 con i valori EPF_DEFERRED ed EPF_NOTDEFERRED

Questi flag possono essere passati a [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) per scorrere i progetti non rinviata e posticipati.

### <a name="new-events"></a>Nuovi eventi

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

Questo evento viene generato dopo il caricamento di tutti i progetti posticipati. A questo punto, VSPROPID_DeferredProjectCount è uguale a 0. Si noti che questo evento non viene generato come parte del carico soluzione e non possono essere generato in una sessione. Viene generato solo se e quando vengono caricati tutti i progetti posticipati.

### <a name="changes-to-existing-api"></a>Modifiche a un'API esistente

* Il passaggio di [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_LOADEDINSOLUTION a [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx) restituisce posticipata progetti.
* Il passaggio di [__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx). EPF_UNLOADEDINSOLUTION non restituisce progetti posticipati.
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx) è impostato su true nella soluzione aperta. Progetti posticipati vengono considerati come caricato in modo da questo contesto viene impostato gran parte anteriore in modalità non LSL.
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx). VSPROPID_ProjectCount restituisce la somma dei progetti caricati e posticipati.

## <a name="helpful-code-snippets"></a>Frammenti di codice utile

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>Controllare se una soluzione è stato aperto in modalità di caricamento posticipato

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>Controllare se un progetto viene posticipato

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>Carica un progetto

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>Caricare un insieme di progetti

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>Controlla se la soluzione è posticipato progetti

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>Ottenere informazioni dettagliate con le API dell'area di lavoro

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>Procedura: ottenere informazioni dettagliate su una soluzione LSL

Nuove API di area di lavoro vengono esposte tramite IVsSolutionWorkspaceService per recuperare informazioni dettagliate su una soluzione.

Queste API possono essere utilizzate per ottenere l'area di lavoro corrente, la soluzione attiva, le informazioni della riga di comando gestito, nonché il servizio di indicizzazione per l'area di lavoro. Queste API possono sfruttare ulteriormente il servizio di indicizzazione per ottenere dati dettagliati, ad esempio, tutti i file sorgente in un progetto, il progetto di un file di origine, tutti i progetti contenuti nella soluzione corrente, tutti i riferimenti P2P in un progetto e così via.

I frammenti di codice seguente viene illustrato l'utilizzo delle API di area di lavoro.

### <a name="get-ivssolutionworkspaceservice-initially"></a>Ottenere inizialmente IVsSolutionWorkspaceService

>**Nota:** ottenere IVsSolutionWorkspaceService solo in scenari LSL per evitare di caricare il pacchetto dell'API dell'area di lavoro.

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**Nota:** i frammenti di codice seguente si supponga che _solutionWorkspaceService è già inizializzate.

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>Recupero di informazioni sulla riga di comando gestito progetti posticipati per configurazione soluzione attiva

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>Ottenere il file di soluzione attiva in LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>Ottenere il progetto di un file di origine

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>Ottenere tutti i file di origine da un progetto

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>Ottenere i riferimenti a P2P in un progetto

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>Ottenere tutti i progetti in una soluzione

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>Risoluzione dei problemi

A causa della natura del LSL, è intenzionale che gli utenti non possono visualizzare una differenza tra i progetti caricati e posticipati. In questo modo lo sviluppo di funzionalità e testing difficile.

È possibile abilitare visual suggerimenti nell'interfaccia utente per i progetti posticipati effettuando le operazioni seguenti:

1. Chiudere Visual Studio.
2. Regedit.exe
3. Selezionare HKLM
4. File > carica Hive
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. Immettere "VisualStudio" come nome di una chiave
7. Impostare `HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1` (DWORD)
8. Selezionare HKLM\VisualStudio
9. File > Scarica Hive
10. Avviare Visual Studio

Per ulteriori domande, visitare per [ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com).







