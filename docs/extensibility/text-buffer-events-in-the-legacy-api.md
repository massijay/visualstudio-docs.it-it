---
title: Gli eventi nel Buffer di testo nell&quot;API Legacy | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
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
ms.openlocfilehash: 39ac6a711278950d09ed16b157fc89980144e3d0
ms.lasthandoff: 02/22/2017

---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventi nel Buffer di testo nell'API Legacy
L'oggetto TextBuffer genera numerosi eventi diversi che consentono di rispondere a situazioni diverse.  
  
 Quando si utilizza l'API legacy, è necessario implementare le interfacce seguenti per ricevere la notifica delle modifiche al buffer di testo. Espone le interfacce per il buffer di testo tramite il `IConnectionPointContainer` interfaccia nel buffer di testo per ricevere una notifica di riga viene modificata dal buffer. Per ulteriori informazioni, vedere [procedura: registrare gli eventi del Buffer di testo con l'API Legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Nel caso di `IVsTextStreamEvents` o `IVsTextLinesEvents` interfacce, le modifiche vengono restituite in un'unidimensionale o bidimensionale coordinate, rispettivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfacce di Buffer di testo  
 Di seguito sono le interfacce implementate dall'oggetto buffer di testo.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction></xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte (vale a dire azioni che vengono raggruppate in un'unità di annullamento/ripristino singolo).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Consente la persistenza dei dati del documento gestiti da buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti clienti.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Consente di lettura e scrittura funzionalità usando le coordinate bidimensionale. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Offre un accesso sequenza, orientato al flusso di testo nel buffer rapido.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Consente di lettura e scrittura funzionalità usando le coordinate unidimensionale. Eredita da `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome o moniker, del buffer. È possibile archiviare dati casuali nel buffer con questa interfaccia mediante la creazione di un GUID e l'uso come chiave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer></xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta punti di connessione per gli eventi.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfacce di eventi del Buffer di testo  
 Di seguito sono le interfacce per la notifica di evento del buffer di testo.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica ai client quando un nuovo servizio di linguaggio è associato a un buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica ai client quando viene inizializzato un buffer di testo e quando vengono apportate modifiche ai dati nel buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica ai client le modifiche apportate al buffer di testo sottostante in base alle coordinate unidimensionale.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica ai client le modifiche apportate al buffer di testo sottostante in base alle coordinate bidimensionale.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica ai client delle modifiche apportate ai dati utente.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica ai client del movimento ultimo commit per attivare l'evento e fornisce l'intervallo di testo modificato. Il `IVsPreliminaryTextChangeCommitEvents` interfaccia non viene generato in risposta a annullare o ripristinare i comandi. Eventi vengono generati solo per i buffer che dispongono di un gestore di annullamento. `IVsPreliminaryTextChangeCommitEvents`viene generato prima di altri eventi, ad esempio di elenco, per assicurarsi che gli altri eventi non modificano il testo prima che le modifiche vengono salvate. Il pacchetto Visual Studio deve monitorare uno di `IVsPreliminaryTextChangeCommitEvents` interfaccia o `IVsFinalTextChangeCommitEvents` interfaccia, ma non entrambi.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents></xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica ai client del movimento ultimo commit per attivare l'evento e fornisce l'intervallo di testo modificato. Il `IVsFinalTextChangeCommitEvents` interfaccia non viene generato in risposta a annullare o ripristinare i comandi. Eventi vengono generati solo per i buffer che dispongono di un gestore di annullamento. `IVsFinalTextChangeCommitEvents`deve essere utilizzato solo da servizi di linguaggio o altri oggetti che dispongono del controllo completo sulla modifica. Il pacchetto Visual Studio deve monitorare uno di `IVsPreliminaryTextChangeCommitEvents` interfaccia o `IVsFinalTextChangeCommitEvents` interfaccia, ma non entrambi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai Buffer di testo tramite l'API Legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Procedura: registrare gli eventi del Buffer di testo con l'API Legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
