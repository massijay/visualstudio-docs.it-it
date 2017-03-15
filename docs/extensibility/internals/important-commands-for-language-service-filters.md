---
title: I filtri di servizio importanti comandi per la lingua | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6b5bad11c47074c29f3b319678419f1e42ab91b
ms.lasthandoff: 02/22/2017

---
# <a name="important-commands-for-language-service-filters"></a>Comandi importanti per i filtri di servizio di linguaggio
Se si desidera creare un filtro per il linguaggio completo, considerare i seguenti comandi di gestione. L'elenco completo degli identificatori di comando viene definito nel <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>enumerazione per codice gestito e l'intestazione Stdidcmd.h file per non gestito [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] codice.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> È possibile trovare il file Stdidcmd.h *il percorso di installazione di Visual Studio SDK*\visualstudiointegration\common\inc..  
  
## <a name="commands-to-handle"></a>Comandi da gestire  
  
> [!NOTE]
>  Non è obbligatorio per filtrare per ogni comando nella tabella seguente.  
  
|Comando|Descrizione|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente fa clic. Questo comando indica che è possibile fornire un menu di scelta rapida. Se non si gestisce questo comando, l'editor di testo fornisce un menu di scelta rapida predefinito senza i comandi specifici del linguaggio. Per includere i comandi del menu, gestire il comando e visualizzare un menu di scelta rapida manualmente.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente digita CTRL + J. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>per visualizzare la finestra di completamento istruzione.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita un carattere. Monitorare questo comando per determinare quando viene digitato un carattere di trigger e per fornire istruzione completamento, metodo suggerimenti e i marcatori di testo, ad esempio la colorazione della sintassi, corrispondenza tra parentesi graffe e marcatori di errore. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>per il completamento delle istruzioni e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>per suggerimenti (metodo).</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Per supportare i marcatori di testo, monitorare questo comando per determinare se il carattere digitato è necessario aggiornare gli indicatori.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto INVIO. Monitorare questo comando per determinare il momento chiudere una finestra del suggerimento metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente digita il tasto Backspace. Monitoraggio per determinare quando chiudere una finestra del suggerimento metodo chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Per impostazione predefinita, la visualizzazione di testo gestisce questo comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu o un tasto di scelta rapida. Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>per aggiornare la finestra suggerimento con le informazioni sui parametri.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato quando l'utente viene posizionato su una variabile o posiziona il cursore su una variabile e seleziona **informazioni rapide** da **IntelliSense** nel **modificare** menu. Restituire il tipo della variabile in un suggerimento chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Se il debug è attivo, il suggerimento visualizzerà il valore della variabile.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In genere inviato quando l'utente digita CTRL + BARRA SPAZIATRICE. Questo comando indica al servizio di linguaggio per chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Inviato da un menu, in genere **Commenta selezione** o **rimuovere il commento selezione** da **avanzate** nel **modificare** menu. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica che l'utente desidera impostare come commento il testo selezionato. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica che si desidera rimuovere il testo selezionato.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Questi comandi possono essere implementati solo dal servizio di linguaggio.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio Legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
