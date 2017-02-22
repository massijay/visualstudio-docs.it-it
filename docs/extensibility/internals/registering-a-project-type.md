---
title: "Registrazione di un tipo di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio SDK], nuovo progetto le voci del Registro di sistema"
  - "Registro di sistema, nuovi tipi di progetto"
  - "registrazione, nuovi tipi di progetto"
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrazione di un tipo di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si crea un nuovo tipo di progetto, è necessario creare voci del Registro di sistema che consente a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per riconoscere e utilizzare il tipo di progetto.  In genere si creano queste voci del Registro di sistema utilizzando un file di script del Registro di sistema \(rgs\).  
  
 Nell'esempio riportato di seguito, le istruzioni dal Registro di sistema forniti i percorsi predefiniti e i dati in cui applicabili, seguito da una tabella contenente le voci da script del Registro di sistema per ogni istruzione.  Le tabelle forniscono le voci e le informazioni aggiuntive di script sulle istruzioni.  
  
> [!NOTE]
>  Le seguenti informazioni del Registro di sistema sono progettate per essere un esempio del tipo e degli scopi delle voci negli script del Registro di sistema verranno scritte per registrare il tipo di progetto.  Le effettive voci e il relativo utilizzo di possono variare in base a requisiti specifici del tipo di progetto.  È necessario rivedere gli esempi disponibili per trovare uno che è molto simile al tipo di progetto che si sta sviluppando quindi per rivedere lo script del Registro di sistema per tale esempio.  
  
 Negli esempi provengono da HKEY\_CLASSES\_ROOT.  
  
## Esempio  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG\_SZ|`FigPrjFile`|Nome e descrizione dei file del tipo di progetto con estensione .figp.|  
|`Content Type`|REG\_SZ|`Text/plain`|tipo di contenuto per i file di progetto.|  
|`NullFile`|REG\_SZ|`Null`||  
|`@`|REG\_SZ|`%MODULE%,-206`|icona predefinita utilizzata per il progetto di questo tipo.  L'istruzione di %MODULE% viene completato nel Registro di sistema nel percorso predefinito della DLL del tipo di progetto.|  
|`@`|REG\_SZ|`&Open in Visual Studio`|Applicazione predefinito in cui questo tipo di progetto verrà aperto.|  
|`@`|REG\_SZ|`devenv.exe "%1"`|Comando predefinito che verrà eseguito quando un progetto di questo tipo è aperto.|  
  
 Negli esempi provengono da HKEY\_LOCAL\_MACHINE e si trovano nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\99.0Exp\\Packages\].  
  
## Esempio  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`\(impostazione predefinita\)|REG\_SZ|`FigPrj Project VSPackage`|Nome localizzabile del package VS registrato \(tipo di progetto\).|  
|`InprocServer32`|REG\_SZ|`%MODULE%`|Percorso della DLL del tipo di progetto.  L'ide carica questa DLL e passa il package VS CLSID a `DllGetClassObject` per ottenere <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> per costruire l'oggetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .|  
|`CompanyName`|REG\_SZ|`Microsoft`|Nome della società che ha causato il tipo di progetto.|  
|`ProductName`|REG\_SZ|`Figure Project Sample`|Nome del tipo di progetto.|  
|`ProductVersion`|REG\_SZ|`9.0`|Numero di versione della versione del tipo di progetto.|  
|`MinEdition`|REG\_SZ|`professional`|Edizione del package VS che viene registrato.|  
|`ID`|REG\_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|La chiave di caricamento del pacchetto per il progetto VSPackage.  La chiave viene convalidata quando un progetto viene caricato dopo che l'ambiente è stato avviato.|  
|`DllName`|REG\_SZ|`%RESOURCE_DLL%`|Nome file della DLL satellite contenente le risorse localizzate per il tipo di progetto.|  
|`Path`|REG\_SZ|`%RESOURCE_PATH%`|Percorso della DLL satellite.|  
|`FigProjectsEvents`|REG\_SZ|Vedere l'istruzione per valore.|determina la stringa di testo restituita per questo evento di automazione.|  
|`FigProjectItemsEvents`|REG\_SZ|Vedere l'istruzione per valore.|determina la stringa di testo restituita per questo evento di automazione.|  
  
 Tutti gli esempi seguenti sono presenti nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Esempio  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG\_SZ|`FigPrj Project`|Nome predefinito dei progetti di questo tipo.|  
|`DisplayName`|REG\_SZ|`#%IDS_PROJECT_TYPE%`|ID di risorsa del nome da recuperare dalla DLL satellite registrato con i pacchetti.|  
|`Package`|REG\_SZ|`%CLSID_Package%`|ID della classe del package VS registrato con i pacchetti.|  
|`ProjectTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito dei file di modello di progetto.  Si tratta dei file visualizzati dal nuovo modello di progetto.|  
|`ItemTemplatesDir`|REG\_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Percorso predefinito dei file di modello di elemento di progetto.  Si tratta dei file visualizzati dal modello di elemento nuovo aggiungi.|  
|`DisplayProjectFileExtensions`|REG\_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Consente all'IDE per implementare la finestra di dialogo di **Aprire** .|  
|`PossibleProjectExtensions`|REG\_SZ|`figp`|Utilizzato dall'IDE per determinare se il progetto aperto viene gestito da questo tipo di progetto \(factory del progetto\).  Il formato per più di un elemento è un elenco delimitato da punti e virgola.  Ad esempio “vdproj; vdp„.|  
|`DefaultProjectExtension`|REG\_SZ|`.figp`|Utilizzato dall'IDE come l'estensione di file predefinito per il tipo.|  
|`Filter Settings`|REG\_DWORD|Esterni, vedere le istruzioni e i commenti che seguono la tabella.|Queste impostazioni vengono utilizzate per configurare vari filtri per visualizzare i file nelle finestre di dialogo dell'interfaccia utente.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|ID di risorsa per aggiungere i modelli di elemento.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso degli elementi di progetto vengono visualizzati nella finestra di dialogo per il modello di **Aggiungi nuovo elemento** .|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Determina l'ordine nel nodo della struttura ad albero dei file visualizzati nella finestra di dialogo di **Aggiungi nuovo elemento** .|  
  
 Nella tabella seguente sono illustrate le opzioni dei filtri disponibili nel segmento di codice precedente.  
  
|opzione di filtro|Descrizione|  
|-----------------------|-----------------|  
|`CommonFindFilesFilter`|Indica che il filtro è uno dei filtri comuni nella finestra di dialogo di **Ricerca nei file** .  I filtri comuni sono elencati nell'elenco di filtri prima dei filtri non contrassegnati come comuni.|  
|`CommonOpenFilesFilter`|Indica che il filtro è uno dei filtri comuni nella finestra di dialogo di **file aperto** .  I filtri comuni sono elencati nell'elenco di filtri prima dei filtri non contrassegnati come comuni.|  
|`FindInFilesFilter`|Indica che il filtro verrà uno dei filtri nella finestra di dialogo di **Ricerca nei file** e verrà elencato dopo che i filtri comuni.|  
|`NotOpenFileFilter`|Indica che il filtro non verrà utilizzata nella finestra di dialogo di **file aperto** .|  
|`NotAddExistingItemFilter`|Indica che il filtro non verrà utilizzata nella finestra di dialogo di **elemento esistente** di aggiunta.|  
  
 Per impostazione predefinita, se un filtro non dispone di una o più di questi flag impostato, il filtro viene utilizzato nella finestra di dialogo di **aggiungere l'elemento esistente** e nella finestra di dialogo di **file aperto** dopo che i filtri comuni sono elencati.  Il filtro non è utilizzato nella finestra di dialogo di **Ricerca nei file** .  
  
 Tutti gli esempi seguenti sono presenti nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Esempio  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|ID di risorsa per i nuovi modelli di progetto.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito per i progetti tipo di progetto registrato.|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Imposta l'ordine dei progetti vengono visualizzati nella nuova finestra di dialogo della procedura guidata di progetti.|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo la finestra di dialogo Nuovo progetto.|  
  
 Tutti gli esempi seguenti sono presenti nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Projects\].  
  
## Esempio  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG\_SZ|Nessuno|Il valore predefinito che indica che le voci seguenti sono per i file esterni proietta le voci.|  
|`@`|REG\_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Valore ID di risorsa per i file nuovi modelli di elementi di aggiunta.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Percorso predefinito degli elementi visualizzati nella finestra di dialogo di **Aggiungi nuovo elemento** .|  
|`SortPriority`|REG\_DWORD|`100 (vcprx64)`|Stabilisce l'ordine di visualizzazione nel nodo della struttura ad albero della finestra di dialogo di **Aggiungi nuovo elemento** .|  
  
 Nell'esempio si trova nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\Menus\].  
  
## Esempio  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 I punti di ingresso del menu l'ide alla risorsa utilizzata per recuperare le informazioni del menu.  Quando questi dati sono stati uniti nel database del menu, la stessa chiave verrà aggiunto nella sezione di MenusMerged del Registro di sistema.  Il package VS non deve modificare direttamente alcun elemento nella sezione di MenusMerged.  Nel campo dati nella tabella riportata di seguito, esistono tre virgola\-separare\-campi.  Il primo campo identifica il percorso completo di un file di risorsa menu:  
  
-   Se il primo campo viene omesso, la risorsa menu viene caricata dalla DLL satellite identificato dal package VS GUID.  
  
 Il secondo campo identifica una risorsa menu ID del tipo CTMENU:  
  
-   Se l'ID della risorsa viene specificato e il percorso del file viene fornito dal primo parametro, una risorsa menu viene caricato dal percorso del file completo.  
  
-   Se ID di risorsa viene fornito, ma il percorso del file non è, la risorsa menu viene caricata dalla DLL satellite.  
  
-   Se il percorso del file completo viene fornito e l'ID della risorsa viene omesso, il file da caricare si prevede sia un file di CTO.  
  
 L'ultimo campo identifica il numero di versione della risorsa di CTMENU.  È possibile unire nuovamente il menu modifica del numero di versione.  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|%CLSID\_Package%|REG\_SZ|`,1000,1`|La risorsa per recuperare le informazioni del menu.|  
  
 Tutti gli esempi seguenti sono presenti nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\NewProjectTemplates\].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`@`|REG\_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Il valore ID di risorsa per le figure progetti nuovi modelli di progetto.|  
|`TemplatesDir`|REG\_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Percorso predefinito della nuova directory di progetti.  Gli elementi contenuti nella directory vengono visualizzati nella finestra di dialogo di **creazione guidata nuovo progetto** .|  
|`SortPriority`|REG\_DWORD|`41 (x29)`|Stabilisce l'ordine in cui i progetti vengono visualizzati nel nodo della struttura ad albero della finestra di dialogo di **nuovo progetto** .|  
|`NewProjectDialogOnly`|REG\_DWORD|`0`|0 indica che i progetti di questo tipo vengono visualizzati solo nella finestra di dialogo di **nuovo progetto** .|  
  
 Nell'esempio si trova nel Registro di sistema nella chiave \[HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\9.0Exp\\InstalledProducts\].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nome|Type|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|`Package`|REG\_SZ|`%CLSID_Package%`|ID della classe del package VS registrato.|  
|`UseInterface`|REG\_DWORD|`1`|1 indica che l'interfaccia utente verrà utilizzata per interagire con questo progetto.  0 indica che non esiste alcuna interfaccia dell'interfaccia utente.|  
  
 I file di The.vsz che controllano i nuovi tipi di progetto contengono spesso una voce di RELATIVE\_PATH.  Questo percorso è un percorso relativo specificato nella chiave di \\ProductDir entry of the project type in the following Setup:  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup  
  
 Ad esempio, i modelli di progetto organizzazione dei framework vengono aggiunti i seguenti voci del Registro di sistema:  
  
 HKEY\_LOCAL\_MACHINE \\ \\SOFTWARE\\Microsoft\\VisualStudio\\7.0Exp\\Setup\\EF\\ProductDir \= C:\\Program Files\\Microsoft Visual Studio\\EnterpriseFrameworks  
  
 Che indica se includere una voce di PROJECT\_TYPE\=EF nel file VSZ, l'ambiente cerca i file vsz nella directory di ProductDir specificata in precedenza.  
  
## Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Creazione di istanze di progetto tramite le factory di progetto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)