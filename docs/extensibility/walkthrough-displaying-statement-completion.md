---
title: "Procedura dettagliata: Visualizzazione di completamento delle istruzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], nuovo - completamento istruzioni"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Procedura dettagliata: Visualizzazione di completamento delle istruzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile implementare il completamento delle istruzioni basate sul linguaggio definendo gli identificatori per il quale si desidera fornire completamento e quindi attivare una sessione di completamento. È possibile definire il completamento delle istruzioni nel contesto di un servizio di linguaggio, definire il proprio estensione di file e il tipo di contenuto e quindi visualizzare il completamento di tale tipo, o è possibile attivare il completamento di un tipo di contenuto esistente, ad esempio, "normale". Questa procedura dettagliata viene illustrato come attivare completamento delle istruzioni per il tipo di contenuto "normale", ovvero il tipo di contenuto dei file di testo. Il tipo di contenuto "text" è il predecessore di tutti gli altri tipi di contenuto, inclusi file XML e codice.  
  
 Completamento delle istruzioni viene in genere attivato digitando alcuni caratteri, ad esempio, digitando l'inizio di un identificatore, ad esempio "using". Viene in genere chiuso premendo il tasto barra spaziatrice, Tab o INVIO per eseguire il commit di una selezione. È possibile implementare le funzionalità di IntelliSense che vengono attivate digitando un carattere utilizzando un gestore comando per le sequenze di tasti \(il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface\) e un gestore provider che implementa il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine di completamento, in cui è riportato l'elenco di identificatori che fanno parte di completamento, implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> interfaccia e un provider di codice sorgente di completamento \(il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> interface\). I provider sono componenti Managed Extensibility Framework \(MEF\). Sono responsabili per le classi di origine e il controller di esportazione e importazione di servizi e Broker, ad esempio, il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente lo spostamento nel buffer di testo e <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, che attiva la sessione di completamento.  
  
 Questa procedura dettagliata viene illustrato come implementare il completamento per un set di identificatori a livello di codice. In implementazioni complete, il servizio di linguaggio e la documentazione del linguaggio sono responsabili per fornire tale contenuto.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un progetto MEF  
  
#### Per creare un progetto MEF  
  
1.  Creare un progetto VSIX in c\#. \(Nel **Nuovo progetto** finestra di dialogo, selezionare **Visual c\# \/ Extensibility**, quindi **progetto VSIX**.\) Denominare la soluzione `CompletionTest`.  
  
2.  Aggiungere un modello di elemento Editor classificatore al progetto. Per altre informazioni, vedere [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** è impostato su `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Implementazione dell'origine di completamento  
 L'origine di completamento è responsabile per la raccolta di set di identificatori e aggiungere il contenuto nella finestra di completamento quando un utente digita un trigger di completamento, ad esempio le prime lettere di un identificatore. In questo esempio, gli identificatori e le relative descrizioni sono hardcoded nel <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo. Nella maggior parte dei casi reali, si utilizzerà il parser del linguaggio per ottenere i token per popolare l'elenco di completamento.  
  
#### Per implementare l'origine di completamento  
  
1.  Aggiungere un file di classe e denominarla `TestCompletionSource`.  
  
2.  Aggiungere queste importazioni:  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Modificare la dichiarazione di classe per `TestCompletionSource` in modo che implementi <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Aggiungere campi privati per il provider di origine, il buffer di testo e un elenco di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> oggetti \(che corrispondono agli identificatori che farà parte della sessione di completamento\):  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Aggiungere un costruttore che imposta il buffer e il provider di origine. La `TestCompletionSourceProvider` classe è definita nei passaggi successivi:  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> metodo mediante l'aggiunta di un set di completamento che contiene i completamenti che si desidera fornire nel contesto. Ogni set di completamento contiene un set di <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> completamenti e corrisponde a una scheda della finestra di completamento. \(Nei progetti di Visual Basic, le schede della finestra completamento sono denominate **comuni** e **tutti**.\) Il metodo FindTokenSpanAtPosition viene definito nel passaggio successivo.  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Per cercare la parola corrente dalla posizione del cursore viene utilizzato il metodo seguente:  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Implementare il `Dispose()` metodo:  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## Implementazione del Provider di origine di completamento  
 Il provider di origine di completamento è la parte del componente MEF che crea un'istanza dell'origine di completamento.  
  
#### Per implementare il provider di origine di completamento  
  
1.  Aggiungere una classe denominata `TestCompletionSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Esportazione di questa classe con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di testo "normale" e un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "completamento del test".  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Importa un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente di trovare la parola corrente nell'origine completamento.  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> metodo per creare un'istanza dell'origine di completamento.  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## Implementazione del Provider di gestore comandi di completamento  
 Il provider di gestore comandi di completamento viene derivato da un <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, che resta in attesa di un evento di creazione di visualizzazione di testo e converte la visualizzazione di un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>che consente l'aggiunta del comando per la catena di comando della shell di Visual Studio, per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Poiché questa classe è un'esportazione MEF, è anche possibile utilizzarlo per importare i servizi necessari per il gestore del comando stesso.  
  
#### Per implementare il provider di gestore comandi di completamento  
  
1.  Aggiungere un file denominato `TestCompletionCommandHandler`.  
  
2.  Aggiungi queste istruzioni using:  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Aggiungere una classe denominata `TestCompletionHandlerProvider` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Esportazione di questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "gestore completamento token", un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di testo "normale" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> di <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Importazione di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, che consente la conversione da un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>,  <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, e un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> che consente l'accesso ai servizi di Visual Studio standard.  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo per creare un'istanza di gestore del comando.  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## Implementazione del gestore di comandi di completamento  
 Poiché il completamento delle istruzioni viene attivato da sequenze di tasti, è necessario implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per ricevere ed elaborare le sequenze di tasti che è attivata, eseguire il commit e chiudere la sessione di completamento.  
  
#### Per implementare il gestore di comandi di completamento  
  
1.  Aggiungere una classe denominata `TestCompletionCommandHandler` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Aggiungere campi privati per il gestore del comando successivo \(a cui si passa il comando\), la visualizzazione di testo, il provider di gestore comando \(che consente di accedere a vari servizi\) e una sessione di completamento:  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Aggiungere un costruttore che imposta la visualizzazione di testo e i campi del provider e aggiunge il comando alla catena di comando:  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo passando il comando lungo:  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Implementare il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Quando questo metodo riceve una sequenza di tasti, è necessario eseguire una di queste due operazioni:  
  
    -   Consentire il carattere di essere scritti nel buffer e quindi attivare o filtrare il completamento. \(I caratteri stampabili tale scopo\).  
  
    -   Eseguire il commit del completamento, ma non consentono il carattere da scrivere nel buffer. \(Gli spazi vuoti, Tab ed Enter farlo durante la visualizzazione di una sessione di completamento.\)  
  
    -   Consente il comando passato al gestore successivo. \(Tutti gli altri comandi.\)  
  
     Poiché questo metodo può visualizzare l'interfaccia utente, chiamare il metodo <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> per assicurarsi che non viene chiamato in un contesto di automazione:  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Questo codice è un metodo privato che attiva la sessione di completamento:  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  Nell'esempio seguente è un metodo privato che annulla la sottoscrizione dal <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> evento:  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione CompletionTest ed eseguirlo nell'istanza sperimentale.  
  
#### Per compilare e testare la soluzione CompletionTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include la parola "Aggiungi".  
  
4.  Mentre si digita prima "a" e quindi "d", verrà visualizzato un elenco che contiene "addition" e "adattamento". Si noti che inoltre sia selezionata. Quando si digita un altro "d", l'elenco dovrebbe contenere solo "aggiunta," che viene selezionato. È possibile eseguire il commit "aggiunta" premendo il tasto barra spaziatrice, Tab o invio o chiudere l'elenco digitando Esc o qualsiasi altra chiave.  
  
## Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)