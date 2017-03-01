---
title: 'Procedura dettagliata: Visualizzazione di suggerimenti lampadina | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
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
ms.openlocfilehash: e3838b7f9161991840bc5498f66abcfd3ce2b248
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Procedura dettagliata: Visualizzazione di suggerimenti di lampadina
Le lampadine sono icone utilizzate nell'editor di Visual Studio che si espandono per visualizzare un set di azioni, ad esempio le correzioni per problemi identificati dal analizzatori di codice incorporato o refactoring del codice.  
  
 Negli editor di Visual c# e Visual Basic, è possibile utilizzare anche la piattaforma del compilatore .NET ("Roslyn") per scrivere e creare un pacchetto personalizzati analizzatori di codice con le azioni che consentono di visualizzare le lampadine automaticamente. Per altre informazioni, vedere:  
  
-   [Procedura: Scrivere un c# diagnostica e la correzione del codice](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
-   [Procedura: Scrivere una correzione del codice e la diagnostica di Visual Basic](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
 Altri linguaggi come C++ forniscono inoltre le lampadine per alcune azioni rapide, ad esempio un suggerimento per creare un'implementazione stub della funzione.  
  
 Ecco come appare una lampadina. In un progetto di Visual Basic o Visual c#, una sottolineatura ondulata rossa viene visualizzata in un nome di variabile quando non è valido. Quando si passa il mouse sull'identificatore non valido, viene visualizzata una lampadina vicino al cursore.  
  
 ![lampadina](../extensibility/media/lightbulb.png "lampadina")  
  
 Se si fa clic sulla freccia giù per la lampadina, viene visualizzato un set di azioni consigliate, insieme a un'anteprima dell'azione selezionata. Viene illustrato in questo caso, le modifiche che verranno apportate al codice se si esegue l'azione.  
  
 ![Anteprima di lampadina](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
 È possibile utilizzare le lampadine per fornire propria le azioni consigliate. Ad esempio, è possibile fornire azioni per spostare l'apertura di parentesi graffe in una nuova riga o spostarli alla fine della riga precedente. La procedura riportata di seguito viene illustrato come creare una lampadina in cui viene visualizzata la parola corrente e ha suggerito due azioni: **convertire in lettere maiuscole** e **Converti in minuscolo**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo, selezionare **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `LightBulbTest`.  
  
2.  Aggiungere un **classificatore Editor** modello di elemento al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
4.  Aggiungere il seguente riferimento al progetto e impostare **copia locale** a `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Aggiungere un nuovo file di classe e denominarla **LightBulbTest**.  
  
6.  Aggiungere le seguenti istruzioni using:  
  
    ```c#  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementazione del Provider di origine di lampadina  
  
1.  Nel file di classe LightBulbTest.cs, eliminare la classe LightBulbTest. Aggiungere una classe denominata **TestSuggestedActionsSourceProvider** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> Esportarlo con un nome di **azioni consigliate Test** e <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>di "text".</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    ```c#  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  All'interno della classe di provider di origine, importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>e aggiungerlo come proprietà.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>  
  
    ```c#  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A>per restituire un <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>oggetto.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> Si parlerà di origine nella sezione successiva.  
  
    ```c#  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementazione di ISuggestedActionSource  
 L'origine di azione suggerita è responsabile per la raccolta di set di azioni suggerite e aggiungerli nel contesto adatto. In questo caso il contesto è la parola corrente e le azioni consigliate sono **UpperCaseSuggestedAction** e **LowerCaseSuggestedAction**, che verranno descritte nella sezione seguente.  
  
1.  Aggiungere una classe **TestSuggestedActionsSource** che implementa <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>  
  
    ```c#  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Aggiungere campi privati di sola lettura per il provider dell'origine azione suggerita, il buffer di testo e la visualizzazione di testo.  
  
    ```c#  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Aggiungere un costruttore che imposta i campi privati.  
  
    ```c#  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Aggiungere un metodo privato che restituisce la parola che si trova attualmente sotto il cursore. Il seguente metodo esamina la posizione corrente del cursore e chiede il Navigatore struttura di testo per l'estensione della parola. Se il cursore si trova in una parola, il <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>viene restituito nel parametro out; in caso contrario il `out` parametro `null` e il metodo restituisce `false`.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A>(metodo).</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> L'editor chiama questo metodo per scoprire se si desidera visualizzare la lampadina. Questa chiamata viene eseguita molto spesso, ad esempio ogni volta che il cursore si sposta da una riga a un altro o quando il puntatore del mouse viene posizionato su una sottolineatura a zigzag di errore. È asincrona per consentire di altre operazioni dell'interfaccia utente di esercitare durante l'utilizzo di questo metodo. Nella maggior parte dei casi che questo metodo deve eseguire alcune analisi e l'analisi della riga corrente, pertanto l'elaborazione potrebbe richiedere del tempo.  
  
     Nell'implementazione ottiene in modo asincrono il <xref:Microsoft.VisualStudio.Text.Operations.TextExtent>e determina se l'extent è significativo, ad esempio, se esiste un testo diverso da uno spazio vuoto.</xref:Microsoft.VisualStudio.Text.Operations.TextExtent>  
  
    ```c#  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A>metodo, che restituisce una matrice di <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>gli oggetti che contengono i diversi <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>oggetti.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> </xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> Questo metodo viene chiamato quando si espande la lampadina.  
  
    > [!WARNING]
    >  È necessario assicurarsi che le implementazioni di `HasSuggestedActionsAsync()` e `GetSuggestedActions()` sono coerente; ovvero, se `HasSuggestedActionsAsync()` restituisce `true`, quindi `GetSuggestedActions()` deve avere alcune azioni per la visualizzazione. In molti casi `HasSuggestedActionsAsync()` viene chiamato immediatamente prima `GetSuggestedActions()`, ma questo non avviene sempre. Ad esempio, se l'utente richiama le azioni di lampadina premendo (CTRL +.) solo `GetSuggestedActions()` viene chiamato.  
  
    ```c#  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Definire un `SuggestedActionsChanged` evento.  
  
    ```c#  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  Per completare l'implementazione, aggiungere le implementazioni per le `Dispose()` e `TryGetTelemetryId()` metodi. Non si desidera eseguire dati di telemetria, poiché restituisce false e impostare il GUID vuoto.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Implementazione di azioni di lampadina  
  
1.  Nel progetto, aggiungere un riferimento a Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll e set **copia locale** a `False`.  
  
2.  Creare due classi, il primo denominato `UpperCaseSuggestedAction` e il secondo denominato `LowerCaseSuggestedAction`. Entrambe le classi implementano <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>  
  
    ```c#  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Entrambe le classi sono simile ad eccezione del fatto che una chiamata <xref:System.String.ToUpper%2A>e le altre chiamate <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A> Anche se i passaggi seguenti descrivono solo la classe dell'azione per le maiuscole, è necessario implementarle entrambe. Usare i passaggi per l'implementazione dell'azione per le maiuscole come criterio per l'implementazione dell'azione per le minuscole.  
  
3.  Aggiungere le seguenti istruzioni using per queste classi:  
  
    ```c#  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Dichiarare un set di campi privati.  
  
    ```c#  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Aggiungere un costruttore che imposta i campi.  
  
    ```c#  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>metodo in modo che venga visualizzato l'anteprima di azione.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A>  
  
    ```c#  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>metodo in modo che restituisca un oggetto vuoto <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet>enumerazione.</xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> </xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A>  
  
    ```c#  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementare le proprietà nel modo indicato di seguito.  
  
    ```c#  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementare il <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>metodo sostituendo il testo nell'intervallo con il relativo equivalente in caratteri maiuscoli.</xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A>  
  
    ```c#  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  L'azione di lampadina **Invoke** metodo non è previsto per visualizzare l'interfaccia utente.  Se l'azione di visualizzare la nuova interfaccia utente (ad esempio una finestra di anteprima o la selezione), non viene visualizzata l'interfaccia utente direttamente dall'interno di **Invoke** metodo ma pianificare invece per visualizzare l'interfaccia utente dopo l'uscita dal **Invoke**.  
  
10. Per completare l'implementazione, aggiungere il `Dispose()` e `TryGetTelemetryId()` metodi.  
  
    ```c#  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Non dimenticare di eseguire la stessa operazione `LowerCaseSuggestedAction` modifica del testo visualizzato "Convertire '{0}' in lettere minuscole" e la chiamata <xref:System.String.ToUpper%2A>a <xref:System.String.ToLower%2A>.</xref:System.String.ToLower%2A> </xref:System.String.ToUpper%2A>  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione LightBulbTest ed eseguirlo nell'istanza sperimentale.  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare alcune parole. Verrà visualizzata una lampadina a sinistra del testo.  
  
     ![test della lampadina](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Posizionare la lampadina. Verrà visualizzata una freccia rivolta verso il basso.  
  
5.  Quando si sceglie la lampadina, due azioni suggerite devono essere visualizzate, insieme l'anteprima dell'azione selezionata.  
  
     ![test della lampadina, espanso](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Se si fa clic sulla prima azione, tutto il testo nella parola corrente verrà convertito in maiuscole. Se si fa clic sulla seconda azione, tutto il testo nella parola corrente verrà convertito in minuscole.
