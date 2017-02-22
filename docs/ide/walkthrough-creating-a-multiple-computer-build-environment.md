---
title: "Procedura dettagliata: creazione di un ambiente di compilazione con pi&#249; computer | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ambiente di compilazione, MSBuild"
  - "MSBuild, compilazione in più computer"
ms.assetid: ae5391b1-3eec-42f5-beb3-f28630615a9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura dettagliata: creazione di un ambiente di compilazione con pi&#249; computer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare un ambiente di compilazione all'interno dell'organizzazione installando Visual Studio su un computer host e quindi copiando i file e le impostazioni in un altro computer in modo che questo possa partecipare alle compilazioni.  Non è necessario installare Visual Studio su l'altro computer.  
  
 Questo documento non conferisce il diritto di ridistribuire il software esternamente o di fornire ambienti di sviluppo a terze parti.  
  
||  
|-|  
|Dichiarazione di non responsabilità<br /><br /> Questo documento viene fornito di base “così comè”.  Mentre sono stati testati tutti i passi descritti, non si è in grado di testare in modo esaustivo ogni configurazione.  Il documento verrà tenuto aggiornato il più possibile man mano che nuove informazioni saranno disponibili.  Le informazioni contenute nel presente documento, inclusi gli URL e altri riferimenti a siti Web, possono essere soggette a modifiche senza preavviso.  Microsoft non offre alcuna garanzia, esplicita o implicita, riguardo alle informazioni fornite in questo documento.  L'utente deve farsi carico del rischio del loro utilizzo.<br /><br /> Questo documento non fornisce alcun diritto legale a qualsiasi proprietà intellettuale di un qualsiasi prodotto Microsoft.  È possibile copiare e utilizzare questo documento per scopi personali o come riferimento.<br /><br /> Non vi è alcun obbligo di fornire a Microsoft suggerimenti, commenti o altri feedback \("Feedback"\) relativi al documento.  Tuttavia, le informazioni immesse volontariamente possono essere utilizzate per prodotti Microsoft, specifiche correlate o in altre documentazioni \("Opzioni di Microsoft"\) che a loro volta possono essere utilizzate da terze parti per compilare i propri prodotti.  Pertanto, se vengono forniti feedback a Microsoft su qualsiasi versione di questo documento o sulle opzioni Microsoft a cui questi si riferiscono, sia accetta: \(a\) Microsoft può liberamente utilizzare, riprodurre, distribuire, imporre una licenza o commercializzare i feedback in ogni opzione Microsoft; \(b\) Si concededono inoltre alle terze parti, senza spese, i diritti necessari per poter utilizzare o interfacciare altri prodotti con le opzioni Microsoft che incorporano i feedback; e \(c\) Non dovranno mai essere forniti a Microsoft feedback \(i\) che violano qualsiasi brevetto, copyright o altre proprietà o diritti intellettuali di terze parti; o \(ii\) altri termini di licenza che impongano di incorporare o derivare tali feedback nelle opzioni Microsoft, o in altre proprietà intellettuali Microsoft, per concederne una licenza o condividerle con terze parti.|  
  
 Questa procedura è stata validata per i seguenti sistemi operativi, eseguendo MSBuild dalla riga di comando e utilizzando Team Foundation Build.  
  
-   Windows 8 \(x86 e x64\)  
  
-   Windows 7 Ultimate  
  
-   Windows Server 2008 R2 Standard  
  
 Dopo aver completato i passaggi di questa procedura, è possibile utilizzare un ambiente multicomputer per compilare questi tipi di applicazioni:  
  
-   Applicazioni desktop C\+\+ che utilizzano Windows 8 SDK  
  
-   Applicazioni desktop Visual Basic o C\# destinate .NET Framework 4.5  
  
 L'ambiente multicomputer non può essere utilizzato per compilare questi tipi di applicazioni:  
  
-   Applicazioni [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)].  Per compilare applicazioni [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], è necessario installare Visual Studio sul computer di compilazione.  
  
-   Applicazioni desktop destinate a .NET Framework 4 o versioni precedenti.  Per compilare questi tipi di applicazioni, è necessario installare Visual Studio o gli assembly e gli strumenti di riferimento di .NET \(da Windows 7.1 SDK\) nel computer di compilazione.  
  
 Questa procedura è suddivisa in queste parti:  
  
-   [Installare il software nei computer](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingSoftware)  
  
-   [Copiare file dal computer host al computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles)  
  
-   [Creare le impostazioni del registro](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingRegistry)  
  
-   [Configurare le variabili d'ambiente del computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#SettingEnvVariables)  
  
-   [Installazione degli assembly di MSBuild nella Global Assembly Cache (GAC) nel computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC)  
  
-   [Compilazione di progetti](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#BuildingProjects)  
  
-   [Creare l'ambiente di compilazione in modo che possa essere verificato nel controllo del codice sorgente](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CreatingForSourceControl)  
  
## Prerequisiti  
  
-   Una copia autorizzata di Visual Studio Ultimate, Visual Studio Premium, o Visual Studio Professional  
  
-   Una copia di .NET Framework 4.5.1, scaricabile dal sito Web [Visual Studio](http://www.microsoft.com/visualstudio/eng/downloads#d-additional-software).  
  
##  <a name="InstallingSoftware"></a> Installare il software nei computer  
 Innanzitutto, installare il computer host e quindi installare il computer di compilazione.  
  
 Installando Visual Studio nel computer host, vengono creati i file e le impostazioni che verranno successivamente copiate nel computer di compilazione.  È possibile installare Visual Studio su un computer x86 o x64, ma l'architettura del computer di compilazione deve corrispondere all'architettura del computer host.  
  
#### Per installare il software nei computer  
  
1.  Nel computer host, installare Visual Studio.  
  
2.  Nel computer di compilazione, installare .NET Framework 4.5. Per verificare che sia installato, assicurarsi che il valore della chiave di registro HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full@Version inizi con "4.5".  
  
##  <a name="CopyingFiles"></a> Copiare file dal computer host al computer di compilazione  
 In questa sezione viene mostrata la copia dei file specifici, i compilatori, gli strumenti di compilazione, le risorse di MSBuild e le impostazioni del registro di sistema dal computer host al computer di compilazione.  Queste istruzioni presuppongono che sia stato installato Visual Studio nel percorso predefinito nel computer host; se è stato installato in un altro percorso, modificare di conseguenza i passaggi.  
  
-   In un computer x86, il percorso predefinito è C:\\Program Files\\Microsoft Visual Studio 11.0\\  
  
-   In un computer x64, il percorso predefinito è C:\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\  
  
 Si noti che il nome della cartella dei programmi dipende dal sistema operativo installato.  In un computer x86, il nome è \\Program Files\\; su un computer x64, il nome è \\Program Files \(x86\)\\.  Indipendentemente dall'architettura di sistema, in questa procedura ci si riferisce alla cartella dei programmi come %ProgramFiles%.  
  
> [!NOTE]
>  Nel computer di compilazione, tutti i file rilevanti devono trovarsi nella stessa unità; tuttavia, la lettera di unità di questo drive può essere diversa dalla letterà di unità del drive nel computer Host in cui è installato Visual Studio.  In ogni caso, è necessario tener conto della locazione dei file quando si creano le voci del registro di sistema come mostrato più avanti in questo documento.  
  
#### Per copiare i file di Windows SDK nel computer di compilazione  
  
1.  Se si dispone solo di Windows SDK per Windows 8, copiare queste cartelle in modo ricorsivo dal computer host al computer di compilazione:  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\bin\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Catalogs\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\DesignTime\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\include\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Lib\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\Redist\\  
  
    -   %ProgramFiles%\\Windows Kits\\8.0\\References\\  
  
     Se si posseggono anche questi altri kit Windows 8...  
  
    -   Kit di valutazione e distribuzione di Microsoft Windows  
  
    -   Kit del driver per Microsoft Windows  
  
    -   Kit di certificazione hardware di Microsoft Windows  
  
     ...potrebbero aver installato dei file nelle cartelle in %ProgramFiles%\\Windows Kits\\8.0\\ elencate nei passi precedenti, le cui condizioni di licenza non consentano diritti di tipo build\-serve.  Controllare le condizioni di licenza per ogni kit Windows installato per verificare se i file possono essere copiati nel computer di compilazione.  Se le condizioni di licenza non consentono diritti di tipo build\-serve, rimuovere i file dal computer di compilazione.  
  
2.  Copiare le seguenti cartelle in modo ricorsivo dal computer host al computer di compilazione:  
  
    -   %ProgramFiles%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\  
  
    -   %ProgramFiles%\\Common Files\\Merge Modules\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\ProjectComponents\\  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\V110\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETCore\\v4.5\\  
  
    -   %ProgramFiles%\\Reference Assemblies\\Microsoft\\Framework\\.NETFramework\\v4.5\\  
  
3.  Copiare questi file dal computer host al computer di compilazione  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msobj110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdb110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbcore.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\mspdbsrv.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\msvcdis110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\makehm.exe  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\VCVarsQueryRegistry.bat  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\Tools\\vsvars32.bat  
  
4.  Le seguenti librerie di runtime di Visual C\+\+ sono necessarie solo se si eseguono output di compilazione nel computer di compilazione. ad esempio come parte di un test automatizzato.  I file in genere si trovano in sottocartelle nel percorso %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x86\\ o %ProgramFiles%\\Microsoft Visual Studio 11.0\\VC\\redist\\x64\\, in base all'architettura di sistema.  Nei sistemi x86, copiare i file binari x86 nella cartella \\Windows\\System32\\.  Nei sistemi x64, copiare i file binari x86 nella cartella Windows\\SysWOW64\\ e i file binari x64 nella cartella Windows\\System32\\.  
  
    -   \\Microsoft.VC110.ATL\\atl110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcp110.dll  
  
    -   \\Microsoft.VC110.CRT\\msvcr110.dll  
  
    -   \\Microsoft.VC110.CXXAMP\\vcamp110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfc110u.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110.dll  
  
    -   \\Microsoft.VC110.MFC\\mfcm110u.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110chs.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110cht.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110deu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110enu.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110esn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110fra.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110ita.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110jpn.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110kor.dll  
  
    -   \\Microsoft.VC110.MFCLOC\\mfc110rus.dll  
  
    -   \\Microsoft.VC110.OPENMP\\vcomp110.dll  
  
5.  Copiare solo i seguenti file dalla cartella \\Debug\_NonRedist\\x86\\ o \\Debug\_NonRedist\\x64\\ nel computer di compilazione, come descritto in [Preparazione di un computer per il test per l'esecuzione di un file eseguibile di debug](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable).  Nessun altro file deve essere copiato.  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcp110d.dll  
  
    -   \\Microsoft.VC110.DebugCRT\\msvcr110d.dll  
  
    -   \\Microsoft.VC110.DebugCXXAMP\\vcamp110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfc110ud.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110d.dll  
  
    -   \\Microsoft.VC110.DebugMFC\\mfcm110ud.dll  
  
    -   \\Microsoft.VC110.DebugOpenMP\\vcomp110d.dll  
  
##  <a name="CreatingRegistry"></a> Creare le impostazioni del registro  
 È necessario creare voci nel registro di sistema per configurare le impostazioni di MSBuild.  
  
#### Per creare configurazioni del registro di sistema  
  
1.  Identificare la cartella padre per le voci del registro di sistema.  Tutte le voci del registro di sistema vengono create nella stessa chiave padre.  In un computer x86, la chiave padre è HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.  In un computer x64, la chiave padre è HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.  Indipendentemente dall'architettura di sistema, in questa procedura dettagliata ci si riferisce alla chiave padre come %RegistryRoot%.  
  
    > [!NOTE]
    >  Se l'architettura del computer host differisce da quella del computer di compilazione, assicurarsi di utilizzare la chiave padre appropriata in ogni computer.  Ciò è particolarmente importante se viene automatizzato il processo di esportazione.  
    >   
    >  Inoltre, se nel computer di compilazione si utilizza una lettera di unità diversa da quella utilizzata nel computer host, assicurarsi di modificare i valori delle voci del registro di sistema di conseguenza.  
  
2.  Creare le seguenti voci nel registro di sistema del computer di compilazione.  Tutte queste voci sono stringhe \(Type \=\= “REG\_SZ” nel registro di sistema\).  Impostare i valori di queste voci allo stesso modo dei valori corrispondenti nel computer host.  
  
    -   %RegistryRoot%\\.NETFramework\\v4.0.30319\\AssemblyFoldersEx\\VCMSBuild Public Assemblies@\(Default\)  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools@InstallationFolder  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools\-x86@InstallationFolder  
  
    -   %RegistryRoot%\\VisualStudio\\11.0@Source Directories  
  
    -   %RegistryRoot%\\VisualStudio\\11.0\\Setup\\VC@ProductDir  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir32  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkDir64  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkVer32  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@FrameworkVer64  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VC7@11.0  
  
    -   %RegistryRoot%\\VisualStudio\\SxS\\VS7@11.0  
  
    -   %RegistryRoot%\\Windows Kits\\Installed Roots@KitsRoot  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   %RegistryRoot%\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
     In un computer di compilazione x64, creare anche la seguente chiave del registro di sistema e verificare il computer host per determinare come impostarla.  
  
    -   %RegistryRoot%\\Microsoft SDKs\\Windows\\v8.0A\\WinSDK\-NetFx40Tools\-x64@InstallationFolder  
  
     Se il computer di compilazione è x64 e si desidera utilizzare la versione a 64 bit di MSBuild, o se si sta utilizzando il servizio di compilazione di Team Foundation Server, è necessario creare le seguenti voci nel registro di sistema a 64 bit nativo.  Verificare il computer host per determinare come impostare queste voci.  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\Setup\\VS@ProductDir  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath10  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\4.0\\11.0@VCTargetsPath11  
  
##  <a name="SettingEnvVariables"></a> Configurare le variabili d'ambiente del computer di compilazione  
 Per utilizzare MSBuild nel computer di compilazione, è necessario impostare le variabili di ambiente PATH.  È possibile utilizzare vcvarsall.bat per impostare le variabili, oppure configurarle manualmente.  
  
#### Per utilizzare vcvarsall.bat per impostare le variabili d'ambiente  
  
-   Aprire una finestra del prompt dei comandi nel computer di compilazione e eseguire %Program Files%\\Microsoft Visual Studio 11.0\\VC\\vcvarsall.bat.  È possibile utilizzare un argomento della riga di comando per specificare il set di strumenti che si desidera utilizzare come x86, x64 nativo o con il compilatore incrociato x64.  Se non si specifica un argomento dalla riga di comando, vengono utilizzati i set di strumenti x86.  
  
     La seguente tabella descrive gli argomenti supportati di vcvarsall.bat:  
  
    |Argomento di vcvarsall.bat|Compilatore|Architettura del computer di compilazione|Architettura dell'output di compilazione|  
    |--------------------------------|-----------------|-----------------------------------------------|----------------------------------------------|  
    |"x86" \(valore predefinito\)|Nativo a 32 bit|x86, x64|x86|  
    |x86\_amd64|x64 incrociato|x86, x64|x64|  
    |amd64|x64 nativo|x64|x64|  
  
     Se vcvarsall.bat viene eseguito correttamente, ovvero se non viene visualizzato alcun messaggio di errore, è possibile ignorare il passaggio successivo e proseguire alla sezione [Installazione degli assembly di MSBuild nella Global Assembly Cache (GAC) nel computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#InstallingMSBuildToGAC) di questo documento.  
  
#### Per impostare manualmente le variabili d'ambiente  
  
1.  Per configurare manualmente l'ambiente dalla riga di comando, aggiungere il seguente percorso alla variabile d'ambiente PATH:  
  
    -   %Program Files%\\Microsoft Visual Studio 11.0\\Common7\\IDE  
  
2.  Facoltativamente, è possibile aggiungere i seguenti percorsi alla variabile d'ambiente PATH per rendere più facile utilizzare MSBuild per compilare le soluzioni.  
  
     Se si desidera utilizzare il MSBuild nativamente a 32 bit, aggiungere questi percorsi alla variabile d'ambiente:  
  
    -   %Program Files%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools  
  
    -   %windir%\\Microsoft.NET\\Framework\\v4.0.30319  
  
     Se si desidera utilizzare il MSBuild nativamente a 64 bit, aggiungere questi percorsi alla variabile d'ambiente:  
  
    -   %Program Files%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\x64  
  
    -   %windir%\\Microsoft.NET\\Framework64\\v4.0.30319  
  
##  <a name="InstallingMSBuildToGAC"></a> Installazione degli assembly di MSBuild nella Global Assembly Cache \(GAC\) nel computer di compilazione  
 MSBuild richiede che siano installati degli assembly aggiuntivi nella GAC del computer di compilazione.  
  
#### Per copiare gli assembly dal computer host e installarli nel computer di compilazione  
  
1.  Copiare i seguenti assembly dal computer host al computer di compilazione:  Poiché saranno installati nella GAC, non importa dove saranno messi nel computer di compilazione.  
  
    -   %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.Build.CPPTasks.Common.v110.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\CommonExtensions\\Microsoft\\VC\\Project\\Microsoft.VisualStudio.Project.VisualC.VCProjectEngine.dll  
  
    -   %ProgramFiles%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\PublicAssemblies\\Microsoft.VisualStudio.VCProjectEngine.dll  
  
2.  Per installare assembly nella GAC, individuare gacutil.exe nel computer di compilazione, in genere si trova in %ProgramFiles%\\Microsoft SDKs\\Windows\\v8.0A\\bin\\NETFX 4.0 Tools\\.  Se non è possibile individuare la cartella, ripetere i passaggi nella sezione [Copiare file dal computer host al computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) di questa procedura.  
  
     Aprire una finestra del prompt dei comandi con permessi di amministrazione e eseguire questo comando per ogni file:  
  
     **gacutil \-i \<file\>**  
  
    > [!NOTE]
    >  Un riavvio potrebbe essere necessario affinché un assembly venga installato completamente nella GAC.  
  
##  <a name="BuildingProjects"></a> Compilazione di progetti  
 È possibile utilizzare Team Foundation Build per compilare progetti e soluzioni [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] o, è possibile compilarli dalla riga di comando.  Quando si utilizza Team Foundation Build per compilare i progetti, viene richiamato il file eseguibile di MSBuild che corrisponde all'architettura di sistema.  Dalla riga di comando, è possibile utilizzare MSBuild a 32 bit o a 64 bit ed è possibile scegliere l'architettura di MSBuild impostando la variabile d'ambiente PATH o richiamando direttamente il file eseguibile specifico per l'architettura di MSBuild.  
  
 Per utilizzare msbuild.exe dal prompt dei comandi, eseguire il comando seguente, dove *solution.sln* è un segnaposto per il nome della soluzione.  
  
 **msbuild** *solution.sln*  
  
 Per ulteriori informazioni su come utilizzare MSBuild dalla riga di comando, vedere [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Per compilare progetti [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è necessario utilizzare il set di strumenti della piattaforma "v110".  Se non si desidera modificare i file di progetto [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è possibile impostare il set di strumenti della piattaforma utilizzando questo argomento dalla riga di comando:  
>   
>  **msbuild** *solution.sln* **\/p:PlatformToolset\=v110**  
  
##  <a name="CreatingForSourceControl"></a> Creare l'ambiente di compilazione in modo che possa essere verificato nel controllo del codice sorgente  
 È possibile creare un ambiente di compilazione che può essere assegnato a diversi computer e non richiede i file di GAC o di modificare le impostazioni del registro di sistema.  I seguenti passaggi sono solo uno dei modi per eseguire questa operazione.  Questi passaggi vanno adatti alle caratteristiche uniche del proprio ambiente di compilazione.  
  
> [!NOTE]
>  È necessario disabilitare la compilazione incrementale in modo che tracker.exe non generi un errore durante la compilazione.  Per disabilitare la compilazione incrementale, impostare il seguente parametro di compilazione:  
>   
>  **msbuild** *solution.sln* **\/p:TrackFileAccess\=false**  
  
#### Per creare un ambiente di compilazione che può essere verificato nel controllo del codice sorgente  
  
1.  Creare una directory "Depot" sul computer host.  
  
     Questi passi si riferiscono alla directory come %Depot%.  
  
2.  Copiare le directory e i file come descritto nella sezione [Copiare file dal computer host al computer di compilazione](../ide/walkthrough-creating-a-multiple-computer-build-environment.md#CopyingFiles) di questa procedura, con l'eccezzione di copiare nella cartella %Depot% appena creata.  Ad esempio, copiare da %ProgramFiles%\\Windows Kits\\8.0\\bin\\ to %Depot%\\Windows Kits\\8.0\\bin\\.  
  
3.  Quando i file vengono inseriti in %Depot%, apportare le seguenti modifiche:  
  
    -   In %Depot%\\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPP.Targets, \\Microsoft.Cpp.InvalidPlatforms.targets\\, \\Microsoft.cppbuild.targets\\, e \\Microsoft.CppCommon.targets\\, cambiare ogni istanza di  
  
         AssemblyName\="Microsoft.Build.CppTasks.Common.v110, Version\=4.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a"  
  
         in  
  
         AssemblyFile\="$\(VCTargetsPath11\)Microsoft.Build.CppTasks.Common.v110.dll”.  
  
         La prima denominazione si riferiscie agli assembly del tipo GAC’ed.  
  
    -   In %Depot% \\MSBuild\\Microsoft.Cpp\\v4.0\\v110\\Microsoft.CPPClean.Targets, modificare ogni istanza di  
  
         AssemblyName\="Microsoft.Build.CppTasks.Common.v110, Version\=4.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a"  
  
         in  
  
         AssemblyFile\="$\(VCTargetsPath11\)Microsoft.Build.CppTasks.Common.v110.dll”.  
  
4.  Creare un file .props, ad esempio Partner.AutoImports.props, e inserirlo nella cartella radice che contiene i progetti.  Questo file viene utilizzato per impostare le variabili utilizzate da MSBuild per trovare le varie risorse.  Se le variabili non sono impostate in questo file, vengono impostate da altri file .props e .targets che si basano sui valori del registro di sistema.  Poiché non viene impostato alcun valore del registro di sistema, queste variabili sarebbero vuote e la compilazione fallirebbe.  Al contrario, aggiungere a questo a Partner.AutoImports.props:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <!-- This file must be imported by all project files at the top of the project file. -->  
    <Project ToolsVersion="4.0"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
    <VCTargetsPath>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath>  
    <VCTargetsPath11>$(DepotRoot)MSBuild\Microsoft.Cpp\v4.0\v110\</VCTargetsPath11>  
    <MSBuildExtensionsPath>$(DepotRoot)MSBuild</MSBuildExtensionsPath>  
    <MSBuildExtensionsPath32>$(DepotRoot)MSBuild</MSBuildExtensionsPath32>  
    <VCInstallDir_110>$(DepotRoot)Microsoft Visual Studio 11.0\VC\</VCInstallDir_110>  
    <VCInstallDir>$(VCInstallDir_110)</VCInstallDir>  
    <WindowsKitRoot>$(DepotRoot)Windows Kits\</WindowsKitRoot>  
    <WindowsSDK80Path>$(WindowsKitRoot)</WindowsSDK80Path>  
    <WindowsSdkDir_80>$(WindowsKitRoot)8.0\</WindowsSdkDir_80>  
    <WindowsSdkDir>$(WindowsSDKDir_80)</WindowsSdkDir>  
    <WindowsSdkDir_80A>$(DepotRoot)Microsoft SDKs\Windows\v8.0A\</WindowsSdkDir_80A>  
    </PropertyGroup>  
    </Project>  
    ```  
  
5.  In ognuno dei file di progetto, aggiungere la seguente riga all'inizio del file, dopo la riga `<Project Default Targets…>`.  
  
    ```  
    <Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), Partner.AutoImports.props))\Partner.AutoImports.props"/>  
    ```  
  
6.  Modifica l'ambiente dalla riga di comando come segue:  
  
    -   Impostare Depot\=*location of the Depot directory that you created in step 1*  
  
    -   Impostare path\=%path%;*location of MSBuild on the computer*;%Depot%\\Windows\\System32;%Depot%\\Windows\\SysWOW64;%Depot%\\Microsoft Visual Studio 11.0\\Common7\\IDE\\  
  
         Per una compilazione nativa a 64 bit, puntare ai 64 bit di MSBuild.  
  
## Vedere anche  
 [Preparazione di un computer per il test per l'esecuzione di un file eseguibile di debug](/visual-cpp/ide/preparing-a-test-machine-to-run-a-debug-executable)   
 [Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)