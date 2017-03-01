---
title: Oggetto VSTextView | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 8
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
ms.openlocfilehash: fd11409382b2db5e5cbea8c0dad25dbdb3b6cb99
ms.lasthandoff: 02/22/2017

---
# <a name="vstextview-object"></a>Oggetto VSTextView
Visualizzazione di testo è una finestra che consente agli utenti di visualizzare e modificare il testo Unicode del buffer di testo. Essenzialmente, la visualizzazione è fare riferimento alla maggior parte degli utenti come l'editor. Poiché la vista è separata dal buffer da vari livelli di testo (ritorno a capo automatico, il testo della struttura e così via), la vista non deve necessariamente essere una rappresentazione esatta del testo nel buffer. Per ulteriori informazioni sulla visualizzazione di testo, vedere [accesso theText vista utilizzando l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Nella tabella seguente mostra le interfacce di <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>oggetto.</xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget></xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite></xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interfaccia OLE standard.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte (vale a dire le azioni che vengono raggruppate in un'unità di annullamento/ripristino singolo).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornisce i metodi di base per la gestione e la visualizzazione di accesso. `IVsTextView`non è thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Crea e gestisce un riquadro della finestra.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagisce con i livelli di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView></xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Esegue operazioni per la vista da un thread diverso.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica di figure](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Oggetto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Accesso a theText visualizzazione tramite l'API Legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
