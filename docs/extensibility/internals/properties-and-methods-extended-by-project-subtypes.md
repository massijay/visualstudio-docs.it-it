---
title: "Proprietà e metodi estesi dai sottotipi di progetto | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes, extended methods
- project subtypes, extended properties
ms.assetid: 2b9833bf-8551-4ae1-93db-197ba645c65e
caps.latest.revision: 17
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 38bb86636edeaeda4485b7ebe6c8a6349450343c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-and-methods-extended-by-project-subtypes"></a>Proprietà e metodi estesi dai sottotipi di progetto
Un sottotipo di progetto è presente una grande quantità di energia elettrica per influenzare il comportamento del progetto perché viene costruito un aggregatore di un progetto di base. Questa sezione vengono riepilogate alcune delle funzionalità che può essere migliorata o modificata dai sottotipi di progetto.  
  
## <a name="features-gained-by-aggregation"></a>Funzionalità ottenute dall'aggregazione  
 Nella tabella seguente sono riepilogate molti dei metodi di aggregazione consente sottotipi di progetto eseguire l'override nei progetti di base.  
  
|Metodi di override da parte di aggregazione|Sottotipo di progetto|  
|---------------------------------------|---------------------|  
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetGuidProperty%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetGuidProperty%2A>|Consente a un sottotipo di progetto per<br /><br /> -Modificare didascalia e l'icona del nodo di progetto.<br />-Eseguire l'override completamente progetto `Browse` oggetto.<br />-Controllare se è possibile rinominare progetto.<br />-Controllo di ordinamento.<br />-Contesto utente controllo per la Guida dinamica.|  
|Da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>:</xref:Microsoft.VisualStudio.Shell.Interop.IVsProject><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetItemContext%2A>|Consente a un sottotipo di progetto controllare quali servizi contestuali disponibili per gli editor e finestre di progettazione.|  
|Da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>|Consente a un sottotipo di progetto per<br /><br /> -Partecipare del routing dei comandi per i comandi di progetto.<br />-Aggiungere, rimuovere o disabilitare comandi ambiente progetto e i comandi attivi di Esplora soluzioni.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2></xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>|Consente il sottotipo di progetto filtrare quanto viene visualizzato all'utente il **Aggiungi nuovo elemento** la finestra di dialogo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGeneratorFactory>|Consente a un sottotipo di progetto per<br /><br /> -Determinare il generatore predefinito ha un'estensione di file.<br />-Eseguire il mapping di un nome generatore leggibile umano a un oggetto COM.|  
  
## <a name="properties-used-by-project-subtypes"></a>Proprietà utilizzate dai sottotipi di progetto  
 Il sistema di progetto ambiente e di base può utilizzare le proprietà da <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>e <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2>enumerazioni dettagliate nella tabella seguente per abilitare un sottotipo di progetto controllare diverse funzionalità del sistema del progetto.</xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> </xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID>  
  
|Proprietà VSHPROPID|Sottotipo di progetto|  
|------------------------|---------------------|  
|`AddItemTemplatesGuid`|Consente a un sottotipo di progetto controllare il contenuto di **Aggiungi elemento** la finestra di dialogo. Il sottotipo di progetto può fornire una nuova specifica le directory di aggiungere nuovi tipi di elementi, rimuovere elementi esistenti e riorganizzare un sottoinsieme degli elementi del progetto base **Aggiungi elemento** la finestra di dialogo.|  
|`PropertyPagesCLSIDList`|Consente a un sottotipo di progetto aggiungere o rimuovere pagine delle proprietà indipendenti dalla configurazione.|  
|`CfgPropertyPagesCLSIDList`|Consente a un sottotipo di progetto aggiungere o rimuovere pagine delle proprietà dipendenti dalla configurazione.|  
|`ExtObjectCATID`|Consente a un sottotipo di progetto fornire un'estensione di automazione per il progetto o il progetto oggetti elemento conoscendo il CATID dell'oggetto Extender. Ad esempio, un sottotipo di progetto può fornire un oggetto personalizzato `Project.Extender("<subtype>")` oggetto.|  
|`BrowseObjectCATID`|Consente a un sottotipo di progetto fornire un'estensione di automazione per il `Browse` oggetto conoscendo il CATID dell'oggetto Extender. Ad esempio, un sottotipo di progetto possa aggiungere altre proprietà per il <xref:EnvDTE.Project.Properties%2A>insieme.</xref:EnvDTE.Project.Properties%2A>|  
|`CfgBrowseObjectCATID`|Consente a un sottotipo di progetto fornire un'estensione di automazione per l'oggetto Sfoglia configurazione di progetto. Ad esempio, un sottotipo di progetto possa aggiungere altre proprietà per il <xref:EnvDTE.Configuration.Properties%2A>insieme.</xref:EnvDTE.Configuration.Properties%2A>|  
|`CfgExtObjectCATID`|Consente a un sottotipo di progetto fornire un'estensione di automazione per l'oggetto di configurazione.|  
|`DefaultPlatformName`|Consente a un sottotipo di progetto determinare il nome della piattaforma per gli oggetti di configurazione del progetto.|  
  
 Il progetto di base fornisce un'implementazione predefinita di queste proprietà. Il progetto di base ottiene queste informazioni chiamando `QueryInterface` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>il sottotipo di progetto più esterno, consentendo in tal modo il sottotipo di progetto per l'override dell'implementazione delle proprietà.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
## <a name="see-also"></a>Vedere anche  
 [Sottotipi di progetto](../../extensibility/internals/project-subtypes-design.md)
