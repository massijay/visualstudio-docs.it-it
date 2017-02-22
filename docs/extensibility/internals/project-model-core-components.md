---
title: "Componenti di base del modello di progetto | Microsoft Docs"
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
  - "modelli di progetto, gli oggetti e interfacce"
  - "modelli di progetto, i servizi"
ms.assetid: b2f572d3-b26d-4846-92d1-84055fac141a
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Componenti di base del modello di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le tabelle seguenti viene illustrato il modello di progetto.  Le descrizioni brevi nelle tabelle delle interfacce e i servizi identificati nel modello e le interfacce e i servizi associati agli oggetti specifici.  Inoltre, le tabelle sono illustrati in dettaglio le altre interfacce che sono facoltative la creazione e la manutenzione di progetto a seconda dei requisiti del tipo di progetto specifico.  
  
 Per ulteriori informazioni, vedere [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
### Oggetto del pacchetto  
  
|Interfaccia|Commenti|  
|-----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>|Inizializza un VSPackage IDE e rende disponibili i servizi dell'IDE.|  
  
### Oggetto factory di progetto  
  
|Interfaccia|Commenti|  
|-----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|Gestisce creare nuovi progetti e aprire i progetti esistenti.|  
  
### Oggetti di project  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>|Gestisce l'aggiunta e la rimozione degli elementi di progetto, aprire gli editor e gestisce il mapping tra ogni moniker del documento e `VSITEMID`.  eredita da `IVsProject` e da `IVsProject2`.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|Gestione della navigazione e visualizzare le proprietà e associati gli eventi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>|Consente l'esecuzione di comandi simile a quella di `IOleCommandTarget` per controlli quali taglia e rinominare che si applicano solo quando lo stato attivo si trova in esplora soluzioni.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Funge da destinazione comando primaria collegamento per una gerarchia del progetto.  È un'interfaccia standard per eseguire una query sugli oggetti per lo stato del comando o stato e controlli in esecuzione.  Disponibile quando non si specifica nella finestra di progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Coordina la persistenza dello stato del progetto.  In genere, lo stato del progetto è archiviato come file di progetto ma può essere adattato a sistemi di archiviazione che non sono basati su file.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>|Abilita il progetto gestire tutti gli aspetti di persistenza per gli elementi di progetto, spostandosi come i file su disco o oggetti in altri sistemi di archiviazione.  L'interfaccia di `IVsPeristHierarchyItem2` viene utilizzata per gli elementi che non implementano l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Coordina le interazioni con il controllo del codice sorgente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfgProvider>|abilita i progetti gestire le informazioni di configurazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>|Gestisce gli oggetti di configurazione del progetto, ad esempio Debug o di rilascio.  La compilazione, la distribuzione e le operazioni di debug vengono coordinati tramite oggetti di configurazione del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler>|Implementato dalle gerarchie di controllare eliminazione \(distruttiva\) o rimuovere le opzioni \(non distruttive\) per gli elementi della gerarchia.  Interfaccia di query sull'interfaccia di `IVsHierarchyDeleteHandler` dall'interfaccia di `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsGetCfgProvider>|Fornisce l'opzione di implementazione di avere l'oggetto che supporta l'interfaccia di `IVsCfgProvider2` su un'identità diversa COM che l'oggetto del progetto che implementa l'interfaccia di `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectStartupServices>|Interfaccia facoltativa distribuita per rendere il progetto estendibile da altri sviluppatori.  L'interfaccia di `IVsProjectStartupServices` consente a un VSPackage di terze parti per registrare un GUID che mantenute nel file di progetto in modo che ogni volta che il progetto venga, è necessario caricare il servizio di terze parti GUID nel file di progetto e nella chiamata `QueryService` per il GUID.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierWinClipboardHelperEvents>|Implementato dalle gerarchie di origine in una finestra di `UIHierarchy` per coordinare le operazioni relative agli Appunti come taglia, copia e incolla.  Utilizzare l'interfaccia di `AdviseClipboardHelperEvents` per registrare gli eventi degli Appunti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataSource2>|Fornisce informazioni su un elemento trascinato in relazione alla relativa origine dati durante un'operazione di trascinamento della selezione in una finestra gerarchia dell'interfaccia utente.  Chiamato dall'interfaccia di `IVsHierarchy` .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDropDataTarget>|Fornisce informazioni su un elemento trascinato relativo alla destinazione di rilascio durante un'operazione di trascinamento della selezione in una finestra gerarchia dell'interfaccia utente.  Chiamato dall'interfaccia di `IVsHierarchy` .|  
  
### Oggetto Configuration  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>|Fornisce informazioni su una configurazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>|abilita i progetti gestire le informazioni di configurazione.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|Consente a un progetto essere eseguito sotto il controllo del debugger.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>|Viene implementata da progetti di distribuzione che eseguono operazioni di distribuzione per altri progetti.|  
  
### Oggetto del generatore di configurazione  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>|Gestisce l'operazione della compilazione di una configurazione di progetto.|  
  
### Oggetti del progetto aggiuntivi  
  
|Interfacce|Commenti|  
|----------------|--------------|  
|`IDispatch`<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages>|Visualizzare le proprietà dell'elemento nella finestra di **Proprietà** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>|Output delle visualizzazioni per la distribuzione.|  
  
 Nella tabella seguente vengono elencate le brevi descrizioni dei servizi identificati nel modello di progetto.  
  
### Services  
  
|Servizio|Commenti|  
|--------------|--------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterProjectTypes>|Utilizzato da package VS che implementa i tipi di progetto per la registrazione della factory di progetto esistente con l'ide.  Il package VS necessario chiamare `QueryService` per questo servizio e registrare la factory di progetto quando il metodo di `IVsPackage::SetSite` viene chiamato.  Se il metodo di `SetSite` non viene chiamato, il progetto non viene creata un'istanza.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Fornisce l'accesso a idi interni, nozione incorporata di soluzione corrente, come la capacità di enumerare i progetti, creare nuovi progetti, avviso della rimozione delle modifiche di progetto, e così via.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>|Chiamato dai progetti che si desidera partecipare al controllo del codice sorgente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>|Gestisce una tabella dei documenti aperti per determinare se uno o più elementi di progetto sono già aperti.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument>|Contiene le interfacce e i metodi chiamati in realtà per aprire un elemento di progetto utilizzando l'editor standard o un editor specifico.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>|Obbligatorio essere chiamato da tutti i progetti in caso di aggiunta, eliminare o rinominare i relativi elementi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx>|Gestisce le modifiche a un file o una directory e notifica ai client quando i file selezionati sono stati modificati su disco.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>|Obbligatorio essere chiamato da tutti i progetti e editor prima di elementi modificati o li salvare.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolutionBuildManager>|Mantiene l'ordine delle operazioni di compilazione e distribuzione per le configurazioni del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellDebugger>|Fornisce l'accesso ai servizi di basso livello del debugger utilizzati per la maggior parte dei comandi di debug.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>|Consente di accedere alle informazioni di package VS sulle selezioni correnti e consente la comunicazione con la finestra di **Proprietà** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Fornisce la funzionalità dell'IDE Interfaccia di base, come la capacità di creare ed enumerare le finestre degli strumenti o le finestre di documento o di segnalare un errore all'utente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar>|Consente di accedere alla barra di stato dell'IDE.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibility3>|Utilizzato per implementare il modello di automazione.  Nel modello di progetto, sarà proprietà definirle che consente di creare un'istanza di tale oggetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIHierWinClipboardHelper>|Utilizzati per implementare gli eventi degli Appunti nell'oggetto del progetto nella gerarchia.  `SVsUIHierWinClipboardHelper` consente di eseguire correttamente taglia, copia e le operazioni Incolla.|  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/it-it/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Supporto di strumenti di esplorazione di simbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)