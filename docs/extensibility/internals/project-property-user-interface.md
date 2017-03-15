---
title: "Interfaccia utente delle proprietà del progetto | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 16
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: b344731061053abb208225a0480408ebbe682050
ms.lasthandoff: 02/22/2017

---
# <a name="project-property-user-interface"></a>Interfaccia utente di proprietà del progetto
Un sottotipo di progetto è possibile utilizzare gli elementi nel progetto **pagine delle proprietà** la finestra di dialogo come vengono forniti dal progetto di base, nascondere o rendere intere pagine e controlli di sola lettura come fornito o aggiungere pagine specifici del sottotipo di progetto per il **pagine delle proprietà** la finestra di dialogo.  
  
## <a name="extending-the-project-property-dialog-box"></a>Estendere la finestra di dialogo Proprietà progetto  
 Un sottotipo di progetto implementa estensioni di automazione e visualizzare oggetti di configurazione progetto. Implementare questi dispositivi Extender di <xref:EnvDTE.IFilterProperties>interfaccia particolari proprietà nascosti o di sola lettura.</xref:EnvDTE.IFilterProperties> Il **pagine delle proprietà** rispetta la finestra di dialogo del progetto di base, implementata dal progetto di base, il filtraggio eseguite da estensioni di automazione.  
  
 Il processo di estensione un **proprietà del progetto** di seguito viene illustrata la finestra di dialogo:  
  
-   Il progetto di base recupera le estensioni dal sottotipo di progetto mediante l'implementazione di <xref:EnvDTE80.IInternalExtenderProvider>interfaccia.</xref:EnvDTE80.IInternalExtenderProvider> L'esplorazione, automazione dei progetti e progetto configurazione Sfoglia oggetti del progetto di base tutti implementano questa interfaccia.  
  
-   L'implementazione di <xref:EnvDTE80.IInternalExtenderProvider>per l'oggetto Sfoglia di progetto e l'oggetto di automazione progetto delegare il <xref:EnvDTE80.IInternalExtenderProvider>implementazione di aggregatore sottotipo progetto (vale a dire che `QueryInterface` per <xref:EnvDTE80.IInternalExtenderProvider>sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>oggetto project).</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider> </xref:EnvDTE80.IInternalExtenderProvider>  
  
-   Implementa inoltre l'oggetto di progetto di base configurazione Sfoglia <xref:EnvDTE80.IInternalExtenderProvider>associare direttamente l'estensione di automazione dall'oggetto di configurazione di progetto sottotipo.</xref:EnvDTE80.IInternalExtenderProvider> L'implementazione di delegati per il <xref:EnvDTE80.IInternalExtenderProvider>interfaccia implementata dall'aggregatore sottotipo di progetto.</xref:EnvDTE80.IInternalExtenderProvider>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementata dall'oggetto Sfoglia configurazione di progetto, restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>oggetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, inoltre implementato dall'oggetto Sfoglia configurazione di progetto, restituisce il <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg>oggetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>  
  
-   Un sottotipo di progetto è possibile determinare il CATID appropriato per i vari oggetti estensibili del progetto di base in fase di esecuzione tramite il recupero dei seguenti <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>valori:</xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2></xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
 Per determinare il CATID per l'ambito del progetto, il sottotipo di progetto recupera le proprietà precedente per <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>dal `VSITEMID``typedef`.</xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT> Un sottotipo di progetto potrebbe inoltre voler controllare quali **pagine delle proprietà** finestre di dialogo vengono visualizzati per il progetto, le configurazioni dipendenti e indipendenti di configurazione. Alcuni sottotipi di progetto potrebbero essere necessario rimuovere le pagine predefinite e aggiungere pagine specifiche sottotipo di progetto. Per attivare questa opzione, il progetto client gestito chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>metodo per le proprietà seguenti:</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>  
  
-   `VSHPROPID_PropertyPagesCLSIDList`ovvero un elenco delimitato da punto e virgola di CLSID delle pagine delle proprietà indipendenti dalla configurazione.  
  
-   `VSHPROPID_CfgPropertyPagesCLSIDList —`un elenco delimitato da punto e virgola di CLSID delle pagine delle proprietà dipendenti dalla configurazione.  
  
 Poiché il progetto sottotipo aggregazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>dell'oggetto, è possibile sostituire la definizione di queste proprietà per controllare quali **pagine delle proprietà** vengono visualizzate finestre di dialogo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Il sottotipo di progetto possa recuperare queste proprietà del progetto di base interna e quindi aggiungere o rimuovere CLSID in base alle esigenze.  
  
 Nuove pagine delle proprietà aggiunte da un sottotipo di progetto sono passate un oggetto di esplorazione di configurazione di progetto rispetto all'implementazione di base di progetto. Questo oggetto Sfoglia configurazione di progetto supporta le estensioni di automazione. Per ulteriori informazioni su AutomationExtenders, vedere [implementazione e utilizzo delle estensioni di automazione](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Le pagine delle proprietà implementati dalla chiamata sottotipo progetto <xref:EnvDTE.Project.Extender%2A>per recuperare i propri progetti sottotipo configurazione Sfoglia oggetto estende l'oggetto visualizzazione di configurazione del progetto di base.</xref:EnvDTE.Project.Extender%2A>  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE.IFilterProperties></xref:EnvDTE.IFilterProperties>   
 [Finestra di dialogo Pagine delle proprietà](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
