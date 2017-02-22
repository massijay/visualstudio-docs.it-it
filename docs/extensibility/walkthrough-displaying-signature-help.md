---
title: "Procedura dettagliata: Visualizzazione della Guida di firma | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], nuovo - firma Guida/informazioni sul parametro"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Visualizzazione della Guida di firma
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Supporto di firma \(noto anche come *informazioni sul parametro*\) viene visualizzata la firma di un metodo in una descrizione comando quando un utente digita il carattere iniziale di elenco parametro \(in genere una parentesi di apertura\). Come parametro e il separatore di parametri \(in genere una virgola\) sono tipizzate, la descrizione comando viene aggiornata per mostrare il parametro successivo in grassetto. È possibile definire supporto firma nel contesto di un servizio di linguaggio, è possibile definire il tipo di estensione e il contenuto di nome file e visualizzare la Guida di firma per il solo tipo, o è possibile visualizzare la Guida in linea di firma per un tipo di contenuto esistente \(ad esempio, "text"\). Questa procedura dettagliata viene illustrato come visualizzare la Guida di firma per il tipo di contenuto "text".  
  
 Supporto di firma viene in genere attivato digitando un carattere specifico, ad esempio, "\(" \(parentesi di apertura\) e verrà eliminato da un altro carattere, ad esempio, digitando "\)" \(la parentesi di chiusura\). Funzionalità IntelliSense che vengono attivate digitando un carattere possono essere implementate tramite un gestore comando per le sequenze di tasti \(il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface\) e un gestore provider che implementa il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> interfaccia. Per creare l'origine supporto firma, ovvero l'elenco di firme che fanno parte di supporto firma, implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> interfaccia e un provider di origine che implementa il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> interfaccia. I provider sono componenti Managed Extensibility Framework \(MEF\) e sono responsabili per le classi di origine e il controller di esportazione e importazione di servizi e Broker, ad esempio, il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, che consente di passare nel buffer di testo, e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, che attiva la sessione di supporto firma.  
  
 Questa procedura dettagliata viene illustrato come implementare la Guida in linea di firma per un set di identificatori a livello di codice. In implementazioni complete, il linguaggio è responsabile di fornire tale contenuto.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un progetto MEF  
  
#### Per creare un progetto MEF  
  
1.  Creare un progetto VSIX in c\#. \(Nel **Nuovo progetto** finestra di dialogo, selezionare **Visual c\# \/ Extensibility**, quindi **progetto VSIX**.\) Denominare la soluzione `SignatureHelpTest`.  
  
2.  Aggiungere un modello di elemento Editor classificatore al progetto. Per altre informazioni, vedere [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere i riferimenti seguenti al progetto e assicurarsi che **CopyLocal** è impostato su `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Implementazione di firma Guida firme e i parametri  
 L'origine supporto firma si basa sulle firme che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, ognuno dei quali contiene i parametri che implementano <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. In un'implementazione completa, questa informazione ottenuta dalla documentazione, ma in questo esempio, le firme sono hardcoded.  
  
#### Per implementare il supporto firma firme e i parametri  
  
1.  Aggiungere un file di classe e denominarla `SignatureHelpSource`.  
  
2.  Aggiungere le seguenti istruzioni imports.  
  
     [!code-vb[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_1.vb)]
     [!code-cs[VSSDKSignatureHelpTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_1.cs)]  
  
3.  Aggiungere una classe denominata `TestParameter` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_2.vb)]
     [!code-cs[VSSDKSignatureHelpTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_2.cs)]  
  
4.  Aggiungere un costruttore che imposta tutte le proprietà.  
  
     [!code-vb[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_3.vb)]
     [!code-cs[VSSDKSignatureHelpTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_3.cs)]  
  
5.  Aggiungere le proprietà di <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!code-vb[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_4.vb)]
     [!code-cs[VSSDKSignatureHelpTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_4.cs)]  
  
6.  Aggiungere una classe denominata `TestSignature` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!code-vb[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_5.vb)]
     [!code-cs[VSSDKSignatureHelpTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_5.cs)]  
  
7.  Aggiungere alcuni campi privati.  
  
     [!code-vb[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_6.vb)]
     [!code-cs[VSSDKSignatureHelpTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_6.cs)]  
  
8.  Aggiungere un costruttore che imposta i campi e sottoscrive il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-vb[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_7.vb)]
     [!code-cs[VSSDKSignatureHelpTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_7.cs)]  
  
9. Dichiarare un `CurrentParameterChanged` evento. Questo evento viene generato quando l'utente viene compilato in uno dei parametri nella firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_8.vb)]
     [!code-cs[VSSDKSignatureHelpTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_8.cs)]  
  
10. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> proprietà in modo che venga generato il `CurrentParameterChanged` evento quando viene modificato il valore della proprietà.  
  
     [!code-vb[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_9.vb)]
     [!code-cs[VSSDKSignatureHelpTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_9.cs)]  
  
11. Aggiungere un metodo che genera il `CurrentParameterChanged` evento.  
  
     [!code-vb[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_10.vb)]
     [!code-cs[VSSDKSignatureHelpTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_10.cs)]  
  
12. Aggiungere un metodo che calcola il parametro corrente confrontando il numero di virgole nel <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> al numero di virgole nella firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_11.vb)]
     [!code-cs[VSSDKSignatureHelpTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_11.cs)]  
  
13. Aggiungere un gestore eventi per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento che chiama il `ComputeCurrentParameter()` metodo.  
  
     [!code-vb[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_12.vb)]
     [!code-cs[VSSDKSignatureHelpTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_12.cs)]  
  
14. Implementare la proprietà <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Questa proprietà contiene un <xref:Microsoft.VisualStudio.Text.ITrackingSpan> che corrisponde all'intervallo di testo nel buffer a cui si applica la firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_13.vb)]
     [!code-cs[VSSDKSignatureHelpTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_13.cs)]  
  
15. Implementare gli altri parametri.  
  
     [!code-vb[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_14.vb)]
     [!code-cs[VSSDKSignatureHelpTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_14.cs)]  
  
## Implementazione dell'origine della Guida in linea di firma  
 L'origine supporto firma è il set di firme per i quali è fornire informazioni.  
  
#### Per implementare l'origine supporto firma  
  
1.  Aggiungere una classe denominata `TestSignatureHelpSource` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!code-vb[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_15.vb)]
     [!code-cs[VSSDKSignatureHelpTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_15.cs)]  
  
2.  Aggiungere un riferimento al buffer di testo.  
  
     [!code-vb[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_16.vb)]
     [!code-cs[VSSDKSignatureHelpTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_16.cs)]  
  
3.  Aggiungere un costruttore che imposta il buffer di testo e il provider dell'origine supporto firma.  
  
     [!code-vb[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_17.vb)]
     [!code-cs[VSSDKSignatureHelpTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_17.cs)]  
  
4.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. In questo esempio, le firme sono hardcoded, ma in un'implementazione completa è necessario ottenere questa informazione dalla documentazione del linguaggio.  
  
     [!code-vb[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_18.vb)]
     [!code-cs[VSSDKSignatureHelpTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_18.cs)]  
  
5.  Il metodo helper `CreateSignature()` viene fornito solo per completezza.  
  
     [!code-vb[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_19.vb)]
     [!code-cs[VSSDKSignatureHelpTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_19.cs)]  
  
6.  Implementare il metodo <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. In questo esempio, esistono solo due firme, ognuno dei quali include due parametri. Pertanto, questo metodo non è richiesto. In un'implementazione completa, in cui più di un'origine supporto firma è disponibile, questo metodo viene utilizzato per stabilire se l'origine di supporto firma priorità più alta possibile fornire una firma corrispondente. Se non è possibile, il metodo restituisce null e l'origine Avanti priorità più alta viene chiesto di fornire una corrispondenza.  
  
     [!code-vb[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_20.vb)]
     [!code-cs[VSSDKSignatureHelpTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_20.cs)]  
  
7.  Implementare il metodo Dispose \(\):  
  
     [!code-vb[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_21.vb)]
     [!code-cs[VSSDKSignatureHelpTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_21.cs)]  
  
## Implementazione del Provider di origine della Guida in linea di firma  
 Il provider dell'origine supporto firma è responsabile per l'esportazione alla parte di Managed Extensibility Framework \(MEF\) e per creare un'istanza dell'origine supporto firma.  
  
#### Per implementare il provider dell'origine supporto firma  
  
1.  Aggiungere una classe denominata `TestSignatureHelpSourceProvider` che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>,  <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "text" e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di prima \= "default".  
  
     [!code-vb[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_22.vb)]
     [!code-cs[VSSDKSignatureHelpTest#22](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_22.cs)]  
  
2.  Implementare <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> creando un'istanza di `TestSignatureHelpSource`.  
  
     [!code-vb[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_23.vb)]
     [!code-cs[VSSDKSignatureHelpTest#23](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_23.cs)]  
  
## Implementazione del gestore di comando  
 Supporto di firma viene in genere attivato da un \(carattere e ignorato da un\) caratteri. È possibile gestire queste sequenze di tasti implementando un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> in modo che attiva una sessione di supporto firma quando viene ricevuta una \(carattere preceduto da un nome di metodo noto e chiude la sessione quando viene ricevuta una\) caratteri.  
  
#### Per implementare il gestore del comando  
  
1.  Aggiungere una classe denominata `TestSignatureHelpCommand` che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_24.vb)]
     [!code-cs[VSSDKSignatureHelpTest#24](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_24.cs)]  
  
2.  Aggiungere campi privati per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> adapter \(che consente di aggiungere il gestore del comando ai gestori di catena di comando\), la visualizzazione di testo, il broker di supporto firma e la sessione, un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, e la successiva <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!code-vb[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_25.vb)]
     [!code-cs[VSSDKSignatureHelpTest#25](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_25.cs)]  
  
3.  Aggiungere un costruttore per inizializzare questi campi e aggiungere il filtro dei comandi con i filtri di catena di comando.  
  
     [!code-vb[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_26.vb)]
     [!code-cs[VSSDKSignatureHelpTest#26](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_26.cs)]  
  
4.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per attivare la sessione di supporto firma quando il filtro dei comandi riceve un \(carattere dopo uno dei nomi di metodo noto e per chiudere la sessione quando viene ricevuta una\) carattere durante la sessione è ancora attiva. In ogni caso, il comando viene inoltrato.  
  
     [!code-vb[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_27.vb)]
     [!code-cs[VSSDKSignatureHelpTest#27](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_27.cs)]  
  
5.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo in modo che venga sempre inoltra il comando.  
  
     [!code-vb[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_28.vb)]
     [!code-cs[VSSDKSignatureHelpTest#28](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_28.cs)]  
  
## Implementazione di Provider di firme Help comando  
 È possibile fornire il comando Help firma implementando il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per creare un'istanza di gestore del comando quando viene creata la visualizzazione di testo.  
  
#### Per implementare il provider di comandi supporto firma  
  
1.  Aggiungere una classe denominata `TestSignatureHelpController` che implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> ed esportarlo con la <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, e <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!code-vb[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_29.vb)]
     [!code-cs[VSSDKSignatureHelpTest#29](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_29.cs)]  
  
2.  Importazione di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(utilizzato per ottenere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, dato il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto\), il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> \(usato per cercare la parola corrente\) e <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> \(per attivare la sessione di supporto firma\).  
  
     [!code-vb[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_30.vb)]
     [!code-cs[VSSDKSignatureHelpTest#30](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_30.cs)]  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> metodo creando un'istanza di `TestSignatureCommandHandler`.  
  
     [!code-vb[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-signature-help_31.vb)]
     [!code-cs[VSSDKSignatureHelpTest#31](../extensibility/codesnippet/CSharp/walkthrough-displaying-signature-help_31.cs)]  
  
## Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione SignatureHelpTest ed eseguirlo nell'istanza sperimentale.  
  
#### Per compilare e testare la soluzione SignatureHelpTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e tipo di testo che include la parola "add" più una parentesi di apertura.  
  
4.  Dopo aver digitato la parentesi di apertura, si dovrebbe visualizzare una descrizione comandi che visualizza un elenco delle firme di due per il `add()` metodo.  
  
## Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)