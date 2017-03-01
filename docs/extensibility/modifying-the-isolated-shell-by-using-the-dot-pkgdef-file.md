---
title: Modifica la Shell isolata utilizzando il. Il File pkgdef | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: 27
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 41e91983aaf236682b4ce723143f4053b5189547
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modifica la Shell isolata utilizzando il. File pkgdef
Il file. pkgdef supporta le impostazioni che è possibile utilizzare per personalizzare un'applicazione shell isolata. Specifica i valori che vengono creati quando un'applicazione è installata in un computer e che viene fatto riferimento dalla shell di Visual Studio quando avvia l'applicazione. Le impostazioni sono organizzate nel file in base alle chiavi del Registro di sistema applicabili.  
  
> [!WARNING]
>  Si noti che quando si avvia Visual Studio non vengono analizzati i file. pkgdef che non vengono dichiarati nel file vsixmanifest del VSPackage.  
  
 Il file. pkgdef contiene sezioni che sono tutti identificate da una chiave, ovvero `[$RootKey$]` o `[$RootKey$\` *sottochiave*`]`, dove $ $RootKey è la chiave radice per l'applicazione.  
  
 Ogni sezione contiene coppie nome/valore con il seguente formato: `"` *ValueName*`"=`*valore*.  
  
 I valori sono una stringa racchiusa tra virgolette o un numero intero a 32 bit che viene rappresentato come un valore dword. I valori sono i seguenti vincoli:  
  
-   Tutti i valori dword sono in formato esadecimale, ad esempio `dword:00000001`.  
  
     Per i valori booleani, 1 rappresenta true e 0 rappresenta false.  
  
-   Tutte le stringhe GUID sono nel formato del Registro di sistema, ad esempio, `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Tutti gli identificatori di risorsa localizzabile avere il formato "@*resourceID*" o "#*resourceID*", dove *resourceID* è l'identificatore di risorsa nel pacchetto dell'interfaccia utente dell'applicazione, ad esempio, `"@102"`. Il pacchetto di interfaccia utente dell'applicazione è il pacchetto a cui fa riferimento nell'impostazione AppLocalizationPackage.  
  
 Di seguito è riportato un esempio:  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 È possibile aggiungere commenti al file. pkgdef. Un commento a riga singola dispone di due barre come i primi due caratteri.  
  
 Per un elenco delle stringhe di sostituzione, vedere [le stringhe di sostituzione utilizzate in. Pkgdef e. File Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 Nelle sezioni seguenti vengono descritti i valori del Registro di sistema che influiscono sul comportamento della shell di Visual Studio in modalità isolata. È inoltre possibile definire i valori del Registro di sistema aggiuntive per l'applicazione in questo file.  
  
> [!NOTE]
>  Se non viene fornita un'impostazione nel file. pkgdef, viene creata alcuna voce corrispondente nel Registro di sistema.  
  
## <a name="settings"></a>Impostazioni  
 Nella tabella seguente vengono descritti i valori definiti in [$$RootKey].  
  
|Name|Tipo|Valore|  
|----------|----------|-----------|  
|AddinsAllowed|dword|True se è possano caricare componenti aggiuntivi; in caso contrario, false.<br /><br /> Il valore predefinito è true.|  
|AllowsDroppedFilesOnMainWindow|dword|True se la finestra principale può accettare un file eliminati; in caso contrario, false. I file trascinati nella finestra principale vengono aperti utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> Ciò equivale all'apertura di un documento tramite il **aprire** comando il **File** menu nell'applicazione.<br /><br /> Il valore predefinito è true.|  
|AppIcon|string|Il percorso completo dell'icona del programma. Questa icona viene visualizzata nella barra del titolo a sinistra del nome dell'applicazione.<br /><br /> Il valore predefinito è "$ $RootFolder\\*solutionName*. ico", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|AppLocalizationPackage|string|Il GUID del package VS che contiene l'assembly satellite dell'interfaccia utente per l'applicazione. Questo pacchetto di Visual Studio include una versione compilata del file vsct e può includere altre stringhe localizzate. Set di funzionalità e i gruppi di comandi di menu possono essere attivati o disabilitati modificando le impostazioni nel file vsct progetto dell'interfaccia utente.<br /><br /> Il valore predefinito è "{*vsUiPackageGuid*}", dove *vsUiPackageGuid* è il GUID assegnato al pacchetto di interfaccia utente dell'applicazione.|  
|AppName|string|Nome dell'applicazione. Il nome viene visualizzato nella barra del titolo della finestra dell'applicazione.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
|CommandLineLogo|string|Il testo dell'intestazione quando l'applicazione viene eseguita in una finestra della console. Questa impostazione influisce solo sulle applicazioni che supportano operazioni di compilazione da riga di comando.<br /><br /> Il valore predefinito è "*companyName**solutionName* versione 1.0.", dove *companyName* è il nome della società fornito durante l'installazione di Windows, e *solutionName* è il nome del file di soluzione dell'applicazione.|  
|DefaultDebugEngine|string|Il GUID del valore predefinito di eseguire il debug del motore da utilizzare per l'applicazione.<br /><br /> Nota: Un GUID vuoto (tutti zero) indica che l'applicazione non specifica un motore di debug predefinito. In questo modo il debugger selezionare il motore di debug da utilizzare.<br /><br /> Il valore predefinito è "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|string|L'URL della pagina iniziale predefinita per la finestra del browser Web interna.<br /><br /> Se il **Home page** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [Web Browser, ambiente, finestra di dialogo Opzioni](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è l'URL della società fornita durante l'installazione di Windows.|  
|DefaultProjectsLocation|string|Il percorso completo della cartella di progetti predefinita. Di seguito è riportato un esempio:<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Se il **percorso progetti di Visual Studio** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [NIB: generale, progetti e soluzioni, finestra di dialogo Opzioni](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Il valore predefinito è "$ $MyDocuments\\*solutionName*", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|DefaultSearchPage|string|L'URL di pagina di ricerca predefinito per la finestra del browser Web interna.<br /><br /> Se il **pagina di ricerca** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [Web Browser, ambiente, finestra di dialogo Opzioni](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è "http://search.live.com".|  
|DefaultUserFilesFolderRoot|string|Cartella documenti del nome della cartella utente relativo all'utente corrente.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
|DisableOutputWindow|dword|Indica se la shell isolata deve considerare la finestra di output come disabilitato.<br /><br /> Se questo valore è impostato su true, Visual Studio non viene visualizzato l'output di manager di compilazione soluzioni nel **Output** finestra e nasconde il **Mostra finestra di Output a inizio compilazione** casella di controllo di **progetti e soluzioni** categoria il **opzioni** la finestra di dialogo.<br /><br /> Il valore predefinito è false.|  
|HideMiscellaneousFilesByDefault|dword|True per nascondere il **file esterni** per impostazione predefinita nella cartella **Esplora**; in caso contrario, false.<br /><br /> Se il **Mostra file esterni in Esplora soluzioni** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [documenti, ambiente, finestra di dialogo Opzioni](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> Il valore predefinito è false.|  
|HideSolutionConcept|dword|True per creare tutti i progetti di progetti in modalità autonoma e nascondere la soluzione e i comandi correlati alla soluzione per progetti autonomi per impostazione predefinita. in caso contrario, false.<br /><br /> Se il **Mostra sempre soluzione** opzione è disponibile nell'applicazione, quindi questa impostazione influisce anche lo stato predefinito dell'opzione. Per ulteriori informazioni, vedere [NIB: generale, progetti e soluzioni, finestra di dialogo Opzioni](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).<br /><br /> Il valore predefinito è false.|  
|NewProjDlgInstalledTemplatesHdr|string|Il nome dell'intestazione di modelli di Visual Studio nstalled nella **modelli** nell'elenco di **nuovo progetto** la finestra di dialogo. Questa è una stringa o un identificatore di risorsa localizzabile che viene caricato dal pacchetto di interfaccia utente dell'applicazione.<br /><br /> Il valore predefinito è "*solutionName* modelli installati", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|NewProjDlgSlnTreeNodeTitle|string|Il nome per il **soluzioni di Visual Studio** nodo il **i tipi di progetto** struttura ad albero nel **nuovo progetto** la finestra di dialogo. Questa è una stringa o un identificatore di risorsa localizzabile che viene caricato dal pacchetto di interfaccia utente dell'applicazione.<br /><br /> Il valore predefinito è "*solutionName* modelli installati", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|SolutionFileCreatorIdentifier|string|L'identificatore dell'applicazione, che viene visualizzata la seconda riga nei file di soluzione che vengono generati dall'applicazione. Questa linea indica l'applicazione che ha creato il file. Per convenzione, questo valore comprende sia il nome dell'applicazione e il numero di versione dell'applicazione. Di seguito è riportato un esempio:<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Il programma VSLauncher.exe, ovvero il programma predefinito per l'apertura di un file di soluzione Visual Studio, utilizza questa riga per determinare la versione di Visual Studio in cui aprire il file della soluzione. L'applicazione richiede un proprio servizio di avvio per gestire i file di soluzione associata. L'utilità di avvio può inoltre utilizzare la seconda riga nel file di soluzione per determinare in quale versione dell'applicazione per aprire la soluzione.<br /><br /> Nota: Il programma di Visual Studio VSLauncher.exe non gestisce i file con estensione sln creati da un'applicazione shell isolata.<br /><br /> Il valore predefinito è "*solutionName* File della soluzione, versione del formato 10,00", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|SolutionFileExt|string|L'estensione di nome file di soluzione per l'applicazione. Si consiglia di scegliere un'estensione nome file univoco (not.sln).<br /><br /> Il valore predefinito è "*solutionName*_sln", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|SplashScreenBitmap|string|Il percorso completo del file bitmap per la schermata per l'applicazione.<br /><br /> Il valore predefinito è "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|string|Identificatore di classe (CLSID) dell'oggetto di automazione per l'applicazione.<br /><br /> L'oggetto di automazione dell'applicazione è oggetto di primo livello per l'applicazione nel modello di automazione della shell di Visual Studio e implementa il <xref:EnvDTE._DTE?displayProperty=fullName>interfaccia.</xref:EnvDTE._DTE?displayProperty=fullName><br /><br /> Se l'oggetto di automazione di applicazioni è stato registrato correttamente con la chiave del Registro di sistema HKEY_CLASSES_ROOT\CLSID, quindi è possibile utilizzare il [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) funzione per creare direttamente un'istanza dell'applicazione.<br /><br /> La shell di Visual Studio questo CLSID viene utilizzato per registrare l'oggetto di automazione di applicazioni in esecuzione oggetto tabella (ROT) utilizzando il flag ACTIVEOBJECT_WEAK. Consente di utilizzare il [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)funzione per recuperare un puntatore a un'istanza in esecuzione dell'applicazione. Inoltre, se si definisce un ProgID dell'oggetto di automazione dell'applicazione, quindi la shell di Visual Studio registra inoltre ogni istanza dell'applicazione nella tabella ROT utilizzando moniker dell'elemento del form *progID*:*processID*, dove *progID* è il ProgID dell'oggetto di automazione dell'applicazione e *processID* è l'identificatore di processo per l'istanza dell'applicazione. Ad esempio, se si crea un moniker come segue:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString*`, &instanceMoniker)`<br /><br /> dove `instanceString` è il *progID*:*processID* stringa. quindi è possibile utilizzare `instanceMoniker` con la funzione GetObject imputrescibili per ottenere l'istanza.<br /><br /> Se l'impostazione ThisVersionDTECLSID viene omesso, quindi l'applicazione non viene esposto tramite il modello COM (Component Object). In questo caso, non è possibile creare un'istanza dell'applicazione chiamando il [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) funzione e non può essere registrato nella tabella ROT.<br /><br /> Ogni versione di un package VS deve essere un CLSID differente.<br /><br /> Il valore predefinito è il GUID generato da Visual Studio per l'oggetto di automazione dell'applicazione.|  
|ThisVersionSolutionCLSID|string|Il CLSID dell'oggetto soluzione per l'applicazione.<br /><br /> L'oggetto di automazione soluzione contiene informazioni sulla soluzione corrente aperta in un'istanza dell'applicazione e implementa il <xref:EnvDTE._Solution?displayProperty=fullName>interfaccia.</xref:EnvDTE._Solution?displayProperty=fullName><br /><br /> Se l'oggetto di automazione di soluzione è stato registrato correttamente con la chiave del Registro di sistema HKEY_CLASSES_ROOT\CLSID, quindi è possibile utilizzare il [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) funzione per creare direttamente un oggetto di soluzione per l'applicazione.<br /><br /> La shell di Visual Studio questo CLSID viene utilizzato per registrare l'oggetto di automazione di soluzione nella tabella ROT utilizzando il flag ACTIVEOBJECT_WEAK.<br /><br /> Se questa impostazione viene omessa, quindi la classe di soluzione non è registrata con il modello COM (Component Object) e non può essere creato un oggetto soluzione chiamando il [CComPtrBase:: CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) funzione e non può essere registrato nella tabella ROT.<br /><br /> Il valore predefinito è un GUID generato da Visual Studio per l'oggetto della soluzione dell'applicazione.|  
|UserFilesSubFolderName|string|Il nome della sottocartella nella cartella documenti dell'utente in cui l'applicazione crea sottocartelle e file utente.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
|UserOptsFileExt|string|L'estensione per i file di soluzione utente opzioni per l'applicazione.<br /><br /> Il valore predefinito è il nome del file di soluzione dell'applicazione.|  
  
## <a name="binding-path-settings"></a>Impostazioni del percorso di associazione  
 Il [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] chiave contiene l'elenco delle directory in cui la shell verifica per gli assembly. Queste directory vengono aggiunti all'elenco delle directory in cui la shell ricerche degli assembly privati per l'applicazione.  
  
 Per impostazione predefinita, le voci alcun percorso di associazione non vengono aggiunti al file. pkgdef. Tuttavia, le seguenti sottodirectory della directory di installazione di Visual Studio vengono automaticamente aggiunti all'elenco percorso di associazione dell'applicazione nel Registro di sistema.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Per aggiungere una directory nel percorso di associazione, aggiungere una voce nel formato "*directoryName*"="", dove *directoryName* è un percorso assoluto. Di seguito è riportato un esempio:  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Impostazioni del profilo  
 Nella tabella seguente vengono descritti i valori definiti per ogni pacchetto associato nel [$RootKey$ \Profile].  
  
|Name|Tipo|Valore|  
|----------|----------|-----------|  
|AutoSaveFile|string|La directory in cui l'applicazione archivia i file di salvataggio automatico.<br /><br /> Il valore predefinito è "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Impostazioni di DLL Satellite del pacchetto  
 Nella tabella seguente vengono descritti i valori che sono definiti in [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] per la DLL di ogni pacchetto associato satellite in *vsPackageGuid* è il GUID del pacchetto associati.  
  
|Name|Tipo|Valore|  
|----------|----------|-----------|  
|NomeDLL|string|Il nome di file della DLL.<br /><br /> Il valore predefinito è "*solutionName*ui.dll", dove *solutionName* è il nome del file di soluzione dell'applicazione.|  
|Path|string|La directory che contiene la DLL satellite.<br /><br /> Il valore predefinito è "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Impostazioni di voce di Menu pacchetto  
 La chiave del Registro di sistema [$RootKey$ \Menus] definisce i file di risorse dell'interfaccia utente per l'applicazione.  
  
 Valori di voci di menu hanno il formato "{*vsUiPackageGuid*}"=" *resourceId*, *versionNumber*", dove *vsUiPackageGuid* è il GUID del pacchetto di interfaccia utente dell'applicazione, *resourceId* è l'identificatore di risorsa della risorsa che contiene gli elementi dell'interfaccia utente, CTMENU e *versionNumber* è un numero di versione virtuale per la risorsa CTMENU. Per ulteriori informazioni, vedere [Assembly di interoperabilità la registrazione di gestori di comandi](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Per impostazione predefinita, viene creata una voce di menu nel file. pkgdef del pacchetto di applicazione dell'interfaccia utente.  
  
 Per ogni pacchetto che fornisce le voci di menu e che viene distribuito come parte dell'applicazione, aggiungere una voce di menu per il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione Shell isolata](../extensibility/customizing-the-isolated-shell.md)   
 [. File Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)
