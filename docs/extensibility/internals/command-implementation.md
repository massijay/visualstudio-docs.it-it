---
title: Implementazione di comando | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 24
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
ms.openlocfilehash: bd3c23baffe767083bc541fa9e2e8718834b3ee1
ms.lasthandoff: 02/22/2017

---
# <a name="command-implementation"></a>Implementazione di comando
Per implementare un comando in un VSPackage, è necessario eseguire le attività seguenti:  
  
1.  Nel file vsct, configurare un gruppo di comandi e quindi aggiungere il comando. Per ulteriori informazioni, vedere [tabella di comando Visual Studio (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Registrare il comando con Visual Studio.  
  
3.  Implementare il comando.  
  
 Nelle sezioni seguenti viene illustrato come registrare e implementare i comandi.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrazione dei comandi con Visual Studio  
 Se il comando viene visualizzato un menu, è necessario aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>alla VSPackage e usare come valore il nome del menu o la relativa risorsa ID.</xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Inoltre, è necessario registrare il comando con <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>.</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> È possibile ottenere questo servizio utilizzando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>metodo se il pacchetto Visual Studio è derivato da <xref:Microsoft.VisualStudio.Shell.Package>.</xref:Microsoft.VisualStudio.Shell.Package> </xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementazione di comandi  
 Esistono diversi modi per implementare i comandi. Se si desidera che un comando di menu statico, che è un comando che è sempre lo stesso modo e nello stesso menu, creare il comando utilizzando <xref:System.ComponentModel.Design.MenuCommand>come illustrato negli esempi nella sezione precedente.</xref:System.ComponentModel.Design.MenuCommand> Per creare un comando statico, è necessario fornire un gestore eventi che è responsabile per l'esecuzione del comando. Poiché il comando è sempre attivo e visibile, non è necessario fornire il relativo stato di Visual Studio. Se si desidera modificare lo stato di un comando in base a determinate condizioni, è possibile creare il comando come un'istanza di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>classe e, nel relativo costruttore, fornire un gestore eventi per eseguire il comando e un gestore di query sullo stato per notificare a Visual Studio quando viene modificato lo stato del comando.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand> È anche possibile implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>come parte di una classe di comando o, è possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Se si specifica un comando come parte di un progetto.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Le due interfacce e <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>tutti classe dispone di metodi per notificare una modifica nello stato di un comando di Visual Studio e altri metodi che forniscono l'esecuzione del comando.</xref:Microsoft.VisualStudio.Shell.OleMenuCommand>  
  
 Quando un comando viene aggiunto al servizio di comando, diventa uno di una serie di comandi. Quando si implementano i metodi di notifica e l'esecuzione di stato per il comando, prestare attenzione per fornire solo per quel comando specifico e per passare tutti gli altri casi per altri comandi della catena. Se non è possibile passare il comando (in genere restituendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio potrebbero smettere di funzionare correttamente.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
## <a name="query-status-methods"></a>Metodi di query dello stato  
 Se si implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>metodo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A>(metodo), cercare il GUID del comando set a cui appartiene il comando e l'ID del comando.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Attenersi alle seguenti indicazioni:  
  
-   Se il GUID non viene riconosciuto, l'implementazione di uno di questi metodi deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Se l'implementazione dei metodi riconosce il GUID, ma non ha implementato effettivamente il comando, il metodo deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
-   Se l'implementazione dei metodi riconosce sia il GUID e il comando, quindi il metodo deve impostare il campo flag di comando di ogni comando (nel `prgCmds` parametro) tramite i flag seguenti:  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se il comando è supportato.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se il comando non deve essere visibile.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se il comando viene attivato e viene visualizzato con stato archiviato.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se il comando è abilitato.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se il comando deve essere nascosto se viene visualizzato un menu di scelta rapida.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>Se il comando è un controller di menu e non è abilitato, ma l'elenco di riepilogo non è vuoto ed è ancora disponibile.</xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> (Questo flag viene raramente utilizzato).  
  
-   Se il comando è stato definito nel file vsct con il `TextChanges` flag, impostare i parametri seguenti:  
  
    -   Impostare il `rgwz` elemento il `pCmdText` parametro per il nuovo testo del comando.  
  
    -   Impostare il `cwActual` elemento il `pCmdText` parametro per le dimensioni della stringa di comando.  
  
 Assicurarsi che il contesto corrente non è una funzione di automazione, a meno che il comando è progettato per gestire le funzioni di automazione.  
  
 Per indicare che si supporta un comando specifico, restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Per tutti gli altri comandi, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 Nell'esempio seguente, il metodo query-status prima assicura che il contesto non è una funzione di automazione, quindi consente di trovare il GUID di set di comandi corretto e l'ID di comando. Il comando è impostato per essere attivato e supportato. Nessun altro comando è supportato.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Metodi di esecuzione  
 Implementazione del metodo di esecuzione è simile a implementazione del metodo query-status. In primo luogo, assicurarsi che il contesto non è una funzione di automazione. Testare quindi per il GUID e ID di comando. Se il GUID o ID non viene riconosciuto, comando restituito <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.</xref:Microsoft.VisualStudio.OLE.Interop.Constants>  
  
 Per gestire il comando, eseguirlo e restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>Se l'esecuzione ha esito positivo.</xref:Microsoft.VisualStudio.VSConstants.S_OK> Il comando è responsabile per il rilevamento errori e la notifica. Pertanto, restituire un codice di errore se l'esecuzione ha esito negativo. Nell'esempio seguente viene illustrato come deve essere implementato il metodo di esecuzione.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
