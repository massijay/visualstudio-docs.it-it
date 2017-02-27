---
title: "Accesso a theText visualizzazione tramite l&#39;API Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - visualizzazione di testo"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Accesso a theText visualizzazione tramite l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Una visualizzazione di testo è una presentazione del testo archiviato in un buffer di testo.  È possibile accedere alla visualizzazione di testo utilizzando le API legacy come illustrato nella sezione seguente.  
  
## Oggetto della visualizzazione di testo  
 Ogni visualizzazione viene associata al relativo buffer di testo e la visualizzazione è una finestra ai dati nel buffer.  Nel diagramma seguente sono illustrate le interfacce principali dell'oggetto della visualizzazione di testo, rappresentato da <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.  
  
 ![Oggetto TextView di Visual Studio](../extensibility/media/vstextview.png "vstextview")  
Oggetto della visualizzazione di testo  
  
 La visualizzazione è una modalità di presentazione del testo nel buffer.  Include funzionalità quali il ritorno a capo automatico e descrizione, in modo che gli elementi visualizzati nella visualizzazione non costituisce un'esatta rappresentazione del testo nel buffer.  
  
 Una visualizzazione consente agli altri servizi o processi per intercettare i controlli in ingresso e l'atto loro prima della visualizzazione avvenga su di essi.  La maggior parte del servizio comune per eseguire questa operazione è un servizio di linguaggio.  Un servizio di linguaggio potrebbe essere necessario, ad esempio, rilevare il comando affinché il tasto INVIO fornisce il comportamento personalizzato o le descrizioni comandi di rientro.  
  
## Aggiunta di funzionalità alla visualizzazione di testo  
 È possibile personalizzare il comportamento della visualizzazione di testo mediante la gestione delle sequenze di tasti specifiche.  Per intercettare le sequenze di tasti, distribuire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> sull'oggetto e fornire una destinazione comando \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) per monitorare e rilevare i controlli.  
  
 La visualizzazione di testo utilizza l'architettura sequenziale per i filtri di comando.  I nuovi filtri di comando \(oggetti di<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> \) vengono aggiunti alla sequenza chiamando il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  
  
 La notifica degli eventi per la visualizzazione di testo viene fornita tramite l'interfaccia di `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` .  Implementare questa interfaccia sull'oggetto client alla notifica di ricezione delle modifiche alla visualizzazione di testo.  Esporre questa interfaccia alla visualizzazione di testo tramite l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> nella visualizzazione di testo per ricevere la notifica delle modifiche dalla visualizzazione.  
  
## Vedere anche  
 [Modifica delle impostazioni di visualizzazione tramite l'API Legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Mediante la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)