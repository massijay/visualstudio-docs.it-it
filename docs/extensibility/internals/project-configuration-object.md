---
title: Oggetto di configurazione progetto | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
caps.latest.revision: 11
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
ms.openlocfilehash: 0518e4844dd7fa7710935f742bf44943a5ef945d
ms.lasthandoff: 02/22/2017

---
# <a name="project-configuration-object"></a>Oggetto di configurazione di progetto
L'oggetto di configurazione di progetto gestisce la visualizzazione delle informazioni di configurazione per l'interfaccia utente.  
  
 ![Configurazione di progetto Visual Studio](~/docs/extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Pagine delle proprietà di configurazione di progetto  
  
 Il Provider di configurazione di progetto gestisce le configurazioni di progetto. L'ambiente e altri pacchetti, per accedere e recuperare informazioni sulle configurazioni del progetto, di chiamare le interfacce associate all'oggetto Provider di configurazione di progetto.  
  
> [!NOTE]
>  È possibile creare o modificare i file di configurazione di soluzione a livello di codice. È necessario utilizzare `DTE.SolutionBuilder`. Vedere [configurazione di soluzione](../../extensibility/internals/solution-configuration.md) per ulteriori informazioni.  
  
 Per pubblicare un nome visualizzato da utilizzare nella configurazione dell'interfaccia utente, il progetto deve implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A> L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, che restituisce un elenco di `IVsCfg` puntatori che è possibile utilizzare per ottenere i nomi visualizzati per le informazioni di configurazione e piattaforma da elencare nell'interfaccia utente dell'ambiente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> La piattaforma e la configurazione attiva dipendono dalla configurazione del progetto nella configurazione soluzione attiva. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>metodo può essere utilizzato per recuperare la configurazione del progetto attivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A>  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>oggetto può essere implementato facoltativamente nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>dell'oggetto con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper>oggetto che consente di recuperare un `IVsProjectCfg2` oggetto in base al nome configurazione progetto canoniche.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>  
  
 È possibile fornire altri progetti e l'ambiente di accesso alle configurazioni di progetto per i progetti fornire un'implementazione del `IVsCfgProvider2::GetCfgs` per restituire uno o più oggetti di configurazione. I progetti possono inoltre implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, che eredita da `IVsProjectCfg` e quindi da `IVsCfg`, per fornire informazioni specifiche della configurazione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>supporta le piattaforme e le funzionalità per l'aggiunta, eliminazione e ridenominazione di configurazioni di progetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>  
  
> [!NOTE]
>  Poiché Visual Studio non è più limitato a due tipi di configurazione, il codice che elabora le configurazioni non deve essere scritte con presupposti relativi al numero di configurazioni, né deve scritto partendo dal presupposto che è un progetto che contiene solo una configurazione Debug o finale. In questo modo l'utilizzo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A>obsoleto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A>  
  
 La chiamata a `QueryInterface` sull'oggetto restituito da`IVsGetCfgProvider::GetCfgProvider` recupera `IVsCfgProvider2`. Se `IVsGetCfgProvider` non viene trovato chiamando `QueryInterface` sul `IVsProject3` oggetto progetto, è possibile accedere all'oggetto provider di configurazione chiamando `QueryInterface` sull'oggetto gerarchia radice browser per l'oggetto restituito per `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, o tramite un puntatore a restituito per il provider di configurazione `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2`principalmente fornisce l'accesso per compilare, eseguire il debug e distribuzione di oggetti di gestione e consente la libertà di output gruppo di progetti. I metodi di `IVsProjectCfg` e `IVsProjectCfg2` può essere utilizzato per implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>per gestire il processo di compilazione, e <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>puntatori per i gruppi di output di una configurazione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> </xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>  
  
 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione supporta anche se il numero di output contenuti all'interno di un gruppo può variare da una configurazione alla configurazione. I gruppi disponga inoltre le stesse informazioni di identificatore (nome canonico, nome visualizzato e informazioni di gruppo) da una configurazione alla configurazione all'interno di un progetto. Per ulteriori informazioni, vedere [configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md).  
  
 Per abilitare il debug, le configurazioni devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> `IVsDebuggableProjectCfg`è un'interfaccia facoltativa implementata dai progetti per consentire al debugger di una configurazione di avvio e viene implementato nell'oggetto di configurazione con `IVsCfg` e `IVsProjectCfg`. L'ambiente viene chiamato quando l'utente decide di avviare il debugger premendo F5.  
  
 `ISpecifyPropertyPages`e `IDispatch` vengono utilizzati in combinazione con le pagine delle proprietà per recuperare e visualizzare all'utente informazioni dipendenti dalla configurazione. Per ulteriori informazioni, vedere [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md)   
 [Pagine delle proprietà](../../extensibility/internals/property-pages.md)   
 [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md)
