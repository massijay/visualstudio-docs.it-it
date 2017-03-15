---
title: 'Procedura: registrare gli eventi del Buffer di testo con l&quot;API Legacy | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 13
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
ms.openlocfilehash: b7da1dc26631294b6e41aa6335f2dca064c2831d
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Procedura: registrare gli eventi del Buffer di testo con l'API Legacy
Se si accede a buffer di testo tramite l'API legacy, è necessario registrarsi per gli eventi nel buffer di testo come illustrato nella procedura seguente.  
  
### <a name="to-advise-text-buffer-events"></a>Avvisare gli eventi nel buffer di testo  
  
1.  Da un puntatore a una delle interfacce in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>, chiamare `QueryInterface` per un puntatore a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> </xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>  
  
2.  Chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>metodo e passare l'ID di interfaccia degli eventi per il quale si desidera registrare.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A>  
  
     Ad esempio, se si desidera registrare per <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>, quindi passare un'interfaccia ID di IID_IVsTextLinesEvents.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>  
  
     Buffer di testo restituisce un puntatore per il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>interfaccia per l'oggetto punto di connessione appropriata.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>  
  
3.  Utilizzare questo puntatore, chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>, passando un puntatore all'implementazione di interfaccia degli eventi per il quale si desidera registrare, ad esempio, il `IVsTextLinesEvents` interfaccia.</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>  
  
     L'ambiente restituisce un cookie che è quindi possibile utilizzare per interrompere l'ascolto di eventi chiamando il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>(metodo).</xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A>  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi nel Buffer di testo nell'API Legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)
