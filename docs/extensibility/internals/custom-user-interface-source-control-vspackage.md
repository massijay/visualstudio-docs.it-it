---
title: Interfaccia utente personalizzata (origine controllo VSPackage) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
caps.latest.revision: 28
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
ms.openlocfilehash: 0d4940ea62ac65671ffcb3bb29958e3d2e544c09
ms.lasthandoff: 02/22/2017

---
# <a name="custom-user-interface-source-control-vspackage"></a>Interfaccia utente personalizzata (origine controllo VSPackage)
Un VSPackage dichiara le voci di menu e i relativi stati predefinito tramite il file di tabella comandi di Visual Studio (vsct). Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) consente di visualizzare le voci di menu negli stati predefiniti finché non viene caricato il VSPackage. Successivamente, il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>viene chiamato per abilitare o disabilitare le voci di menu.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Un VSPackage è possibile impostare una chiave del Registro di sistema in modo VSPackage può essere caricati automaticamente in base a un contesto dell'interfaccia utente di comando, sebbene in genere un controllo origine VSPackage verrà caricato su richiesta anziché solo il passaggio a un particolare contesto dell'interfaccia utente. Per ulteriori informazioni sulla chiave del Registro di sistema AutoLoadPackages, vedere [gestione package VS](../../extensibility/managing-vspackages.md).  
  
## <a name="vspackage-ui"></a>Interfaccia utente di VSPackage  
 Un pacchetto di controllo di origine viene implementato come un VSPackage e non utilizza l'interfaccia utente da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ogni controllo del codice sorgente VSPackage debba specificare elementi dell'interfaccia utente, ad esempio voci di menu, gruppi di menu, finestre degli strumenti, barre degli strumenti e interfaccia utente necessarie per impostare le opzioni specifiche per il controllo del codice sorgente VSPackage. Questi elementi dell'interfaccia utente possono essere abilitati in modo statico o dinamico. Elementi dell'interfaccia utente statici definiti in un file vsct e vengono visualizzati se il package VS è stato caricato o non. Elementi dell'interfaccia utente dinamici siano visibili a seconda del contesto dell'interfaccia utente un comando specifico, ad esempio <xref:EnvDTE.Constants.vsContextNoSolution>, o come risultato di una chiamata al <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>(metodo).</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> </xref:EnvDTE.Constants.vsContextNoSolution> La visibilità degli elementi dell'interfaccia utente dinamici è conforme con la strategia per il caricamento ritardato di VSPackage.  
  
## <a name="ui-constraints-on-source-control-vspackages"></a>Vincoli dell'interfaccia utente nel controllo di origine VSPackage  
 Poiché il controllo del codice sorgente VSPackage non possa essere rimosse dall'IDE di dopo essere stato caricato, VSPackage deve essere in grado di immettere uno stato inattivo. Quando un VSPackage riceve notifica che non è più attivo, VSPackage disabilita la relativa interfaccia utente e Ignora intervento esterno dell'IDE. Implementazione del VSPackage di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>metodo deve nascondere comandi quando il package VS non è attivo.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>  
  
 Ogni controllo del codice sorgente VSPackage deve implementare il `IVsSccProvider` interfaccia. Due metodi sull'interfaccia, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>, deve essere implementata da VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A>  
  
 Il controllo del codice sorgente VSPackage potrebbe sottoscritti a vari eventi IDE, che sono implementati dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>e così via.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> Inoltre, il package VS hanno implementato le interfacce di callback basate sul Registro di sistema, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Questi devono tutti essere ignorati quando è inattivo.  
  
 Nell'elenco seguente mostra le interfacce lo stato attivo di un controllo del codice sorgente VSPackage interessate:  
  
-   Tenere traccia degli eventi di documenti del progetto.  
  
-   Eventi della soluzione.  
  
-   Interfacce di persistenza di soluzione. Quando è inattivo, pacchetti non dovrebbero scrivere in file con estensione sln e suo.  
  
-   Estensioni della proprietà.  
  
 Obbligatoria <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, e anche le interfacce facoltative associate al controllo del codice sorgente, non vengono chiamati quando il controllo del codice sorgente VSPackage è inattivo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> </xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
  
 Quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE viene avviato, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] imposta il contesto dell'interfaccia utente del comando per l'ID del controllo origine predefinita corrente ID VSPackage. In questo modo l'interfaccia utente statico del controllo di origine attiva VSPackage venga visualizzata nell'IDE senza effettivamente il caricamento di VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pause per VSPackage da registrare con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>prima di tutte le chiamate a VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>  
  
 Nella tabella seguente vengono illustrati i dettagli specifici su come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE nasconde gli elementi dell'interfaccia utente diversi.  
  
|Elemento dell'interfaccia utente|Descrizione|  
|-------------|-----------------|  
|Menu e barre degli strumenti|Il pacchetto di controllo di origine è necessario impostare gli stati di visibilità della barra degli strumenti e menu iniziali con l'ID di pacchetto di controllo di origine nel [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) sezione del file vsct. In questo modo il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE per impostare lo stato delle voci di menu in modo corretto senza caricamento VSPackage e chiamare un'implementazione del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>(metodo).</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>|  
|Finestre degli strumenti|Il controllo del codice sorgente VSPackage nasconde tutte le finestre di che sua proprietà quando viene reso inattivo.|  
|Controllo del codice sorgente VSPackage specifico le pagine delle opzioni|La chiave del Registro di sistema HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts consente un VSPackage impostare i contesti in cui richiede le pagine di opzioni da visualizzare. Una voce del Registro di sistema in questa chiave doveva essere creato utilizzando il servizio ID (SID) del servizio di controllo di origine e assegnarle un valore DWORD pari a 1. Ogni volta che un evento dell'interfaccia utente in un contesto VSPackage è registrato con il controllo del codice sorgente, verrà chiamato VSPackage se è attiva.|  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2></xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2></xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>   
 <xref:EnvDTE.Constants.vsContextNoSolution></xref:EnvDTE.Constants.vsContextNoSolution>   
 [La gestione di VSPackage](../../extensibility/managing-vspackages.md)
