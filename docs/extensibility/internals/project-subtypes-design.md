---
title: "Sottotipi di progetto | Microsoft Docs"
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
  - "sottotipi di progetto, progettazione"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
caps.handback.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
---
# Sottotipi di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I sottotipi di progetto let Vspackage estendere i progetti basati su Microsoft Build Engine \(MSBuild\).  L'utilizzo di aggregazione consente di riutilizzare la maggior parte del sistema del progetto gestito principale implementato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tuttavia ancora personalizzare il comportamento per un determinato scenario.  
  
 I seguenti argomenti sono descritti in dettaglio la progettazione di base e l'implementazione di sottotipi di progetto:  
  
-   Progettazione del sottotipo di progetto.  
  
-   aggregazione a più livelli.  
  
-   Interfacce di supporto.  
  
## Progettazione del sottotipo di progetto  
 L'inizializzazione di un sottotipo di progetto viene ottenuta mediante l'aggregazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> e gli obiettivi principali di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .  Questo aggregato consente a un sottotipo di progetto per eseguire l'override o aumentare la maggior parte delle funzionalità del progetto di base.  I sottotipi di progetto hanno la prima possibilità di gestire le proprietà utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, i controlli utilizzando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>e la gestione degli elementi di progetto utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>.  I sottotipi di progetto possono anche essere estesa:  
  
-   Oggetti di configurazione del progetto.  
  
-   oggetti dipendenti dalla configurazione.  
  
-   oggetti di esplorazione dell'Configurazione\-indipendente.  
  
-   Proiettare gli oggetti di automazione.  
  
-   Raccolte di proprietà di automazione del progetto.  
  
 Per ulteriori informazioni sull'estensibilità dai sottotipi di progetto, vedere [Proprietà e metodi estesi dai sottotipi di progetto](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### file di criteri  
 L'ambiente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce un esempio di estensione del sistema di progetto di base con un sottotipo di progetto nella relativa implementazione file di criteri.  Un file di criteri consente formazione dell' ambiente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]delle funzionalità che includono Esplora soluzioni, nella finestra di dialogo **aggiungere il progetto** , la finestra di dialogo di **Aggiungi nuovo elemento** e la finestra di dialogo **Proprietà** .  Il sottotipo di criteri esegue l'override di e migliora le funzionalità con <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` e le implementazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .  
  
##### meccanismo di aggregazione  
 Il meccanismo di aggregazione di sottotipo del progetto dell'ambiente supporta livelli di aggregazione più, consentendo pertanto a un sottotipo avanzato da implementare per ulteriori condimento un progetto condito.  Inoltre, gli oggetti supporto di un sottotipo di progetto, come <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sono progettati per consentire più livelli di sovrapposizione.  In conformità con i vincoli le regole di aggregazione COM e COM, sottotipi di progetto e i progetti di base devono essere implementati in modo cooperativo per abilitare il sottotipo interno o il progetto di base correttamente partecipare alle chiamate al metodo dell'autorizzazione e conteggi dei riferimenti gestire.  Ovvero il progetto su essere aggregatoe deve essere pianificata per supportare aggregato.  
  
 Nella figura seguente viene illustrata una rappresentazione schematica di un aggregato a più livelli sottotipo di progetto.  
  
 ![Rappresentazione grafica dei progetti multilivello Visual Studio](../../extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
Sottotipo multilivello di progetto  
  
 Un aggregato a più livelli sottotipo di progetto è costituito da tre livelli, un progetto di base, che verranno aggregati da un sottotipo di progetto, quindi ulteriormente aggregato da un sottotipo avanzato di progetto.  È incentrata sulla figura di alcune interfacce di supporto disponibili come una parte dell'architettura di sottotipo di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
##### meccanismi di distribuzione  
 Tra molte delle funzionalità di base del sistema del progetto avanzate da un sottotipo di progetto sono meccanismi di distribuzione.  Un sottotipo di progetto influisce sui meccanismi di distribuzione mediante l'implementazione delle interfacce di configurazione \(come <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\) recuperate chiamando QueryInterface su <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>.  In uno scenario in cui sia il sottotipo di progetto che il sottotipo avanzato di progetto aggiunte le implementazioni diverse di configurazione, le chiamate di base `QueryInterface` di progetto in `IUnknown`avanzato per il sottotipo di progetto.  Se il sottotipo interno di progetto contiene l'implementazione di configurazione cui il progetto di base viene richiesto, i delegati avanzati sottotipo di progetto all'implementazione fornivano il tipo interno del progetto.  Ad esempio un meccanismo per mantenere lo stato da un livello di aggregazione a un altro, tutti i livelli di sottotipi di progetto implementa <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> per rendere persistenti i dati XML correlati non compilazione nei file di progetto.  Per ulteriori informazioni, vedere [Rendere persistenti i dati nel File di progetto MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  <xref:EnvDTE80.IInternalExtenderProvider> viene implementato come meccanismo per recuperare le estensioni di automazione dai sottotipi di progetto.  
  
 I seguenti stati attivi mostrato nell'implementazione delle estensioni di automazione, l'oggetto di esplorazione di configurazione del progetto in particolare, utilizzato dai sottotipi di progetto per estendere il sistema di progetto di base.  
  
 ![Rappresentazione dell'Extender automatico delle caratteristiche dei progetti VS](../../extensibility/internals/media/vs_projectflavorautoextender.png "VS\_ProjectFlavorAutoExtender")  
Proiettare l'Extender di automazione del sottotipo.  
  
 I sottotipi di progetto possono ulteriormente estendere il sistema di progetto di base estendendo il modello a oggetti di automazione.  Questi sono definiti come parte dell'oggetto ActiveX DTE e vengono utilizzati per estendere l'oggetto del progetto, l'oggetto di `ProjectItem` e l'oggetto di `Configuration` .  Per ulteriori informazioni, vedere [Estendere il modello a oggetti del progetto di Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## aggregazione a più livelli  
 Un'implementazione di sottotipo di progetto che esegue il wrapping di un sottotipo di livello più basso di progetto deve essere programmato in modo cooperativo per consentire al sottotipo interno del progetto funzioni correttamente.  Un elenco delle responsabilità di programmazione include:  
  
-   L'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> del sottotipo di progetto che esegue il wrapping del sottotipo interno venga delegati <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> l'implementazione del sottotipo interno del progetto sia per <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> che i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .  
  
-   L'implementazione di <xref:EnvDTE80.IInternalExtenderProvider> del sottotipo di progetto del wrapper deve delegare quello del sottotipo interno del progetto.  In particolare, l'implementazione delle necessità di <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> di ottenere la serie di nomi dal sottotipo interno del progetto e quindi di concatenare stringhe che desidera aggiungere come estensioni.  
  
-   L'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> di un sottotipo di progetto del wrapper deve creare un'istanza dell'oggetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> del sottotipo interno del progetto e utilizzarla come delegato privato, poiché solo l'oggetto di base della configurazione del progetto direttamente sa che l'oggetto di configurazione sottotipo di progetto del wrapper esistente.  Il sottotipo esterno di progetto può inizialmente scegliere le interfacce di configurazione desidera gestire direttamente e quindi delegate dal resto dell'implementazione interna del sottotipo di progetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## Interfacce di supporto  
 Il progetto di base delega le chiamate le interfacce di supporto aggiunte da un sottotipo di progetto, per estendere vari aspetti dell'implementazione.  Sono inclusi gli oggetti estensione di configurazione del progetto e diversi oggetti del Visualizzatore proprietà.  Queste interfacce vengono recuperate chiamando `QueryInterface` su `punkOuter` \(un puntatore a `IUnknown`\) dell'aggregatore più esterno sottotipo di progetto.  
  
|Interfaccia|proiettare il sottotipo|  
|-----------------|-----------------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|Consente il sottotipo di progetto a:<br /><br /> -   Fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-   Controllareavvio del debugger in modo che il sottotipo di progetto fornisce la propria implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-   Disabilitare la valutazione di espressioni in fase di progettazione in modo appropriato gestendo il caso di `DBGLAUNCH_DesignTimeExprEval` nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|Consente il sottotipo di progetto a:<br /><br /> -   Estendere <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> del progetto aggiungere o rimuovere le proprietà indipendenti di configurazione del progetto.<br />-   Estendere l'oggetto ActiveX di progetto \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\) del progetto.<br /><br /> I valori delle proprietà sopra derivano dall'enumerazione di <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Consente il sottotipo di progetto al mapping dell'oggetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> fornito l'oggetto di esplorazione di configurazione del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Consente il sottotipo di progetto al mapping a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> l'oggetto o di `VSITEMID` , visto l'oggetto di esplorazione di configurazione del progetto.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Consente al sottotipo di progetto permanga i dati strutturati XML arbitrari nel file di progetto \(con estensione csproj o vbproj\).  questi dati non sono visibili a MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|Consente il sottotipo di progetto a:<br /><br /> -   Aggiungere nuove proprietà MSBuild rendere persistenti.<br />-   Rimuovere le proprietà non necessari da MSBuild.<br />-   Query per un valore corrente di una proprietà MSBuild.<br />-   Modificare il valore corrente di una proprietà MSBuild.|  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>