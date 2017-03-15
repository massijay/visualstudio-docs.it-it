---
title: "Creazione di finestre di progettazione ed editor personalizzati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "finestre di progettazione [Visual Studio SDK]"
  - "editor [Visual Studio SDK], personalizzato"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# Creazione di finestre di progettazione ed editor personalizzati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ambiente di sviluppo integrato \(IDE\) di Visual Studio può ospitare diversi tipi di editor:  
  
-   Editor di componenti di base di Visual Studio  
  
-   Editor personalizzati  
  
-   Editor esterni  
  
-   Finestre di progettazione  
  
 Le informazioni seguenti consentono di scegliere il tipo di editor, che è necessario.  
  
## Tipi di Editor  
 Per informazioni sull'editor di componenti di base di Visual Studio, vedere [Estensione dell'Editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).  
  
##### Editor personalizzati  
 Un editor personalizzato è quello che è progettato per funzionare in circostanze speciali. Ad esempio, è possibile creare un editor la cui funzione consiste nel leggere e scrivere dati in un repository specifico, ad esempio un server di Microsoft Exchange. Scegliere un editor personalizzato se si desidera un editor che funziona con solo il tipo di progetto o se si desidera un editor che presenta solo alcuni comandi specifici. Si noti tuttavia che gli utenti non saranno in grado di utilizzare un editor personalizzato per modificare standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti.  
  
 Un editor personalizzato è possibile utilizzare una factory editor e aggiungere informazioni sull'editor del Registro di sistema. Tuttavia, il tipo di progetto associato all'editor personalizzato può creare un'istanza all'editor personalizzato in altri modi.  
  
 Un editor personalizzato è possibile utilizzare l'attivazione sul posto o incorporamento semplificato per implementare una vista.  
  
##### Editor esterni  
 Editor esterni sono editor che non sono integrati in Visual Studio, ad esempio Microsoft Word, il blocco note o Microsoft FrontPage. Se, ad esempio, si passa il testo ad esso dal pacchetto Visual Studio, è possibile chiamare un editor di questo tipo. Editor esterni effettuano la registrazione e può essere utilizzato all'esterno di Visual Studio. Quando si chiama un editor esterno, che possono essere incorporato in una finestra host, viene visualizzato in una finestra nell'IDE. In caso contrario, verrà creata una finestra separata per esso.  
  
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo imposta la priorità di documento utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione. Se il `DP_External` viene specificato, il file può essere aperto da un editor esterno.  
  
## Decisioni di progettazione dell'editor  
 Le domande di progettazione seguenti consentono di scegliere il tipo di editor migliore adatto alla propria applicazione:  
  
-   L'applicazione salverà i dati nei file o non? Se i dati verrà salvato nel file, saranno in un formato standard o personalizzato?  
  
     Se si utilizza un formato di file standard, altri tipi di progetto oltre il progetto sarà in grado di aprire e leggere e scrivere dati a essi. Se si utilizza un formato di file personalizzati, tuttavia, solo il tipo di progetto sarà in grado di aprire e leggere e scrivere dati a essi.  
  
     Se il progetto utilizza i file, è necessario personalizzare l'editor standard. Se il progetto non utilizza i file, ma piuttosto utilizza gli elementi in un database o altri repository, è necessario creare un editor personalizzato.  
  
-   L'editor è necessario per ospitare i controlli ActiveX?  
  
     Se l'editor ospita controlli ActiveX, quindi implementare un editor di attivazione sul posto, come descritto [Attivazione sul posto](../misc/in-place-activation.md). Se non ospita controlli ActiveX, quindi utilizzare un editor di incorporamento semplificato oppure personalizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predefinito.  
  
-   L'editor supporterà più viste? Se si desidera che le viste dell'editor sia visibile allo stesso tempo come editor predefinito, è necessario supportare più visualizzazioni.  
  
     Se l'editor deve supportare più visualizzazioni, i dati dei documenti e gli oggetti di visualizzazione documento per l'editor devono essere oggetti separati. Per altre informazioni, vedere [Supporta più viste di documento](../extensibility/supporting-multiple-document-views.md).  
  
     Se l'editor supporta più viste, si intende utilizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementazione del buffer di testo dell'editor di base \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto\) per l'oggetto dati documento? Vale a dire, con cui si desidera supportare l'editor visualizza side\-by\-side con la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale? La possibilità di eseguire questa operazione costituisce la base della finestra di progettazione form.  
  
-   Se è necessario ospitare un editor esterno, l'editor incorporabili all'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?  
  
     Se può essere incorporato, è necessario creare una finestra host per l'editor esterno e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valore di enumerazione `DP_External`. Se l'editor non può essere incorporato, l'IDE crea automaticamente una finestra separata per esso.  
  
## Contenuto della sezione  
 [Procedura dettagliata: Creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md)  
 Viene illustrato come creare un editor personalizzato.  
  
 [Procedura dettagliata: Aggiunta di funzionalità in un Editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 Viene illustrato come aggiungere funzionalità a un editor personalizzato.  
  
 [Inizializzazione della finestra di progettazione e configurazione dei metadati](../extensibility/designer-initialization-and-metadata-configuration.md)  
 Viene illustrato come inizializzare una finestra di progettazione.  
  
 [Fornisce il supporto di annullamento a finestre di progettazione](../extensibility/supplying-undo-support-to-designers.md)  
 Viene spiegato come fornire supporto per l'annullamento delle finestre di progettazione.  
  
 [Colorazione in editor personalizzati della sintassi](../extensibility/syntax-coloring-in-custom-editors.md)  
 Viene illustrata la differenza tra la colorazione nell'editor di componenti di base e negli editor personalizzati della sintassi.  
  
 [Dati del documento e visualizzazione di documento nell'editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 Viene illustrato come implementare i dati del documento e visualizzazione dei documenti in un editor personalizzato.  
  
## Sezioni correlate  
 [Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)  
 Viene illustrato come accedere all'editor di componenti di base tramite l'API legacy.  
  
 [Lo sviluppo di un servizio di linguaggio](../extensibility/internals/developing-a-legacy-language-service.md)  
 Viene illustrato come implementare un servizio di linguaggio.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come creare elementi dell'interfaccia utente che corrispondano al resto del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>