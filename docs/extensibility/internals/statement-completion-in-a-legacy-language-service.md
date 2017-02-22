---
title: "Completamento delle istruzioni in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "completamento delle istruzioni"
  - "servizi di linguaggio, il completamento delle istruzioni"
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Completamento delle istruzioni in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Completamento delle istruzioni è il processo mediante il quale il servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o un elemento che siano avviati la digitazione nell'editor di componenti di base. In questo argomento viene descritto il funzionamento di completamento delle istruzioni e per l'implementazione del servizio di linguaggio.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare il completamento delle istruzioni, vedere [Procedura dettagliata: Visualizzazione di completamento delle istruzioni](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Implementazione di completamento delle istruzioni  
 Nell'editor di componenti di base, il completamento delle istruzioni attiva una speciale interfaccia utente in modo interattivo consente più facilmente e rapidamente scriverà codice. Completamento delle istruzioni facilita da Visualizzazione classi o oggetti pertinenti quando sono necessarie, che consente di evitare di dover ricordare elementi specifici o dover cercare un argomento di riferimento della Guida.  
  
 Per implementare il completamento delle istruzioni, la lingua deve avere un trigger di completamento istruzione, che può essere analizzato. Ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilizza un punto \(.\) operatore, mentre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] utilizza una freccia \(\-\>\) \(operatore\). Un servizio di linguaggio possa utilizzare più di un trigger per avviare il completamento delle istruzioni. Questi trigger vengono programmati nel filtro del comando.  
  
## Filtri dei comandi e trigger  
 Comandi filtri intercettano le occorrenze del trigger o del trigger. Per aggiungere il filtro dei comandi per la visualizzazione, implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e collegarlo alla visualizzazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo. È possibile utilizzare lo stesso filtro di comando \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) per tutti gli aspetti del servizio di linguaggio, ad esempio il completamento delle istruzioni, i marcatori di errore e suggerimenti \(metodo\). Per altre informazioni, vedere [Intercettazione di comandi del servizio di linguaggio Legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Quando viene immesso il trigger nell'editor, in particolare, il buffer di testo, quindi chiama il servizio di linguaggio di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> \(metodo\). In questo modo l'editor visualizzare l'interfaccia utente in modo che l'utente può scegliere tra i candidati di completamento istruzione. Questo metodo richiede di implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> e <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flag come parametri. Verrà visualizzato l'elenco di elementi di completamento in una casella di scorrimento. L'utente continua a digitare, la selezione nella casella di riepilogo viene aggiornata per riflettere che la corrispondenza più vicina per i caratteri più recente tipizzato. L'editor di componenti di base implementa l'interfaccia utente per il completamento delle istruzioni, ma il servizio di linguaggio deve implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia per definire un set di elementi di completamento candidate per l'istruzione.  
  
## Vedere anche  
 [Intercettazione di comandi del servizio di linguaggio Legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)