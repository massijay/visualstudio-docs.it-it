---
title: "La registrazione di progetto e modelli di elemento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio SDK], aggiunta di elementi"
  - "Registro di sistema, la finestra di dialogo Aggiungi nuovo elemento"
  - "Finestra di dialogo Aggiungi nuovo elemento"
  - "Aggiungere la finestra di dialogo Nuovo progetto"
  - "Registro di sistema, la finestra di dialogo Aggiungi nuovo progetto"
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# La registrazione di progetto e modelli di elemento
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Tipi di progetto è necessario registrare le directory in cui si trovano i propri modelli di progetto e di elemento di progetto.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizza le informazioni di registrazione associate a tipi di progetto per determinare gli elementi da visualizzare nel **Aggiungi nuovo progetto** e **Aggiungi nuovo elemento** le finestre di dialogo.  
  
 Per ulteriori informazioni sui modelli, vedere [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Voci del Registro di sistema per i progetti  
 Gli esempi seguenti illustrano le voci del Registro di sistema in HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*versione*\>. Le tabelle di accompagnamento illustrano gli elementi utilizzati negli esempi.  
  
```  
[Projects\{ProjectGUID}]  
@="MyProjectType"  
"DisplayName"="#2"  
"Package"="{VSPackageGUID}"  
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"  
```  
  
|Nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|@|REG\_SZ|Nome predefinito di progetti di questo tipo.|  
|DisplayName|REG\_SZ|ID di risorsa del nome viene recuperato dalla DLL satellite registrato in pacchetti.|  
|Pacchetto|REG\_SZ|ID classe del pacchetto di registrazione in pacchetti.|  
|ProjectTemplatesDir|REG\_SZ|Percorso predefinito dei file di modello di progetto. Vengono visualizzati i file di modello di progetto per il **Nuovo progetto** modello.|  
  
### Registrazione di modelli di elemento  
 È necessario registrare la directory in cui vengono archiviati i modelli di elemento.  
  
```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|@|REG\_SZ|ID della risorsa per i modelli di Aggiungi elemento.|  
|TemplatesDir|REG\_SZ|Percorso degli elementi di progetto visualizzato nella finestra di dialogo per la **Aggiungi nuovo elemento** procedura guidata.|  
|TemplatesLocalizedSubDir|REG\_SZ|ID di risorsa di una stringa che assegna un nome di sottodirectory di TemplatesDir che contiene modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Carica la risorsa stringa dalla DLL satellite se sono stati, ogni DLL satellite può contenere un nome di sottodirectory localizzate diverse.|  
|SortPriority|REG\_DWORD|Impostare SortPriority per regolare l'ordine in cui i modelli vengono visualizzati nel **Aggiungi nuovo elemento** la finestra di dialogo. I valori superiori SortPriority vengono visualizzati in precedenza nell'elenco dei modelli.|  
  
### Registrazione di filtri di file  
 Facoltativamente, è possibile registrare i filtri che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene utilizzato quando viene richiesto per i nomi di file. Ad esempio, il [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] per filtrare l'il **Apri File** è la finestra di dialogo:  
  
 **File Visual c\# \(cs, resx, \*.settings, XSD, WSDL\), cs, resx, \*.settings, XSD, WSDL\)**  
  
 Per supportare la registrazione di più filtri, ogni filtro è registrato nella propria sottochiave HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ \<*versione*\> \\Projects\\ {\<*ProjectGUID*\>} \\Filters\\ \<*sottochiave*\>. Il nome della sottochiave è arbitrario. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ignora il nome della sottochiave e utilizza solo i valori.  
  
 È possibile controllare i contesti in cui viene utilizzato un filtro impostando flag, illustrato nella tabella seguente. Se un filtro non ha nessun flag impostato, verrà elencata dopo i filtri comuni nel **Aggiungi elemento esistente** la finestra di dialogo e **Apri** la finestra di dialogo, ma non verrà utilizzato nel **Cerca nei file** la finestra di dialogo.  
  
```  
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]  
@="#3"  
"CommonOpenFilesFilter"=dword:00000000  
"CommonFindFilesFilter"=dword:00000000  
"FindInFilesFilter"=dword:00000000  
"NotOpenFileFilter"=dword:00000000  
"NotAddExistingItemFilter"=dword:00000000  
"SortPriority"=dword:00000064  
```  
  
|Nome|Tipo|Descrizione|  
|----------|----------|-----------------|  
|CommonFindFilesFilter|REG\_DWORD|Rende il filtro a uno dei filtri comuni di **Cerca nei file** la finestra di dialogo. I filtri comuni sono elencati nell'elenco di filtri prima di filtri non è contrassegnato come comune.|  
|CommonOpenFilesFilter|REG\_DWORD|Rende il filtro a uno dei filtri comuni nel **Apri** la finestra di dialogo. I filtri comuni sono elencati nell'elenco di filtri prima di filtri non è contrassegnato come comune.|  
|FindInFilesFilter|REG\_DWORD|Elenca il filtro dopo i filtri in comune il **Cerca nei file** la finestra di dialogo.|  
|NotOpenFileFilter|REG\_DWORD|Indica che il filtro non viene utilizzato nel **Apri** la finestra di dialogo.|  
|NotAddExistingItemFilter|REG\_DWORD|Indica che il filtro non viene utilizzato nel **Aggiungi elemento esistente** la finestra di dialogo.|  
|SortPriority|REG\_DWORD|Impostare SortPriority per regolare l'ordine in cui vengono visualizzati i filtri. Valori più grandi SortPriority vengono visualizzati in precedenza nell'elenco dei filtri.|  
  
## Struttura di directory  
 Package VS può inserire le cartelle e file di modello in qualsiasi punto su un disco locale o remoto, purché la posizione è registrata tramite l'ambiente di sviluppo integrato \(IDE\). Tuttavia, per facilitare l'organizzazione, si consiglia la seguente struttura di directory nel percorso di installazione del prodotto.  
  
 \\Templates  
  
 \\Projects \(contiene i modelli di progetto\)  
  
 \\Applications  
  
 \\Components  
  
 \\ ...  
  
 \\ProjectItems \(contiene gli elementi del progetto\)  
  
 \\CLASSE  
  
 \\Form  
  
 \\Web pagina  
  
 \\HelperFiles \(contiene i file utilizzati negli elementi di progetto a più file\)  
  
 \\WizardFiles  
  
## Vedere anche  
 [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [Localizzazione di applicazioni](../../ide/localizing-applications.md)   
 [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)