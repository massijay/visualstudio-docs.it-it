---
title: "AL (Assembly Linker) Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#AL"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "AL task [MSBuild]"
  - "MSBuild, AL task"
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AL (Assembly Linker) Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività AL esegue il wrapping di AL.exe, uno strumento distribuito con [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Lo strumento Assembly Linker consente di creare un assembly con un manifesto a partire da uno o più moduli o file di risorse.  Poiché è possibile che negli ambienti di compilazione e sviluppo queste funzionalità siano già disponibili, spesso non è necessario utilizzare direttamente questa attività.  Assembly Linker è particolarmente utile per gli sviluppatori che hanno la necessità di creare un unico assembly da più file di componenti, ad esempio quelli che possono essere prodotti dallo sviluppo in linguaggi misti.  Questa attività non combina i moduli in un unico file assembly. Affinché l'assembly ottenuto venga caricato correttamente, è comunque necessario che i singoli moduli vengano distribuiti e che siano disponibili.  Per ulteriori informazioni su AL.exe, vedere [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `AL`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AlgorithmID`|Parametro `String` facoltativo.<br /><br /> Specifica un algoritmo per generare un hash per tutti i file di un assembly su più file ad eccezione del file contenente il manifesto assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/algid` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`BaseAddress`|Parametro `String` facoltativo.<br /><br /> Specifica l'indirizzo da utilizzare in fase di esecuzione per il caricamento di una DLL sul computer dell'utente.  Il caricamento delle applicazioni risulta più veloce se si specifica l'indirizzo di base delle DLL, poiché non viene affidato al sistema operativo il compito di rilocare le DLL nello spazio di processo.  Questo parametro corrisponde all'opzione \/base\[address\] di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`CompanyName`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Company` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/comp[any]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Configuration`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Configuration` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/config[uration]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Copyright`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Copyright` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/copy[right]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Culture`|Parametro `String` facoltativo.<br /><br /> Specifica la stringa delle impostazioni cultura da associare all'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/c[ulture]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`DelaySign`|Parametro `Boolean` facoltativo.<br /><br /> Se il parametro è impostato su `true`, nell'assembly viene inserita solo la chiave pubblica. Se è impostato su `false`, l'assembly viene firmato completamente.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/delay[sign]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Description`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Description` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/descr[iption]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EmbedResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Incorpora le risorse specificate nell'immagine contenente il manifesto dell'assembly.  Questa attività copia nell'immagine il contenuto del file di risorse.  È possibile che agli elementi passati a questo parametro siano associati metadati facoltativi denominati `LogicalName` e `Access`.  Il metadato `LogicalName` viene utilizzato per specificare l'identificatore interno per la risorsa,  I metadati `Access` possono essere impostati su `private` per rendere la risorsa invisibile ad altri assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/embed[resource]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`EvidenceFile`|Parametro `String` facoltativo.<br /><br /> Incorpora il file specificato nell'assembly con il nome di risorsa `Security.Evidence`.<br /><br /> Non è possibile utilizzare il nome `Security.Evidence` per risorse regolari.  Questo parametro corrisponde all'opzione `/e[vidence]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ExitCode`|Parametro di output di sola lettura `Int32` facoltativo.<br /><br /> Specifica il codice di uscita fornito dal comando eseguito.|  
|`FileVersion`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `File Version` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/fileversion` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Flags`|Parametro `String` facoltativo.<br /><br /> Specifica un valore per il campo `Flags` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/flags` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`GenerateFullPaths`|Parametro `Boolean` facoltativo.<br /><br /> Determina l'utilizzo del percorso assoluto per tutti i file segnalati in un messaggio di errore.  Questo parametro corrisponde all'opzione `/fullpaths` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyContainer`|Parametro `String` facoltativo.<br /><br /> Specifica un contenitore che contiene una coppia di chiavi.  Tale parametro firmerà l'assembly, ossia assegnerà a quest'ultimo un nome sicuro, inserendo una chiave pubblica nel manifesto dell'assembly.  L'assembly finale verrà quindi firmato con la chiave privata.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/keyn[ame]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`KeyFile`|Parametro `String` facoltativo.<br /><br /> Specifica un file contenente una coppia di chiavi o solo una chiave pubblica da utilizzare per la firma di un assembly.  Durante la compilazione la chiave pubblica verrà inserita nel manifesto dell'assembly, mentre l'assembly finale verrà firmato con la chiave privata.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/keyf[ile]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`LinkResources`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Collega i file di risorse specificati a un assembly.  La risorsa diventa parte dell'assembly, ma il file non viene copiato.  Agli elementi passati a questo parametro possono essere associati metadati facoltativi denominati `LogicalName`, `Target` e `Access`.  Il metadato `LogicalName` viene utilizzato per specificare l'identificatore interno per la risorsa,  I metadati `Target` vengono utilizzati per specificare il percorso e il nome file in cui il file viene copiato e quindi compilato nell'assembly.  I metadati `Access` possono essere impostati su `private` per rendere la risorsa invisibile ad altri assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/link[resource]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`MainEntryPoint`|Parametro `String` facoltativo.<br /><br /> Specifica il nome completo \(*classe.metodo*\) del metodo da utilizzare come punto di ingresso durante la conversione di un modulo in un file eseguibile.  Questo parametro corrisponde all'opzione `/main` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`OutputAssembly`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> obbligatorio.<br /><br /> Specifica il nome del file generato dall'attività.  Questo parametro corrisponde all'opzione `/out` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Limita le piattaforme su cui è possibile eseguire il codice. I valori possibili sono: `x86`, `Itanium`, `x64` e `anycpu`.  Il valore predefinito è `anycpu`.  Questo parametro corrisponde all'opzione `/platform` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductName`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Product` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/prod[uct]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ProductVersion`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `ProductVersion` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/productv[ersion]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ResponseFiles`|Parametro `String[]` facoltativo.<br /><br /> Specifica i file di risposta contenenti opzioni aggiuntive da passare ad Assembly Linker.|  
|`SdkToolsPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso degli strumenti SDK, ad esempio resgen.exe.|  
|`SourceModules`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Si tratta di uno o più moduli da compilare in un assembly.  I moduli verranno elencati nel manifesto dell'assembly ottenuto. Affinché l'assembly venga caricato, è comunque necessario che i moduli vengano distribuiti e che siano disponibili.  È possibile che agli elementi passati a questo parametro siano associati metadati aggiuntivi denominati `Target`, in cui sono specificati il percorso e il nome di file in cui il file viene copiato e quindi compilato nell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa ad [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).  Questo parametro corrisponde all'elenco di moduli passati ad Al.exe senza utilizzare un'opzione specifica.|  
|`TargetType`|Parametro `String` facoltativo.<br /><br /> Specifica il formato del file di output. I valori possibili sono: `library` per le librerie di codici, `exe` per le applicazioni console e `win` per le applicazioni basate su Windows.  Il valore predefinito è `library`.  Questo parametro corrisponde all'opzione `/t[arget]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`TemplateFile`|Parametro `String` facoltativo.<br /><br /> Specifica l'assembly dal quale ereditare tutti i metadati dell'assembly, ad eccezione del campo relativo alle impostazioni cultura.  All'assembly specificato deve essere assegnato un nome sicuro.<br /><br /> Gli assembly creati con il parametro `TemplateFile` saranno assembly satellite.  Questo parametro corrisponde all'opzione `/template` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Timeout`|Parametro `Int32` facoltativo.<br /><br /> Specifica l'intervallo di tempo, in millisecondi, al termine del quale l'eseguibile dell'attività verrà interrotto.  Il valore predefinito è `Int.MaxValue`, con cui viene indicato che non è stato specificato alcun periodo di timeout.|  
|`Title`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Title` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/title` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`ToolPath`|Parametro `String` facoltativo.<br /><br /> Specifica il percorso da cui l'attività carica il file eseguibile sottostante \(Al.exe\).  Se questo parametro non è specificato, viene utilizzato il percorso di installazione SDK corrispondente alla versione del framework che esegue [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|`Trademark`|Parametro `String` facoltativo.<br /><br /> Specifica una stringa per il campo `Trademark` dell'assembly.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/trade[mark]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Version`|Parametro `String` facoltativo.<br /><br /> Specifica le informazioni sulla versione dell'assembly.  Il formato della stringa è *principale.secondario.build.revisione*.  Il valore predefinito è 0.  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/v[ersion]` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Icon`|Parametro `String` facoltativo.<br /><br /> Inserisce nell'assembly un file ico  Il file .ico fornisce al file di output l'aspetto desiderato in Esplora file.  Questo parametro corrisponde all'opzione `/win32icon` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
|`Win32Resource`|Parametro `String` facoltativo.<br /><br /> Inserisce nel file di output una risorsa Win32 \(file res\).  Per ulteriori informazioni, vedere la documentazione relativa all'opzione `/win32res` di [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md).|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, che eredita dalla classe <xref:Microsoft.Build.Utilities.ToolTask>.  Per un elenco di tali parametri aggiuntivi e le relative descrizioni, vedere [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Esempio  
 Nell'esempio riportato di seguito viene creato un assembly con le opzioni specificate.  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## Vedere anche  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Tasks](../msbuild/msbuild-tasks.md)