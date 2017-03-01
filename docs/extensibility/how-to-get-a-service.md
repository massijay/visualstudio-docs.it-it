---
title: 'Procedura: ottenere un servizio | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
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
ms.openlocfilehash: f66c7e1f01c8d8eb69c6718314890bfb02cccc17
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-get-a-service"></a>Procedura: ottenere un servizio
È spesso necessario ottenere servizi di Visual Studio per accedere alle funzionalità diverse. In generale, un servizio di Visual Studio fornisce una o più interfacce che è possibile utilizzare. È possibile ottenere la maggior parte dei servizi da un VSPackage.  
  
 Un package VS che deriva da <xref:Microsoft.VisualStudio.Shell.Package>e che è stato individuato correttamente può richiedere qualsiasi servizio globale.</xref:Microsoft.VisualStudio.Shell.Package> Poiché implementa la classe del pacchetto <xref:System.IServiceProvider>, qualsiasi package VS che deriva dal pacchetto è anche un provider di servizi.</xref:System.IServiceProvider>  
  
 Quando viene caricata in Visual Studio un <xref:Microsoft.VisualStudio.Shell.Package>, passa un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>dell'oggetto per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>metodo durante l'inizializzazione.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> </xref:Microsoft.VisualStudio.Shell.Package> Si tratta di *posa* VSPackage. La classe del pacchetto viene eseguito il wrapping di questo provider di servizi e fornisce il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>metodo per i servizi.</xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Recupero di un servizio da un VSPackage inizializzato  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene le risorse di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `GetServiceExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  A questo punto aggiungere un modello di elemento di comando personalizzato denominato **GetServiceCommand**. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **GetServiceCommand.cs**. Per ulteriori informazioni su come creare un comando personalizzato [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  In GetServiceCommand.cs, rimuovere il corpo del metodo MenuItemCommand e aggiungere il codice seguente:  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Questo codice recupera un servizio SVsActivityLog e ne esegue il cast a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>interfaccia, che consente di scrivere nel registro attività.</xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Per un esempio, vedere [procedura: utilizzare il registro attività](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
5.  Dal menu Strumenti dell'istanza sperimentale, trovare il **GetServiceCommand richiamare** pulsante. Quando si fa clic su questo pulsante, viene visualizzata una finestra di messaggio che indica che **trovare il servizio registro attività.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Recupero di un servizio da un contenitore di controllo o finestra dello strumento  
 In alcuni casi potrebbe essere necessario ottenere un servizio da una finestra degli strumenti o controllo contenitore che non è stato individuato in caso contrario, è stato individuato con un provider di servizi che non conosce il servizio desiderato. Ad esempio, è possibile scrivere per la registrazione delle attività all'interno di un controllo.  
  
 Il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>metodo si basa su un provider di servizi memorizzati nella cache che viene inizializzato la prima volta un VSPackage derivato da <xref:Microsoft.VisualStudio.Shell.Package>viene individuato.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Poiché viene chiamato il costruttore di VSPackage prima VSPackage viene individuato, sono in genere non sono disponibili all'interno del costruttore VSPackage servizi globali. Vedere [procedura: risolvere i servizi](../extensibility/how-to-troubleshoot-services.md) per una soluzione alternativa.  
  
 Di seguito è riportato un esempio del modo in cui per ottenere un servizio in una finestra degli strumenti o un altro elemento non VSPackage.  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Recupero di un servizio dall'oggetto DTE  
 È inoltre possibile ottenere servizi da <xref:EnvDTE.DTEClass>oggetto.</xref:EnvDTE.DTEClass> Tuttavia, è necessario ottenere l'oggetto DTE come un servizio da un VSPackage o chiamando il metodo statico <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>  
  
 Implementa l'oggetto DTE <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, che è possibile utilizzare per eseguire query per un servizio utilizzando <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.</xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
 Di seguito viene illustrato come ottenere un servizio dall'oggetto DTE.  
  
```c#  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md)   
 [Utilizzo e servizi](../extensibility/using-and-providing-services.md)   
 [Funzionalità fondamentali del servizio](../extensibility/internals/service-essentials.md)
