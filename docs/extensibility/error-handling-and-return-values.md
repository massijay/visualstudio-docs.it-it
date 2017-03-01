---
title: Gestione degli errori e i valori restituiti | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
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
ms.openlocfilehash: c30c795363738b5715bc6d5c928ba8553d01210b
ms.lasthandoff: 02/22/2017

---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e i valori restituiti
Package VS e COM utilizzano la stessa architettura per gli errori. Il `SetErrorInfo` e `GetErrorInfo` funzioni fanno parte delle Win32 application programming interface (API). Qualsiasi VSPackage nell'ambiente di sviluppo integrato (IDE) può chiamare questi globale API Win32 per registrare le informazioni di errore avanzata quando si riceve una notifica di errore. Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce gli assembly di interoperabilità per gestire le informazioni di errore.  
  
## <a name="interop-methods"></a>Metodi di interoperabilità  
 Per comodità, l'IDE fornisce un metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, utilizzare invece di chiamare le API Win32.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Nel codice gestito, utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Quando un errore `HRESULT` arriva al livello in cui deve essere visualizzato il messaggio di errore (spesso corrisponde all'oggetto che implementa un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>gestore del comando), l'IDE utilizza un altro metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, per visualizzare la finestra di messaggio appropriato.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Nel codice gestito, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
 Come responsabile dell'implementazione package VS, gli oggetti COM implementare normalmente `ISupportErrorInfo`. Il `ISupportErrorInfo` interfaccia assicura che informazioni dettagliate sull'errore possibile spostarsi in senso verticale fino alla catena di chiamata. Gli oggetti che possono essere utilizzati tra processi o tra thread devono supportare `ISupportErrorInfo` per garantire che le informazioni dettagliate sull'errore correttamente eseguito il marshalling al chiamante.  
  
 Tutti gli oggetti che sono correlati a VSPackage e che sono interessati a estendere l'IDE, tra cui factory editor, Editor, gerarchie e offerte di servizi, devono supportare informazioni dettagliate sull'errore. Mentre l'IDE non richiede tali oggetti VSPackage implementare `ISupportErrorInfo`, è sempre consigliabile.  
  
 L'IDE è responsabile della segnalazione di informazioni sull'errore e di visualizzarli all'utente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ogni volta che un `HRESULT` viene propagato all'IDE. L'IDE è anche il meccanismo per la creazione di `ErrorInfo` oggetti.  
  
## <a name="general-guidelines"></a>Indicazioni generali  
 È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>metodi per impostare e segnalare gli errori interni all'implementazione di VSPackage nonché.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Tuttavia, come regola generale, seguire queste linee guida per la gestione dei messaggi di errore il pacchetto Visual Studio:  
  
-   Implementare `ISupportErrorInfo` negli oggetti COM VSPackage.  
  
-   Creare un meccanismo che chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>metodo negli oggetti che implementano <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> di segnalazione  
  
-   Consente di visualizzare gli errori agli utenti tramite l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>  
  
## <a name="error-information-in-the-ide"></a>Informazioni sull'errore nell'IDE  
 Le regole seguenti indicano come gestire le informazioni di errore nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Come una strategia di difesa per garantire che informazioni di errore non aggiornati non viene segnalato agli utenti, le funzioni che chiamano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>metodo deve chiamare prima il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> Passare `null` per cancellare i messaggi di errore memorizzato nella cache chiamando qualsiasi cosa che potrebbe impostare nuove informazioni sull'errore.  
  
-   Funzioni che non comunicano direttamente i messaggi di errore sono consentite solo per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>metodo restituiscano un errore `HRESULT`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> È possibile cancellare il `ErrorInfo` sulla voce di una funzione o la restituzione <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> L'unica eccezione a questa regola è quando una chiamata restituisce un errore `HRESULT` da cui possa ripristinare in modo esplicito o ignorare la parte ricevente.  
  
-   Tutte le parti che vengono ignorati in modo esplicito un errore `HRESULT` deve chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>metodo con <xref:Microsoft.VisualStudio.VSConstants.S_OK>.</xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> In caso contrario, il `ErrorInfo` oggetto può essere usato quando un'altra entità viene generato un errore senza fornire le proprie accidentalmente `ErrorInfo`.  
  
-   Tutti i metodi che hanno origine errore `HRESULT` si consiglia di chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>metodo per fornire informazioni dettagliate sull'errore.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Se l'oggetto restituito `HRESULT` è una speciale `FACILITY_ITF` errore, quindi il metodo è necessario fornire un corretto `ErrorInfo`oggetto. Se l'errore restituito è un errore di sistema standard (ad esempio, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>e così via) è accettabile per restituire il codice di errore senza chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> </xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> </xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> </xref:Microsoft.VisualStudio.VSConstants.E_ABORT> </xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> Come una strategia di codifica difensiva, quando un errore di origine `HRESULT` (compresi gli errori di sistema), chiamare sempre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>(metodo), con `ErrorInfo` che descrive l'errore in modo più dettagliato, o `null`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>  
  
-   Tutte le funzioni che restituiscono un errore viene generato da un'altra chiamata necessario passare le informazioni che è stato ricevuto da errori di chiamano `HRESULT` senza modificare il `ErrorInfo` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget></xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (componente automazione)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interfaccia ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)
