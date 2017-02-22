---
title: "Vbc Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Vbc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Vbc task [MSBuild]"
  - "MSBuild, Vbc task"
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Vbc Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping di vbc.exe, un compilatore che genera file eseguibili con estensione exe, librerie a collegamento dinamico con estensione dll o moduli di codice  NETMODULE.  Per ulteriori informazioni su vbc.exe, vedere [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `Vbc`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parametro `String[]` facoltativo.<br /><br /> Specifica cartelle aggiuntive in cui eseguire la ricerca degli assembly specificati nell'attributo References.|  
|`AddModules`|Parametro `String[]` facoltativo.<br /><br /> Permette al compilatore di rendere disponibili al progetto in corso di compilazione tutte le informazioni sui tipi presenti nei file specificati.  Questo parametro corrisponde all'opzione [\/addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) del compilatore vbc.exe.|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base della DLL.  Questo parametro corrisponde all'opzione [\/baseaddress](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) del compilatore vbc.exe.|  
|`CodePage`|Parametro `Int32` facoltativo.<br /><br /> Consente di specificare la tabella codici da utilizzare per tutti i file del codice sorgente nella compilazione.  Questo parametro corrisponde all'opzione [\/codepage](/dotnet/visual-basic/reference/command-line-compiler/codepage) del compilatore vbc.exe.|  
|`DebugType`|Parametro `String[]` facoltativo.<br /><br /> Determina la generazione di informazioni di debug da parte del compilatore.  Per il parametro è possibile specificare i seguenti valori:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Il valore predefinito è `full`, che consente di associare un debugger al programma in esecuzione.  Il valore `pdbonly` consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma il codice del linguaggio assembly viene visualizzato solo quando il programma in esecuzione è associato al debugger.  Per ulteriori informazioni, vedere [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`DefineConstants`|Parametro `String[]` facoltativo.<br /><br /> Definisce le costanti condizionali del compilatore.  Le coppie simbolo\/valore sono separate da punti e virgola e vengono specificate utilizzando la seguente sintassi:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Questo parametro corrisponde all'opzione [\/define](/dotnet/visual-basic/reference/command-line-compiler/define) del compilatore vbc.exe.|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, la chiave pubblica viene inserita nell'assembly.  Se è impostato su `false`, l'assembly viene firmato completamente.  Il valore predefinito è `false`. Il parametro non ha effetto se non viene utilizzato con il parametro `KeyFile` o `KeyContainer`.  Questo parametro corrisponde all'opzione [\/delaysign](/dotnet/visual-basic/reference/command-line-compiler/delaysign) del compilatore vbc.exe.|  
|`DisabledWarnings`|Parametro `String` facoltativo.<br /><br /> Evita la visualizzazione degli avvisi specificati.  È sufficiente specificare la parte numerica dell'identificatore dell'avviso.  Se sono specificati più avvisi, questi sono separati da punti e virgola.  Questo parametro corrisponde all'opzione [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) del compilatore vbc.exe.|  
|`DocumentationFile`|Parametro `String` facoltativo.<br /><br /> Elabora i commenti relativi alla documentazione nel file XML specificato.  Questo parametro esegue l'override dell'attributo `GenerateDocumentation`.  Per ulteriori informazioni, vedere [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`EmitDebugInformation`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, le informazioni di debug vengono generate e inserite in un file pdb.  Per ulteriori informazioni, vedere [\/debug](/dotnet/visual-basic/reference/command-line-compiler/debug).|  
|`ErrorReport`|Parametro `String` facoltativo.<br /><br /> Specifica la modalità di segnalazione degli errori interni del compilatore.  Per il parametro è possibile specificare i seguenti valori:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Se è specificato il valore `prompt` e si verifica un errore interno del compilatore, viene chiesto se si desidera inviare i dati dell'errore a Microsoft.<br /><br /> Se è specificato il valore `send` e si verifica un errore interno del compilatore, i dati dell'errore vengono inviati a Microsoft.<br /><br /> Il valore predefinito è `none`, con cui gli errori vengono segnalati solo nell'output di testo.<br /><br /> Questo parametro corrisponde all'opzione [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) del compilatore vbc.exe.|  
|`FileAlignment`|Parametro `Int32` facoltativo.<br /><br /> Specifica, in byte, il punto in cui allineare le sezioni del file di output.  Per il parametro è possibile specificare i seguenti valori:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Questo parametro corrisponde all'opzione [\/filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) del compilatore vbc.exe.|  
|`GenerateDocumentation`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, le informazioni relative alla documentazione vengono generate e inserite in un file XML con il nome dell'eseguibile o della libreria in corso di creazione.  Per ulteriori informazioni, vedere [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).|  
|`Imports`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Importa gli spazi dei nomi dalle raccolte di elementi specificati.  Questo parametro corrisponde all'opzione [\/imports](/dotnet/visual-basic/reference/command-line-compiler/imports) del compilatore vbc.exe.|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi di crittografia.  Questo parametro corrisponde all'opzione [\/keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) del compilatore vbc.exe.|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia.  Per ulteriori informazioni, vedere [\/keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile).|  
|`LangVersion`|Parametro [String](assetId:///String?qualifyHint=False&autoUpgrade=True) facoltativo.<br /><br /> Specifica la versione di linguaggio: "9" o "10".|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Crea un collegamento a una risorsa .NET Framework nel file di output, ma il file di risorse non viene inserito nel file di output.  Questo parametro corrisponde all'opzione [\/linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) del compilatore vbc.exe.|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Consente di specificare la classe o il modulo che contiene la routine `Sub Main`.  Questo parametro corrisponde all'opzione [\/main](/dotnet/visual-basic/reference/command-line-compiler/main) del compilatore vbc.exe.|  
|`ModuleAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica l'assembly di cui fa parte questo modulo.|  
|`NoConfig`|Parametro `Boolean` facoltativo.<br /><br /> Specifica che il file vbc.rsp non deve essere utilizzato dal compilatore.  Questo parametro corrisponde al parametro [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) del compilatore vbc.exe.|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, viene disabilitata la visualizzazione dei messaggi informativi del compilatore.  Questo parametro corrisponde all'opzione [\/nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) del compilatore vbc.exe.|  
|`NoStandardLib`|Parametro `Boolean` facoltativo.<br /><br /> Con questo parametro il compilatore non fa riferimento alle librerie standard.  Questo parametro corrisponde all'opzione [\/nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) del compilatore vbc.exe.|  
|`NoVBRuntimeReference`|Parametro `Boolean` facoltativo.<br /><br /> Solo per uso interno.  Se true, viene impedito il riferimento automatico a Microsoft.VisualBasic.dll.|  
|`NoWarnings`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, viene disabilitata la visualizzazione di tutti gli avvisi.  Per ulteriori informazioni, vedere [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).|  
|`Optimize`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, vengono attivate le ottimizzazioni del compilatore.  Questo parametro corrisponde all'opzione [\/optimize](/dotnet/visual-basic/reference/command-line-compiler/optimize) del compilatore vbc.exe.|  
|`OptionCompare`|Parametro `String` facoltativo.<br /><br /> Specifica la modalità con cui vengono confrontate le stringhe.  Per il parametro è possibile specificare i seguenti valori:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Il valore `binary` indica l'utilizzo di confronti di stringhe binarie,  mentre il valore `text` indica l'utilizzo di confronti di stringhe di testo.  Il valore predefinito del parametro è `binary`.  Questo parametro corrisponde all'opzione [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) del compilatore vbc.exe.|  
|`OptionExplicit`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, è necessario dichiarare le variabili in modo esplicito.  Questo parametro corrisponde all'opzione [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) del compilatore vbc.exe.|  
|`OptionInfer`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, consente l'inferenza del tipo delle variabili.|  
|`OptionStrict`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, viene attivata la semantica dei tipi rigida per limitare le conversioni implicite di tipi.  Questo parametro corrisponde all'opzione [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) del compilatore vbc.exe.|  
|`OptionStrictType`|Parametro `String` facoltativo.<br /><br /> Specifica la semantica dei tipi rigida che consente di generare un avviso.  Al momento, è supportato solo "custom".  Questo parametro corrisponde all'opzione [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) del compilatore vbc.exe.|  
|`OutputAssembly`|Parametro di output `String` facoltativo.<br /><br /> Specifica il nome del file di output.  Questo parametro corrisponde all'opzione [\/out](/dotnet/visual-basic/reference/command-line-compiler/out) del compilatore vbc.exe.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma processore di destinazione del file di output.  Il parametro può essere impostato su `x86`, `x64`, `Itanium` o `anycpu`.  Il valore predefinito è `anycpu`.  Questo parametro corrisponde all'opzione [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform) del compilatore vbc.exe.|  
|`References`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Determina l'importazione delle informazioni sui tipi pubblici dagli elementi specificati nel progetto corrente.  Questo parametro corrisponde all'opzione [\/reference](/dotnet/visual-basic/reference/command-line-compiler/reference) del compilatore vbc.exe.|  
|`RemoveIntegerChecks`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, i controlli degli errori di overflow di Integer vengono disabilitati.  Il valore predefinito è `false`.  Questo parametro corrisponde all'opzione [\/removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) del compilatore vbc.exe.|  
|`Resources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Incorpora una risorsa .NET Framework nel file di output.  Questo parametro corrisponde all'opzione [\/resource](/dotnet/visual-basic/reference/command-line-compiler/resource) del compilatore vbc.exe.|  
|`ResponseFiles`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività.  Questo parametro corrisponde all'opzione [@ \(specifica del file di risposta\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) del compilatore vbc.exe.|  
|`RootNamespace`|Parametro `String` facoltativo.<br /><br /> Specifica lo spazio dei nomi di primo livello per tutte le dichiarazioni di tipi.  Questo parametro corrisponde all'opzione [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) del compilatore vbc.exe.|  
|`SdkPath`|Parametro `String` facoltativo.<br /><br /> Specifica la posizione dei file mscorlib.dll e microsoft.visualbasic.dll.  Questo parametro corrisponde all'opzione [\/sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) del compilatore vbc.exe.|  
|`Sources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica uno o più file di origine [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].|  
|`TargetCompactFramework`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, viene utilizzato [!INCLUDE[Compact](../extensibility/includes/compact_md.md)].  Questa opzione corrisponde all'opzione [\/netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) del compilatore vbc.exe.|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output.  Il parametro può essere impostato su `library` per la creazione di una libreria di codice, su `exe` per la creazione di un'applicazione console, su `module` per la creazione di un modulo oppure su `winexe` per la creazione di un'applicazione Windows.  Il valore predefinito è `library`.  Questo parametro corrisponde all'opzione [\/target](/dotnet/visual-basic/reference/command-line-compiler/target) del compilatore vbc.exe.|  
|`Timeout`|Parametro `Int32` facoltativo.<br /><br /> Specifica l'intervallo di tempo, in millisecondi, al termine del quale l'eseguibile dell'attività verrà interrotto.  Il valore predefinito è `Int.MaxValue`, con cui viene indicato che non è stato specificato alcun periodo di timeout.|  
|`ToolPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso da cui l'attività carica il file eseguibile sottostante \(vbc.exe\).  Se questo parametro non è specificato, viene utilizzato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`TreatWarningsAsErrors`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, tutti gli avvisi vengono considerati come errori.  Per ulteriori informazioni, vedere [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).|  
|`UseHostCompilerIfAvailable`|Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di utilizzare, se disponibile, l'oggetto compilatore in\-process.  Utilizzato solo da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore utilizzando la codifica UTF\-8.  Questo parametro corrisponde all'opzione [\/utf8output](/dotnet/visual-basic/reference/command-line-compiler/utf8output) del compilatore vbc.exe.|  
|`Verbosity`|Parametro `String` facoltativo.<br /><br /> Specifica il livello di dettaglio dell'output del compilatore.  Il parametro può essere impostato su `Quiet`, `Normal` \(valore predefinito\) o `Verbose`.|  
|`WarningsAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori.  Per ulteriori informazioni, vedere [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Questo parametro esegue l'override del parametro `TreatWarningsAsErrors`.|  
|`WarningsNotAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da non considerare come errori.  Per ulteriori informazioni, vedere [\/warnaserror](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Questo parametro risulta utile solo se il parametro `TreatWarningsAsErrors` è impostato su `true`.|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di icona nell'assembly, che fornisce il file di output l'aspetto desiderato in Esplora file.  Questo parametro corrisponde all'opzione [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) del compilatore vbc.exe.|  
|`Win32Resources`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorse Win32 \(res\) nel file di output.  Questo parametro corrisponde all'opzione [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) del compilatore vbc.exe.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene compilato un progetto [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## Vedere anche  
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)