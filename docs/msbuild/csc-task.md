---
title: "Attivit&#224; Csc | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Csc"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Csc (attività) [MSBuild]"
  - "MSBuild, Csc (attività)"
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Attivit&#224; Csc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esegue il wrapping CSC.exe e produce file eseguibili (file .exe), librerie a collegamento dinamico (file con estensione dll) o moduli di codice (file con estensione netmodule). Per ulteriori informazioni su CSC.exe, vedere [Opzioni del compilatore c#](/dotnet/csharp/language-reference/compiler-options/index).  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Csc`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Parametro `String[]` facoltativo.<br /><br /> Specifica directory aggiuntive in cui cercare i riferimenti. Per ulteriori informazioni, vedere [/lib (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/lib-compiler-option).|  
|`AddModules`|Parametro `String` facoltativo.<br /><br /> Specifica uno o più moduli che devono fare parte dell'assembly. Per ulteriori informazioni, vedere [/addmodule (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option).|  
|`AllowUnsafeBlocks`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, compila il codice che utilizza il [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) (parola chiave). Per ulteriori informazioni, vedere [/unsafe (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option).|  
|`ApplicationConfiguration`|Parametro `String` facoltativo.<br /><br /> Specifica il file di configurazione contenente le impostazioni di associazione di assembly.|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL è impostato il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] common language runtime. Per ulteriori informazioni, vedere [/baseaddress (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).|  
|`CheckForOverflowUnderflow`|Parametro `Boolean` facoltativo.<br /><br /> Specifica se aritmetici che superano i limiti del tipo di dati genera un'eccezione in fase di esecuzione. Per ulteriori informazioni, vedere [/checked (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).|  
|`CodePage`|Parametro `Int32` facoltativo.<br /><br /> Specifica la tabella codici da usare per tutti i file del codice sorgente nella compilazione. Per ulteriori informazioni, vedere [/codepage (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/codepage-compiler-option).|  
|`DebugType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di debug. `DebugType` può essere `full` o `pdbonly`. Il valore predefinito è `full`, che consente di associare un debugger a un programma in esecuzione. Specifica di `pdbonly` consente il debug del codice quando il programma viene avviato nel debugger, ma assembler viene visualizzato solo quando il programma in esecuzione è collegato al debugger di origine.<br /><br /> Questo parametro esegue l'override di `EmitDebugInformation` parametro.<br /><br /> Per ulteriori informazioni, vedere [/debug (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`DefineConstants`|Parametro `String` facoltativo.<br /><br /> Definisce i simboli del preprocessore. Per ulteriori informazioni, vedere [/define (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/define-compiler-option).|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica che si desidera che l'assembly abbia firmato completa. Se `false`, specifica che si desidera inserire la chiave pubblica nell'assembly.<br /><br /> Questo parametro ha effetto solo se utilizzato con il `KeyFile` o `KeyContainer` parametro.<br /><br /> Per ulteriori informazioni, vedere [/delaysign (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/delaysign-compiler-option).|  
|`DisabledWarnings`|Parametro `String` facoltativo.<br /><br /> Specifica l'elenco di avvisi da disabilitare. Per ulteriori informazioni, vedere [/nowarn (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option).|  
|`DocumentationFile`|Parametro `String` facoltativo.<br /><br /> Elabora commenti sulla documentazione in un file XML. Per ulteriori informazioni, vedere [/doc (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option).|  
|`EmitDebugInformation`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, l'attività genera informazioni di debug e lo colloca in un file di programma (PDB) del database. Se `false`, l'attività non genera alcuna informazione di debug. Il valore predefinito è `false`. Per ulteriori informazioni, vedere [/debug (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).|  
|`ErrorReport`|Parametro `String` facoltativo.<br /><br /> Fornisce un modo pratico per segnalare a Microsoft un errore interno in c#. Questo parametro può avere un valore di `prompt`, `send`, o `none`. Se il parametro è impostato su `prompt`, si riceverà un prompt dei comandi quando si verifica un errore interno del compilatore. Il prompt dei comandi consente di inviare elettronicamente una segnalazione a Microsoft. Se il parametro è impostato su `send`, viene inviato automaticamente un report sui bug. Se il parametro è impostato su `none`, l'errore viene segnalato solo nell'output di testo del compilatore. Il valore predefinito è `none`. Per ulteriori informazioni, vedere [/errorreport (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).|  
|`FileAlignment`|Parametro `Int32` facoltativo.<br /><br /> Specifica le dimensioni delle sezioni nel file di output. Per ulteriori informazioni, vedere [/filealign (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).|  
|`GenerateFullPaths`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, specifica il percorso assoluto del file nell'output del compilatore. Se `false`, specifica il nome del file. Il valore predefinito è `false`. Per ulteriori informazioni, vedere [/fullpaths (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/fullpaths-compiler-option).|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del contenitore di chiavi crittografiche. Per ulteriori informazioni, vedere [/keycontainer (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/keycontainer-compiler-option).|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome del file contenente la chiave di crittografia. Per ulteriori informazioni, vedere [/keyfile (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/keyfile-compiler-option).|  
|`LangVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione del linguaggio da usare. Per ulteriori informazioni, vedere [/langversion (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option).|  
|`LinkResources`|Facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametro.<br /><br /> Crea un collegamento a un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] risorse nel file di output, il file di risorse non viene inserito nel file di output.<br /><br /> Gli elementi passati a questo parametro è possono associare metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al `identifier` parametro il `/linkresource` passare, e `Access` corrisponde a `accessibility-modifier` parametro. Per ulteriori informazioni, vedere [/linkresource (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option).|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica la posizione del `Main` metodo. Per ulteriori informazioni, vedere [/main (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option).|  
|`ModuleAssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'assembly che conterrà una parte di questo modulo.|  
|`NoConfig`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, indica al compilatore di non eseguire la compilazione con il file csc. rsp. Per ulteriori informazioni, vedere [/noconfig (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/noconfig-compiler-option).|  
|`NoLogo`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, evita la visualizzazione dei messaggi informativi del compilatore. Per ulteriori informazioni, vedere [/nologo (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/nologo-compiler-option).|  
|`NoStandardLib`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, impedisce l'importazione di mscorlib. dll, che definisce l'intero spazio dei nomi System. Utilizzare questo parametro se si desidera definire o creare il proprio spazio dei nomi System e gli oggetti. Per ulteriori informazioni, vedere [/nostdlib (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).|  
|`NoWin32Manifest`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, non includere il manifesto Win32 predefinito.|  
|`Optimize`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, abilita le ottimizzazioni. Se `false`, disabilita le ottimizzazioni. Per ulteriori informazioni, vedere [/optimize (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/optimize-compiler-option).|  
|`OutputAssembly`|Facoltativo `String` parametro di output.<br /><br /> Specifica il nome del file di output. Per ulteriori informazioni, vedere [/out (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option).|  
|`PdbFile`|Parametro `String` facoltativo.<br /><br /> Specifica il nome di file di informazioni di debug. Il nome predefinito è il nome del file di output con estensione pdb.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma del processore da impostare come destinazione del file di output. Questo parametro può avere un valore di `x86`, `x64`, o `anycpu`. Il valore predefinito è `anycpu`. Per ulteriori informazioni, vedere [/platform (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option).|  
|`References`|Facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametro.<br /><br /> Determina l'attività importare informazioni sui tipi pubblici dagli elementi specificati nel progetto corrente. Per ulteriori informazioni, vedere [/reference (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option).<br /><br /> È possibile specificare un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] riferimento alias in un [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] file aggiungendo i metadati `Aliases` all'elemento originale "Riferimento". Ad esempio, per impostare l'alias "LS1" nella riga di comando CSC seguente:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> è necessario utilizzare:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametro.<br /><br /> Incorpora un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] risorse nel file di output.<br /><br /> Gli elementi passati a questo parametro è possono associare metadati facoltativi denominati `LogicalName` e `Access`. `LogicalName` corrisponde al `identifier` parametro il `/resource` passare, e `Access` corrisponde a `accessibility-modifier` parametro. Per ulteriori informazioni, vedere [/resource (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option).|  
|`ResponseFiles`|Parametro `String` facoltativo.<br /><br /> Specifica il file di risposta che contiene i comandi per questa attività. Per ulteriori informazioni, vedere [@ (Specify Response File)](/dotnet/csharp/language-reference/compiler-options/response-file-compiler-option).|  
|`Sources`|Facoltativo <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametro.<br /><br /> Specifica uno o più [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] file di origine.|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. Questo parametro può avere un valore di `library`, che consente di creare una libreria di codice, `exe`, che consente di creare un'applicazione console, `module`, che consente di creare un modulo o `winexe`, che consente di creare un programma per Windows. Il valore predefinito è `library`. Per ulteriori informazioni, vedere [/target (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option).|  
|`TreatWarningsAsErrors`|Parametro `Boolean` facoltativo.<br /><br /> Se `true`, gli avvisi vengono considerati come errori. Per ulteriori informazioni, vedere [/warnaserror (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).|  
|`UseHostCompilerIfAvailable`|Parametro `Boolean` facoltativo.<br /><br /> Indica all'attività di utilizzare l'oggetto del compilatore in-process, se disponibile. Utilizzato solo da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|`Utf8Output`|Parametro `Boolean` facoltativo.<br /><br /> Registra l'output del compilatore utilizzando la codifica UTF-8. Per ulteriori informazioni, vedere [/utf8output (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/utf8output-compiler-option).|  
|`WarningLevel`|Parametro `Int32` facoltativo.<br /><br /> Specifica il livello di avviso per il compilatore da visualizzare. Per ulteriori informazioni, vedere [/warn (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option).|  
|`WarningsAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi da considerare come errori. Per ulteriori informazioni, vedere [/warnaserror (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Questo parametro esegue l'override di `TreatWarningsAsErrors` parametro.|  
|`WarningsNotAsErrors`|Parametro `String` facoltativo.<br /><br /> Specifica un elenco di avvisi che non vengono considerati errori. Per ulteriori informazioni, vedere [/warnaserror (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/warnaserror-compiler-option).<br /><br /> Questo parametro è utile solo se il `TreatWarningsAsErrors` parametro è impostato su `true`.|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce un file con estensione ico nell'assembly, che fornisce il file di output l'aspetto desiderato in Esplora File. Per ulteriori informazioni, vedere [/win32icon (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option).|  
|`Win32Manifest`|Parametro `String` facoltativo.<br /><br /> Specifica il manifesto Win32 da includere.|  
|`Win32Resource`|Parametro `String` facoltativo.<br /><br /> Inserisce un file di risorse (res) Win32 nel file di output. Per ulteriori informazioni, vedere [/win32res (opzioni del compilatore c#)](/dotnet/csharp/language-reference/compiler-options/win32res-compiler-option).|  
  
## <a name="remarks"></a>Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dal `Microsoft.Build.Tasks.ManagedCompiler` classe che eredita dal <xref:Microsoft.Build.Tasks.ToolTaskExtension> classe, che a sua volta eredita il <xref:Microsoft.Build.Utilities.ToolTask> classe. Per un elenco di parametri aggiuntivi e le relative descrizioni, vedere [classe di Base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene utilizzata la `Csc` attività per compilare un eseguibile dal file di origine di `Compile` raccolta di elementi.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento di attività](../msbuild/msbuild-task-reference.md)   
 [Attività](../msbuild/msbuild-tasks.md)