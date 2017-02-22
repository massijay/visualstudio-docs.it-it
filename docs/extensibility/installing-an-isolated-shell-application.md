---
title: "Installazione di un&#39;applicazione Shell isolata | Microsoft Docs"
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
  - "Distribuzione di applicazioni basate su shell shell [Visual Studio]"
  - "Visual Studio shell, la distribuzione di applicazioni shell"
ms.assetid: 33416226-9083-41b5-b153-10d2bf35c012
caps.latest.revision: 40
caps.handback.revision: 40
ms.author: "gregvanl"
manager: "ghogen"
---
# Installazione di un&#39;applicazione Shell isolata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per installare un'applicazione di Shell è necessario eseguire la procedura seguente.  
  
-   Preparare la soluzione.  
  
-   Creare un pacchetto Windows Installer \(MSI\) per l'applicazione.  
  
-   Creare un programma di avvio automatico Setup.  
  
 Tutto il codice di esempio in questo documento provengono dal [Shell distribuzione esempio](http://go.microsoft.com/fwlink/?LinkId=262245), che è possibile scaricare da sito Web MSDN Code Gallery. L'esempio mostra i risultati dell'esecuzione di ciascuno di questi passaggi.  
  
## Prerequisiti  
 Per eseguire le procedure descritte in questo argomento, è necessario installare gli strumenti seguenti nel computer in uso.  
  
-   Visual Studio SDK  
  
-   Il [set di strumenti di Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=82720) versione 3.6  
  
 L'esempio richiede anche il Microsoft Visualization and Modeling SDK, che richiedono che non tutte le shell.  
  
## Preparazione della soluzione  
 Per impostazione predefinita, i modelli di Shell build con pacchetti VSIX, ma questo comportamento è destinato principalmente a scopo di debug. Quando si distribuisce un'applicazione di Shell, è necessario utilizzare pacchetti MSI per consentire l'accesso del Registro di sistema e per i riavvii durante l'installazione. Per preparare l'applicazione per la distribuzione MSI, eseguire la procedura seguente.  
  
#### Per preparare un'applicazione di Shell per la distribuzione MSI  
  
1.  Modificare ogni file vsixmanifest nella soluzione.  
  
     Nel `Identifier` elemento, aggiungere un `InstalledByMSI` elemento e un `SystemComponent` elemento, quindi impostare i relativi valori `true`.  
  
     Questi elementi impediscono il programma di installazione VSIX di tentare di installare i componenti e l'utente da disinstallarli tramite il **estensioni e aggiornamenti** la finestra di dialogo.  
  
2.  Per ogni progetto che contiene un manifesto VSIX, modificare le attività di compilazione per restituire il contenuto nel percorso da cui verrà installato MSI. Includere il manifesto VSIX nell'output di compilazione, ma non creare un file con estensione VSIX.  
  
## Creazione di un file MSI della shell  
 Per compilare il pacchetto MSI, è consigliabile utilizzare il [set di strumenti di Windows Installer XML](http://go.microsoft.com/fwlink/?LinkId=82720) che offre maggiore flessibilità rispetto a un progetto di installazione standard.  
  
 Nel file Product.wxs impostare blocchi di rilevamento e il layout dei componenti della Shell.  
  
 Quindi creare le voci del Registro di sistema, il file. reg per la soluzione sia in ApplicationRegistry.wxs.  
  
### Rilevamento dei blocchi  
 Un blocco di rilevamento è costituito da un `Property` elemento che specifica un prerequisito per il rilevamento e un `Condition` elemento che specifica un messaggio da restituire se i prerequisiti non sono presenti nel computer. Ad esempio, l'applicazione di Shell richiederà Microsoft Visual Studio Shell redistributable, e il blocco di rilevamento sarà simile al markup seguente.  
  
```xml  
<Property Id="ISOSHELLSFX"> <RegistrySearch Id="IsoShellSfx" Root="HKLM" Key="Software\Microsoft\DevDiv\vs\Servicing\\$(var.ShellVersion)\IsoShell\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Property Id="INTSHELLSFX"> <RegistrySearch Id="IntShellSfx" Root="HKLM" Key="SOFTWARE\Microsoft\DevDiv\vs\Servicing\$(var.ShellVersion)\devenv\$(var.ProductLanguage)" Name="Install" Type="raw" /> </Property> <Condition Message="This application requires $(var.IsoShellName).  Please install $(var.IsoShellName) then run this installer again."> <![CDATA[Installed OR ISOSHELLSFX]]> </Condition> <Condition Message="This application requires $(var.IntShellName).  Please install $(var.IntShellName) then run this installer again."> <![CDATA[Installed OR INTSHELLSFX]]> </Condition>  
  
```  
  
### Layout dei componenti della Shell  
 È necessario aggiungere gli elementi per identificare la struttura di directory di destinazione e i componenti da installare.  
  
##### Per impostare il layout dei componenti della Shell  
  
1.  Creare una gerarchia di `Directory` gli elementi per rappresentare tutte le directory per creare il file System nel computer di destinazione, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Directory Id="TARGETDIR" Name="SourceDir"> <Directory Id="ProgramFilesFolder"> <Directory Id="CompanyDirectory" Name="$(var.CompanyName)"> <Directory Id="INSTALLDIR" Name="$(var.FullProductName)"> <Directory Id="ExtensionsFolder" Name="Extensions" /> <Directory Id="Folder1033" Name="1033" /> </Directory> </Directory> </Directory> <Directory Id="ProgramMenuFolder"> <Directory Id="ApplicationProgramsFolder" Name="$(var.FullProductName)"/> </Directory> </Directory>  
    ```  
  
     Queste directory a cui fa riferimento `Id` quando vengono specificati i file che devono essere installati.  
  
2.  Identificare i componenti che richiedono la Shell e l'applicazione di Shell, come illustrato nell'esempio seguente.  
  
    > [!NOTE]
    >  Alcuni elementi possono fare riferimento alle definizioni in altri file con estensione wxs.  
  
    ```xml  
    <Feature Id="ProductFeature" Title="$(var.ShortProductName)Shell" Level="1"> <ComponentGroupRef Id="ApplicationGroup" /> <ComponentGroupRef Id="HelpAboutPackage" /> <ComponentRef Id="GeneralProfile" /> <ComponentGroupRef Id="EditorAdornment"/> <ComponentGroupRef Id="SlideShowDesignerGroup"/> <!-- Note: The following ComponentGroupRef is required to pull in generated authoring from project references. --> <ComponentGroupRef Id="Product.Generated" /> </Feature>  
    ```  
  
    1.  Il `ComponentRef` elemento fa riferimento a un altro file con estensione wxs che identifica i file necessari per il componente corrente. Ad esempio, GeneralProfile presenta la seguente definizione in HelpAbout.wxs.  
  
        ```xml  
        <Fragment Id="FragmentProfiles"> <DirectoryRef Id="INSTALLDIR"> <Directory Id="ProfilesFolder" Name="Profiles"> <Component Id='GeneralProfile' Guid='*'> <File Id='GeneralProfile' Name='General.vssettings' DiskId='1' Source='$(var.BuildOutputDir)Profiles\General.vssettings' KeyPath='yes' /> </Component> </Directory> </DirectoryRef> </Fragment>  
        ```  
  
         Il `DirectoryRef` elemento specifica in cui questi file nel computer dell'utente. Il `Directory` elemento specifica che verrà installato in una sottodirectory, mentre ogni `File` elemento rappresenta un file che viene compilato o che esiste come parte della soluzione e identifica in tale file è disponibile quando viene creato il file MSI.  
  
    2.  Il `ComponentGroupRef` elemento fa riferimento a un gruppo di altri componenti \(o i componenti e i gruppi di componenti\). Ad esempio, `ComponentGroupRef` in ApplicationGroup è definita come segue in Application.wxs.  
  
        ```xml  
        <ComponentGroup Id="ApplicationGroup"> <ComponentGroupRef Id="DebuggerProxy" /> <ComponentRef Id="MasterPkgDef" /> <ComponentRef Id="SplashResource" /> <ComponentRef Id="IconResource" /> <ComponentRef Id="WinPrfResource" /> <ComponentRef Id="AppExe" /> <ComponentRef Id="AppConfig" /> <ComponentRef Id="AppPkgDef" /> <ComponentRef Id="AppPkgDefUndef" /> <ComponentRef Id="$(var.ShortProductName)UI1033" /> <ComponentRef Id="ApplicationShortcut"/> <ComponentRef Id="ApplicationRegistry"/> </ComponentGroup>  
        ```  
  
    > [!NOTE]
    >  Le dipendenze per le applicazioni Shell \(Isolated\) sono necessari: DebuggerProxy, MasterPkgDef, risorse \(in particolare il file .winprf\), applicazione e PkgDefs.  
  
### Voci del Registro di sistema  
 Il modello di progetto Shell \(Isolated\) include un *NomeProgetto*file. reg per le chiavi del Registro di sistema da unire nell'installazione. Queste voci del Registro di sistema devono far parte del file MSI per l'installazione e a scopo di pulizia. È inoltre necessario creare i blocchi del Registro di sistema corrispondenti in ApplicationRegistry.wxs.  
  
##### Per integrare le voci del Registro di sistema in MSI  
  
1.  Nel **personalizzazione della Shell** cartella, aprire *NomeProgetto*. reg.  
  
2.  Sostituire tutte le istanze del token $ $RootFolder con il percorso della directory di installazione di destinazione.  
  
3.  Aggiungere eventuali altre voci del Registro di sistema richieste dall'applicazione.  
  
4.  Aprire ApplicationRegistry.wxs.  
  
5.  Per ogni voce del Registro di sistema in *NomeProgetto*. reg, aggiungere un blocco del Registro di sistema corrispondente, come negli esempi seguenti.  
  
    |*NomeProgetto*. reg|ApplicationRegisty.wxs|  
    |-------------------------|----------------------------|  
    |\[HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= "Oggetto DTE PhotoStudio"|\< Id RegistryKey \= radice 'DteClsidRegKey' \= 'HKCR' Key \=' $\(VAR. DteClsidRegKey\)' azione \= 'createAndRemoveOnUninstall' \><br /><br /> \< tipo RegistryValue \= 'stringa' nome \=' @' valore \=' $\(VAR. Oggetto ShortProductName\) DTE "\/ \><br /><br /> \< \/ RegistryKey \>|  
    |\[\\LocalServer32 HKEY\_CLASSES\_ROOT\\CLSID\\ {bb431796\-a179\-4df7\-b65d\-c0df6bda7cc6}\]<br /><br /> @\= "$RootFolder$\\PhotoStudio.exe"|\< Id RegistryKey \= radice 'DteLocSrv32RegKey' \= 'HKCR' Key \=' $\(VAR. \\LocalServer32 DteClsidRegKey\)' azione \= 'createAndRemoveOnUninstall' \><br /><br /> \< tipo RegistryValue \= 'stringa' nome \=' @' valore \='\[INSTALLDIR\] $\(VAR. .Exe ShortProductName\) "\/ \><br /><br /> \< \/ RegistryKey \>|  
  
     In questo esempio, Var.DteClsidRegKey risolve la chiave del Registro di sistema nella riga superiore. Var.ShortProductName si risolve in `PhotoStudio`.  
  
## Creazione di un programma di avvio automatico di installazione  
 MSI completato verrà installato solo se tutti i prerequisiti vengono installati prima. Per semplificare l'esperienza utente finale, creare un programma di installazione che raccoglie e installa tutti i prerequisiti prima di installare l'applicazione. Per garantire una corretta installazione, eseguire queste azioni:  
  
-   Imporre l'installazione dall'amministratore.  
  
-   Rileva se è installata Visual Studio Shell \(Isolated\).  
  
-   Eseguire uno o più programmi di installazione della Shell in ordine.  
  
-   Gestire le richieste di riavvio.  
  
-   Eseguire il file MSI.  
  
### Applicazione di installazione dall'amministratore  
 Questa procedura è necessaria per abilitare il programma di installazione di accedere alle directory necessaria, ad esempio \\Programmi\\.  
  
##### Per imporre l'installazione dall'amministratore  
  
1.  Aprire il menu di scelta rapida per il progetto di installazione e quindi scegliere **proprietà**.  
  
2.  In **File di configurazione del Linker\/proprietà\/manifesto**, impostare **il livello di esecuzione di controllo dell'account utente** a **requireAdministrator**.  
  
     Questa proprietà consente di inserire l'attributo che richiede il programma da eseguire come amministratore nel file manifesto incorporato.  
  
### Rilevamento di installazioni di Shell  
 Per determinare se è necessario installare Visual Studio Shell \(Isolated\), determinare innanzitutto se è già installato controllando il valore del Registro di sistema di HKLM\\Software\\Microsoft\\DevDiv\\vs\\Servicing\\ShellVersion\\isoshell\\LCID\\Install.  
  
> [!NOTE]
>  Questi valori vengono inoltre letti dal blocco di rilevamento della Shell in Product.wxs.  
  
 HKLM\\Software\\Microsoft\\AppEnv\\14.0\\ShellFolder Specifica il percorso in cui è stata installata Visual Studio Shell, è possibile cercare i file non esiste.  
  
 Per un esempio di come rilevare un'installazione di Shell, vedere il `GetProductDirFromReg` funzione di Utilities.cpp nell'esempio di distribuzione di Shell.  
  
 Se uno o entrambi di Visual Studio Shell che richiede il pacchetto non è installato nel computer, è necessario aggiungere all'elenco dei componenti da installare. Per un esempio, vedere il `ComponentsPage::OnInitDialog` funzione di ComponentsPage.cpp nell'esempio di distribuzione di Shell.  
  
### Esegue i programmi di installazione della Shell  
 Per eseguire i programmi di installazione di Shell, chiamare i componenti ridistribuibili di Visual Studio Shell utilizzando gli argomenti della riga di comando appropriati. Come minimo, è necessario utilizzare gli argomenti della riga di comando **\/norestart \/q** e verificare che il codice restituito determinare cosa deve essere eseguita successivamente. Nell'esempio seguente viene eseguita la Shell \(Isolated\) redistributable.  
  
```  
dwResult = ExecCmd("Vs_IsoShell.exe /norestart /q", TRUE);  
```  
  
### Esegue i programmi di installazione di Shell Language Pack  
 Se si trova invece che la shell o la shell sono state installate e semplicemente necessario un language pack, è possibile installare i language pack come illustrato nell'esempio seguente.  
  
```  
dwResult = ExecCmd("Vs_IsoShellLP.exe /norestart /q", TRUE);  
  
```  
  
### Decifrare i valori restituiti  
 In alcuni sistemi operativi, l'installazione di Visual Studio Shell \(Isolated\) richiede il riavvio. Questa condizione può essere determinata mediante il codice restituito della chiamata a `ExecCmd`.  
  
|Valore restituito|Descrizione|  
|-----------------------|-----------------|  
|ERROR\_SUCCESS|Installazione completata. È ora possibile installare l'applicazione.|  
|ERROR\_SUCCESS\_REBOOT\_REQUIRED|Installazione completata. È possibile installare l'applicazione dopo il riavvio del computer.|  
|3015|È in corso l'installazione. Per continuare l'installazione è necessario un riavvio del computer.|  
  
### Gestione riavvio  
 Quando è stato eseguito il programma di installazione di Shell utilizzando il **\/norestart** argomento, è specificato che non riavviare il computer o richiedere il riavvio del computer. Tuttavia, potrebbe essere necessario un riavvio ed è necessario assicurarsi che il programma di installazione continuerà dopo il riavvio del computer.  
  
 Per gestire correttamente i riavvii, assicurarsi che un solo programma di installazione è impostato per riprendere e che il processo di ripresa verrà gestito correttamente.  
  
 Se viene restituito ERROR\_SUCCESS\_REBOOT\_REQUIRED o 3015, il codice necessario riavviare il computer prima di continua l'installazione.  
  
 Per gestire i riavvii, eseguire queste azioni:  
  
-   Impostare il Registro di sistema per riprendere l'installazione all'avvio di Windows.  
  
-   Eseguire un riavvio del doppio del programma di avvio automatico.  
  
-   Eliminare la chiave di ResumeData Shell programma di installazione.  
  
-   Riavvio di Windows.  
  
-   Reimpostare il percorso di inizio del file MSI.  
  
### Impostazione del Registro di sistema per riprendere la configurazione all'avvio di Windows  
 Il HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\RunOnce\\ chiave del Registro di sistema viene eseguita all'avvio del sistema con autorizzazioni amministrative e quindi vengono cancellati.HKEY\_CURRENT\_USER contiene una chiave simile, ma viene eseguito come utente normale e non è appropriata per le installazioni. È possibile riprendere l'installazione inserendo un valore stringa nella chiave RunOnce che chiama il programma di installazione. Tuttavia, è consigliabile chiamare il programma di installazione utilizzando un **\/restart** o parametro simile per notificare all'applicazione che sta riprendendo anziché iniziare. È inoltre possibile includere parametri per indicare dove si è nel processo di installazione, è particolarmente utile nelle installazioni che potrebbero richiedere più riavvii.  
  
 Nell'esempio seguente viene illustrato un valore di chiave del Registro di sistema RunOnce per la ripresa di un'installazione.  
  
 `"c:\MyAppInstaller.exe /restart /SomeOtherDataFlag"`  
  
### L'installazione di Double il riavvio del programma di avvio automatico  
 Se il programma di installazione viene utilizzato direttamente dal RunOnce, sarà in grado di caricare completamente il desktop. Per rendere disponibile l'interfaccia utente completa, è necessario creare un'altra esecuzione del programma di installazione e terminare l'istanza RunOnce.  
  
 È necessario eseguire nuovamente il programma di installazione in modo da ottenere le autorizzazioni corrette, è necessario specificare le informazioni necessarie per conoscere in cui è stata interrotta prima del riavvio, come illustrato nell'esempio seguente.  
  
```  
if (_cmdLineInfo.IsRestart()) { TCHAR path[MAX_PATH]={0}; GetModuleFileName(NULL, path, MAX_PATH * sizeof(TCHAR)); ShellExecute( NULL, _T( "open" ), path, _T("/install"), 0, SW_SHOWNORMAL ); }  
  
```  
  
### Eliminare la chiave di ResumeData Shell programma di installazione  
 I set di programma di installazione della Shell di HKLM\\Software\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData chiave del Registro di sistema con i dati per riprendere l'installazione dopo il riavvio. Poiché l'applicazione, non la Shell programma di installazione, viene ripresa, eliminare tale chiave del Registro di sistema, come illustrato nell'esempio seguente.  
  
```  
CString resumeSetupPath(MAKEINTRESOURCE("SOFTWARE\\Microsoft\\VisualStudio\\14.0\\Setup\\ResumeData")); RegDeleteKey(HKEY_LOCAL_MACHINE, resumeSetupPath);  
```  
  
### Il riavvio di Windows  
 Dopo aver impostato le chiavi del Registro di sistema, è possibile riavviare Windows. Nell'esempio seguente richiama i comandi di riavvio per diversi sistemi operativi Windows.  
  
```  
OSVERSIONINFO ov; HANDLE htoken ; //Ask for the SE_SHUTDOWN_NAME token as this is needed by the thread calling for a system shutdown. if (OpenProcessToken(GetCurrentProcess(), TOKEN_ADJUST_PRIVILEGES | TOKEN_QUERY, &htoken)) { LUID luid ; LookupPrivilegeValue(NULL, SE_SHUTDOWN_NAME, &luid) ; TOKEN_PRIVILEGES    privs ; privs.Privileges[0].Luid = luid ; privs.PrivilegeCount = 1 ; privs.Privileges[0].Attributes = SE_PRIVILEGE_ENABLED ; AdjustTokenPrivileges(htoken, FALSE, &privs, 0, (PTOKEN_PRIVILEGES) NULL, 0) ; } //Use InitiateSystemShutdownEx to avoid unexpected restart message box try { if ( (ov.dwMajorVersion > 5) || ( (ov.dwMajorVersion == 5) && (ov.dwMinorVersion  > 0) )) { bExitWindows = InitiateSystemShutdownEx(0, _T(""), 0, TRUE, TRUE, REASON_PLANNED_FLAG); } else { #pragma prefast(suppress:380,"ignore warning about legacy api") bExitWindows = InitiateSystemShutdown(0, _T(""), 0, TRUE, TRUE); } } catch(...) { //advapi32.dll call not available! Will not restart! }  
  
```  
  
### Reimpostare il percorso iniziale di MSI  
 Prima del riavvio, la directory corrente è il percorso del programma di installazione, ma dopo il riavvio, la posizione diventa la directory system32. Il programma di installazione deve reimpostare la directory corrente prima di ogni chiamata MSI, come illustrato nell'esempio seguente.  
  
```  
CString GetSetupPath() { TCHAR file[MAX_PATH]; GetModuleFileName(NULL, file, MAX_PATH * sizeof(TCHAR)); CString path(file); int fpos = path.ReverseFind('\\'); if (fpos != -1) { path = path.Left(fpos + 1); } return path; }  
  
```  
  
### Esecuzione dell'applicazione MSI  
 Dopo l'installazione di Visual Studio Shell restituisce ERROR\_SUCCESS, è possibile eseguire il file MSI per l'applicazione. Poiché il programma di installazione fornisce l'interfaccia utente, avviare il file MSI in modalità non interattiva \(**\/q**\) e con la registrazione \(**\/L**\), come illustrato nell'esempio seguente.  
  
```cpp#  
TCHAR temp[MAX_PATH]; GetTempPath(MAX_PATH, temp); CString boutiqueInstallCmd, msi, log; CString cmdLine(MAKEINTRESOURCE("msiexec /q /I %s /L*vx %s REBOOT=ReallySuppress")); CString name(MAKEINTRESOURCE("PhotoStudioIntShell.msi")); log.Format(_T("\"%s%s.log\""), temp, name); msi.Format(_T("\"%s%s\""), GetSetupPath(), name); boutiqueInstallCmd.Format(cmdLine, msi, log); //TODO: You can use MSI API to gather and present install progress feedback from your MSI. dwResult = ExecCmd(boutiqueInstallCmd, FALSE);  
```  
  
## Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione di base Shell isolata](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)