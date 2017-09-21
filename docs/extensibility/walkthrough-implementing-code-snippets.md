---
title: "Procedura dettagliata: Implementazione di frammenti di codice | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adbc5382-d170-441c-9fd0-80faa1816478
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Procedura dettagliata: Implementazione di frammenti di codice
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare frammenti di codice e includerli in un'estensione di editor in modo che gli utenti dell'estensione possono aggiungere il proprio codice.  
  
 Un frammento di codice è un frammento di codice o testo che può essere incorporato in un file. Per visualizzare tutti i frammenti registrati per determinati linguaggi di programmazione, nel **strumenti** menu, fare clic su **Gestione frammenti di codice**. Per inserire un frammento di codice in un file, in cui si desidera che il frammento, fare clic su **Inserisci frammento di codice** o **Racchiudi**, individuare il frammento desiderato e quindi fare doppio clic. Premere TAB o MAIUSC \+ TAB per modificare le parti pertinenti del frammento e premere INVIO o ESC per accettarla. Per altre informazioni, vedere [Frammenti di codice](../ide/code-snippets.md).  
  
 Un frammento di codice è contenuto in un file XML con l'estensione del nome file snippet. Un frammento di codice può contenere i campi che vengono evidenziati dopo l'inserimento del frammento in modo che l'utente può trovare e modificarle. Un file di frammento fornisce inoltre informazioni per il **Gestione frammenti di codice** in modo che sia possibile visualizzare il nome del frammento di codice nella categoria corretto. Per informazioni sullo schema del frammento di codice, vedere [Riferimento dello schema dei frammenti di codice](../ide/code-snippets-schema-reference.md).  
  
 Questa procedura dettagliata illustra come eseguire queste attività:  
  
1.  Creare e registrare i frammenti di codice per una lingua specifica.  
  
2.  Aggiungere il **Inserisci frammento di codice** comando a un menu di scelta rapida.  
  
3.  Implementare l'espansione di frammento di codice.  
  
 Questa procedura dettagliata è basata su [Procedura dettagliata: Visualizzazione di completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).  
  
## Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Creazione e registrazione di frammenti di codice  
 Frammenti di codice sono in genere associati a un servizio di linguaggio registrato. Tuttavia, non è necessario implementare un <xref:Microsoft.VisualStudio.Package.LanguageService> per registrare i frammenti di codice. Al contrario, specificare solo un GUID nel file di indice del frammento di codice e quindi utilizzare lo stesso GUID nel <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> aggiunti al progetto.  
  
 La procedura seguente viene illustrato come creare frammenti di codice e associarli a un GUID specifico.  
  
1.  Creare la struttura di directory seguente:  
  
     **%INSTALLDIR%\\TestSnippets\\Snippets\\1033\\**  
  
     dove *% InstallDir %* è la cartella di installazione di Visual Studio. \(Anche se questo percorso è in genere utilizzato per installare i frammenti di codice, è possibile specificare qualsiasi percorso.\)  
  
2.  Nella cartella \\1033\\, creare un file XML e denominarlo **TestSnippets.xml**. \(Anche se questo nome viene in genere utilizzato per un file di indice del frammento di codice, è possibile specificare qualsiasi nome, purché ha un'estensione di file XML.\) Aggiungere il testo seguente, quindi eliminare il GUID segnaposto e aggiungere il proprio.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <SnippetCollection> <Language Lang="TestSnippets" Guid="{00000000-0000-0000-0000-000000000000}"> <SnippetDir> <OnOff>On</OnOff> <Installed>true</Installed> <Locale>1033</Locale> <DirPath>%InstallRoot%\TestSnippets\Snippets\%LCID%\</DirPath> <LocalizedName>Snippets</LocalizedName> </SnippetDir> </Language> </SnippetCollection>  
    ```  
  
3.  Creare un file nella cartella frammento, il nome **test**`.snippet`, quindi aggiungere il testo seguente:  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?> <CodeSnippets  xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet"> <CodeSnippet Format="1.0.0"> <Header> <Title>Test replacement fields</Title> <Shortcut>test</Shortcut> <Description>Code snippet for testing replacement fields</Description> <Author>MSIT</Author> <SnippetTypes> <SnippetType>Expansion</SnippetType> </SnippetTypes> </Header> <Snippet> <Declarations> <Literal> <ID>param1</ID> <ToolTip>First field</ToolTip> <Default>first</Default> </Literal> <Literal> <ID>param2</ID> <ToolTip>Second field</ToolTip> <Default>second</Default> </Literal> </Declarations> <References> <Reference> <Assembly>System.Windows.Forms.dll</Assembly> </Reference> </References> <Code Language="TestSnippets"> <![CDATA[MessageBox.Show("$param1$"); MessageBox.Show("$param2$");]]> </Code> </Snippet> </CodeSnippet> </CodeSnippets>  
    ```  
  
 La procedura seguente viene illustrato come registrare i frammenti di codice.  
  
#### Per registrare i frammenti di codice per un GUID specifico  
  
1.  Aprire il **CompletionTest** progetto. Per informazioni su come creare il progetto, vedere [Procedura dettagliata: Visualizzazione di completamento delle istruzioni](../extensibility/walkthrough-displaying-statement-completion.md).  
  
2.  Nel progetto, aggiungere riferimenti agli assembly seguenti:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.TextManager.Interop.8.0  
  
    -   Microsoft.MSXML  
  
3.  Nel progetto, aprire il file source.extension.vsixmanifest.  
  
4.  Assicurarsi che il **asset** scheda contiene un **VsPackage** tipo e che il contenuto **progetto** è impostato sul nome del progetto.  
  
5.  Selezionare il progetto CompletionTest e nella finestra Proprietà impostare **Genera Pkgdef File** a **true**. Salvare il progetto.  
  
6.  Aggiungere un valore statico `SnippetUtilities` classe al progetto.  
  
     [!code-cs[VSSDKCompletionTest#22](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_1.cs)]
     [!code-vb[VSSDKCompletionTest#22](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_1.vb)]  
  
7.  Nella classe SnippetUtilities, definire un GUID e assegnargli il valore utilizzato nel file SnippetsIndex.xml.  
  
     [!code-cs[VSSDKCompletionTest#23](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_2.cs)]
     [!code-vb[VSSDKCompletionTest#23](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_2.vb)]  
  
8.  Aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> per la `TestCompletionHandler` classe. Questo attributo può essere aggiunto a qualsiasi classe \(non statici\) pubblico o interno del progetto. \(Potrebbe essere necessario aggiungere un `using` istruzione per lo spazio dei nomi Microsoft.VisualStudio.Shell.\)  
  
     [!code-cs[VSSDKCompletionTest#24](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_3.cs)]
     [!code-vb[VSSDKCompletionTest#24](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_3.vb)]  
  
9. Compilare ed eseguire il progetto. Nell'istanza sperimentale di Visual Studio che viene avviato quando viene eseguito il progetto, il frammento di codice appena registrato deve essere visualizzato nel **Gestione frammenti di codice** sotto il **TestSnippets** language.  
  
## Aggiunta di Insert Snippet, comando al Menu di scelta rapida  
 Il **Inserisci frammento di codice** comando non è incluso nel menu di scelta rapida per un file di testo. Pertanto, è necessario abilitare il comando.  
  
#### Per aggiungere il comando Inserisci frammento di codice per il menu di scelta rapida  
  
1.  Aprire il `TestCompletionCommandHandler` file di classe.  
  
     Poiché questa classe implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, è possibile attivare il **Inserisci frammento di codice** comando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. Prima di abilitare il comando, verificare che questo metodo non è viene chiamato all'interno di una funzione di automazione perché quando il **Inserisci frammento di codice** si fa clic sul comando, verrà visualizzato l'interfaccia utente di selezione frammento di codice \(UI\).  
  
     [!code-cs[VSSDKCompletionTest#25](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_4.cs)]
     [!code-vb[VSSDKCompletionTest#25](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_4.vb)]  
  
2.  Compilare ed eseguire il progetto. Nell'istanza sperimentale, aprire un file con estensione zzz e quindi fare clic in essa contenuti. Il **Inserisci frammento di codice** comando dovrebbe essere visualizzato il menu di scelta rapida.  
  
## Implementazione di frammento espansione in selezione frammento di codice dell'interfaccia utente  
 In questa sezione viene illustrato come implementare l'espansione di frammento di codice in modo che la selezione frammento di codice dell'interfaccia utente viene visualizzato quando **Inserisci frammento di codice** si fa clic sul menu di scelta rapida. Un frammento di codice viene espanso anche quando un utente digita il collegamento al frammento di codice e quindi preme TAB.  
  
 Per visualizzare la selezione frammento di codice dell'interfaccia utente e per abilitare la navigazione e l'accettazione di post\-inserimento frammento, utilizzare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. L'inserimento stesso viene gestita dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A> metodo.  
  
 L'implementazione di espansione di frammento di codice utilizza legacy <xref:Microsoft.VisualStudio.TextManager.Interop> interfacce. Quando si traducono dalle classi editor corrente al codice legacy, tenere presente che le interfacce legacy utilizzano una combinazione di numeri di riga e colonna per specificare i percorsi in un buffer di testo, ma le classi corrente utilizzano un indice. Pertanto, se un buffer con tre righe, ognuna delle quali dispone di dieci caratteri \(più di una nuova riga, che viene considerata come 1 carattere\), il quarto carattere nella terza riga si trova in posizione 27 nell'implementazione corrente, ma è nella riga 2, posizione 3 nell'implementazione precedente.  
  
#### Per implementare l'espansione di frammento di codice  
  
1.  Il file che contiene la `TestCompletionCommandHandler` classe, aggiungere il codice seguente `using` istruzioni.  
  
     [!code-cs[VSSDKCompletionTest#26](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_5.cs)]
     [!code-vb[VSSDKCompletionTest#26](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_5.vb)]  
  
2.  Rendere la `TestCompletionCommandHandler` classe implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia.  
  
     [!code-cs[VSSDKCompletionTest#27](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_6.cs)]
     [!code-vb[VSSDKCompletionTest#27](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_6.vb)]  
  
3.  Nella `TestCompletionCommandHandlerProvider` classe, importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>.  
  
     [!code-cs[VSSDKCompletionTest#28](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_7.cs)]
     [!code-vb[VSSDKCompletionTest#28](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_7.vb)]  
  
4.  Aggiungere alcuni campi privati per le interfacce di espansione del codice e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#29](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_8.cs)]
     [!code-vb[VSSDKCompletionTest#29](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_8.vb)]  
  
5.  Nel costruttore della `TestCompletionCommandHandler` classe, impostare i campi seguenti.  
  
     [!code-cs[VSSDKCompletionTest#30](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_9.cs)]
     [!code-vb[VSSDKCompletionTest#30](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_9.vb)]  
  
6.  Per visualizzare selezione frammento di codice quando l'utente fa clic il **Inserisci frammento di codice** comando, aggiungere il codice seguente per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. \(Per rendere questa spiegazione più leggibile, non viene visualizzato il codice di Exec \(\) che viene utilizzato per il completamento delle istruzioni; al contrario, blocchi di codice vengono aggiunti al metodo esistente\). Aggiungere il blocco di codice seguente dopo il codice che verifica la presenza di un carattere.  
  
     [!code-cs[VSSDKCompletionTest#31](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_10.cs)]
     [!code-vb[VSSDKCompletionTest#31](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_10.vb)]  
  
7.  Se un frammento di codice include campi che è possono spostarsi, la sessione di espansione viene mantenuta aperta finché l'espansione in modo esplicito viene accettato. Se il frammento di codice non dispone di campi, la sessione viene chiusa e viene restituita come `null` per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionManager.InvokeInsertionUI%2A> metodo. Nel <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> \(metodo\), dopo la selezione frammento di codice dell'interfaccia utente che è stato aggiunto nel passaggio precedente, aggiungere il codice seguente per gestire la navigazione di frammenti \(quando l'utente preme TAB o MAIUSC \+ TAB dopo l'inserimento del frammento\).  
  
     [!code-cs[VSSDKCompletionTest#32](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_11.cs)]
     [!code-vb[VSSDKCompletionTest#32](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_11.vb)]  
  
8.  Per inserire il frammento di codice quando l'utente digita la scelta rapida corrispondente e quindi preme TAB, aggiungere codice per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo. Verrà visualizzato il metodo privato che inserisce il frammento di codice in un passaggio successivo. Aggiungere il codice seguente dopo il codice di navigazione che è stato aggiunto nel passaggio precedente.  
  
     [!code-cs[VSSDKCompletionTest#33](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_12.cs)]
     [!code-vb[VSSDKCompletionTest#33](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_12.vb)]  
  
9. Implementare i metodi del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient> interfaccia. In questa implementazione sono gli unici metodi di interesse <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.EndExpansion%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Gli altri metodi devono restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
     [!code-cs[VSSDKCompletionTest#34](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_13.cs)]
     [!code-vb[VSSDKCompletionTest#34](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_13.vb)]  
  
10. Implementare il metodo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansionClient.OnItemChosen%2A>. Il metodo helper che effettivamente inserisce le espansioni si parlerà in un passaggio successivo. Il <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> fornisce informazioni di riga e colonna, che è possibile ottenere dal <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  
  
     [!code-cs[VSSDKCompletionTest#35](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_14.cs)]
     [!code-vb[VSSDKCompletionTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_14.vb)]  
  
11. Il metodo privato seguente consente di inserire un frammento di codice, in base sia il collegamento o il titolo e il percorso. Chiama quindi il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsExpansion.InsertNamedExpansion%2A> metodo con il frammento di codice.  
  
     [!code-cs[VSSDKCompletionTest#36](../extensibility/codesnippet/CSharp/walkthrough-implementing-code-snippets_15.cs)]
     [!code-vb[VSSDKCompletionTest#36](../extensibility/codesnippet/VisualBasic/walkthrough-implementing-code-snippets_15.vb)]  
  
## Compilare e testare l'espansione di frammento di codice  
 È possibile verificare se funziona espansione frammento di codice nel progetto.  
  
1.  Compilare la soluzione. Quando si esegue il progetto nel debugger, viene creata un'istanza di una seconda istanza di Visual Studio.  
  
2.  Aprire un file di testo e digitare un testo.  
  
3.  Fare doppio clic in un punto qualsiasi nel testo e quindi fare clic su **Inserisci frammento di codice**.  
  
4.  Selezione frammento di codice dell'interfaccia utente deve essere visualizzate con una finestra popup che afferma **testare i campi di sostituzione**. Fare doppio clic sulla finestra a comparsa.  
  
     Il frammento seguente deve essere inserito.  
  
    ```  
    MessageBox.Show("first"); MessageBox.Show("second");  
    ```  
  
     Non si preme INVIO o ESC.  
  
5.  Premere TAB e MAIUSC \+ TAB per passare tra "first" e "secondo".  
  
6.  Accettare l'inserimento premendo INVIO o ESC.  
  
7.  In un'altra parte del testo, digitare "test" e quindi premere TAB. Poiché "test" è il collegamento al frammento di codice, il frammento di codice deve essere inserito nuovamente.  
  
## Passaggi successivi