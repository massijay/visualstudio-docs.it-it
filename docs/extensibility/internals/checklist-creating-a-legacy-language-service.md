---
title: "Elenco di controllo: Creazione di un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "servizi di linguaggio"
  - "servizi di linguaggio, il codice nativo"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Elenco di controllo: Creazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nell'elenco di controllo vengono riepilogati i passaggi fondamentali che è necessario contenere l'ordine per creare un servizio di linguaggio per l'editor di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Per integrare il servizio di linguaggio in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario creare un analizzatore di espressioni di debug.  Per ulteriori informazioni, vedere [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) in [Estensibilità del Debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Operazioni necessarie per creare un servizio di linguaggio  
  
1.  Implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   Nel package VS, implementare l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> per fornire al servizio di linguaggio.  
  
    -   Per rendere il servizio di linguaggio l'ambiente \(IDE\) di sviluppo integrato nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> .  
  
2.  Implementare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> nella classe principale del servizio di linguaggio.  
  
     L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> è il punto iniziale di interazione fra l'editor principale e il servizio di linguaggio.  
  
### funzionalità facoltative  
 Le seguenti funzionalità sono facoltative e possono essere implementate in qualsiasi ordine.  Queste funzionalità consentono di migliorare la funzionalità del servizio di linguaggio.  
  
-   Colorazione della sintassi  
  
     Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  L'implementazione di questa interfaccia se le informazioni del parser restituiscono informazioni sui colori appropriate.  
  
     il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> restituisce l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  Un'istanza separata del colorizer viene creata per ciascun buffer di testo, pertanto è necessario implementare separatamente l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> .  Per ulteriori informazioni, vedere [In un servizio di linguaggio Legacy colorazione della sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Finestra del codice  
  
     Implementare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per consentire al servizio di linguaggio per ricevere la notifica di quando una nuova finestra del codice viene creata.  
  
     il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> restituisce l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> .  Il servizio di linguaggio quindi possibile aggiungere l'interfaccia utente speciale per la finestra del codice in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>.  Il servizio di linguaggio anche eseguire l'elaborazione speciale, quali l'aggiunta di un filtro di visualizzazione di testo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Filtro di visualizzazione di testo  
  
     Per fornire il completamento di istruzioni in IntelliSense in un servizio di linguaggio, è necessario rilevare alcuni dei controlli della visualizzazione di testo gestirebbe in caso contrario.  Per intercettare tali controlli, completare i passaggi seguenti:  
  
    -   Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per partecipare ai controlli dell'editor della catena di handle e di comando.  
  
    -   Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> e passare nell'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    -   Chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> quando si rimuove dalla visualizzazione in modo da non passare questi controlli più l'utente.  
  
     I controlli che devono essere gestiti dipendono dai servizi forniti da.  Per ulteriori informazioni, vedere [Comandi importanti per i filtri di servizio di linguaggio](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> devono essere implementate nello stesso oggetto dell'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
-   Completamento istruzioni  
  
     Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Supportare il comando di completamento delle istruzioni \(ovvero <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\) e chiamare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , passando l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .  Per ulteriori informazioni, vedere [Completamento delle istruzioni in un servizio di linguaggio Legacy](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   suggerimenti di metodo  
  
     Implementare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> per fornire dati per la finestra dell'hint del metodo.  
  
     Installare il filtro di visualizzazione di testo per gestire i controlli in modo appropriato, in modo che si conosce quando visualizzare una finestra del suggerimento dati di metodo.  Per ulteriori informazioni, vedere [Informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   marcatori di errori  
  
     Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Creare il marcatore di errori\) che implementano l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> e chiama il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> , passando l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> dell'oggetto del marcatore di errori.  
  
     In genere ogni marcatore di errori gestisce un elemento nella finestra elenco attività.  
  
-   Elementi di elenco attività  
  
     Implementare una classe di attività che fornisce l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> .  
  
     L'implementazione di una classe di provider di attività che fornisce l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> e l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> .  
  
     Implementare una classe dell'enumeratore di attività che fornisce l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> .  
  
     Register the task provider with the task list's <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> method.  
  
     Ottenere l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> chiamando il provider di servizi del servizio di linguaggio con il servizio il GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Creare gli oggetti dell'elemento attività e chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> quando sono disponibili nuove o attività aggiornate.  
  
-   elementi attività di commento  
  
     utilizzare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> e l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> per ottenere i token di attività di commento.  
  
     Ottenere un'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> dal servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
     Ottenere l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> dal metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> .  
  
     Implementare l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> per ascoltare le modifiche nell'elenco di token.  
  
-   Struttura  
  
     Esistono diverse opzioni per il supporto della struttura.  Ad esempio, è possibile supportare il comando di **Comprimi alle definizioni** , immettere le aree controllate dall'editor della struttura, o supportare le aree selezionate a client.  Per ulteriori informazioni, vedere [Procedura: fornire il supporto esteso della struttura in un servizio di linguaggio Legacy](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Registrazione del servizio di linguaggio  
  
     per ulteriori informazioni su come registrare un servizio di linguaggio, vedere [Registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md) e [La gestione di VSPackage](../../extensibility/managing-vspackages.md).  
  
-   Guida sensibile al contesto  
  
     Fornire contesto all'editor in uno dei modi seguenti:  
  
    -   Per fornire un contesto per i marcatori di testo implementando l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> .  
  
 Specificare qualsiasi contesto utente implementando l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> .  
  
## Vedere anche  
 [Lo sviluppo di un servizio di linguaggio](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)