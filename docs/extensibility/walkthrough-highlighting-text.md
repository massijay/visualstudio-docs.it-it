---
title: 'Procedura dettagliata: Evidenziazione di testo | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 42
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 029cc7785c49a08c7128bfaaff8f236e438efad8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-highlighting-text"></a>Procedura dettagliata: Evidenziazione del testo
È possibile aggiungere diversi effetti visivi all'editor creando componenti Managed Extensibility Framework (MEF). Questa procedura dettagliata viene illustrato come evidenziare tutte le occorrenze della parola corrente in un file di testo. Se una parola si verifica più volte in un file di testo e si posiziona il punto di inserimento in un'occorrenza, ogni occorrenza viene evidenziata.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c#. (Nel **nuovo progetto** finestra di dialogo, selezionare **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `HighlightWordTest`.  
  
2.  Aggiungere un modello di elemento Editor classificatore al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="defining-a-textmarkertag"></a>Definizione di un TextMarkerTag  
 Evidenziazione di testo il primo passaggio consiste nella sottoclasse <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>e definirne l'aspetto.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Per definire un TextMarkerTag e un MarkerFormatDefinition  
  
1.  Aggiungere un file di classe e denominarla **HighlightWordTag**.  
  
2.  Aggiungere i riferimenti seguenti:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Importare gli spazi dei nomi seguenti.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Linq;  
    using System.Threading;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Text.Tagging;  
    using Microsoft.VisualStudio.Utilities;  
    using System.Windows.Media;  
    ```  
  
4.  Creare una classe che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>e denominarlo `HighlightWordTag`.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>  
  
    ```c#  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Creare una seconda classe che eredita da <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>e denominarla HighlightWordFormatDefinition.</xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> Per utilizzare questa definizione di formato per il tag, è necessario esportarlo con gli attributi seguenti:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: tag utilizzano questa opzione per fare riferimento a questo formato</xref:Microsoft.VisualStudio.Utilities.NameAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: in questo modo il formato da visualizzare nell'interfaccia utente</xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>  
  
    ```c#  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  Nel costruttore per HighlightWordFormatDefinition, definire il nome visualizzato e l'aspetto. La proprietà Background definisce il colore di riempimento, mentre la proprietà Foreground definisce il colore del bordo.  
  
    ```c#  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  Nel costruttore per HighlightWordTag, passare il nome di definizione del formato che appena creato.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Implementazione di un ITagger  
 Il passaggio successivo consiste nell'implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>interfaccia.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> Questa interfaccia viene assegnato a un buffer di testo, tag che forniscono l'evidenziazione del testo e altri effetti visivi.  
  
#### <a name="to-implement-a-tagger"></a>Per implementare un tagger  
  
1.  Creare una classe che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>di tipo `HighlightWordTag`e denominarla `HighlightWordTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>  
  
    ```c#  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Aggiungere i seguenti campi privati e le proprietà alla classe:  
  
    -   Un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, che corrisponde alla visualizzazione di testo corrente.</xref:Microsoft.VisualStudio.Text.Editor.ITextView>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.ITextBuffer>, che corrisponde al buffer di testo sottostante la visualizzazione di testo.</xref:Microsoft.VisualStudio.Text.ITextBuffer>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, che consente di trovare il testo.</xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    -   Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, che dispone di metodi per spostarsi all'interno di intervalli di testo.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>  
  
    -   Oggetto <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, che contiene il set di parole per evidenziare.</xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>  
  
    -   Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, che corrisponde alla parola corrente.</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
    -   Oggetto <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, che corrisponde alla posizione corrente del punto di inserimento.</xref:Microsoft.VisualStudio.Text.SnapshotPoint>  
  
    -   Un oggetto di blocco.  
  
    ```c#  
    ITextView View { get; set; }  
    ITextBuffer SourceBuffer { get; set; }  
    ITextSearchService TextSearchService { get; set; }  
    ITextStructureNavigator TextStructureNavigator { get; set; }  
    NormalizedSnapshotSpanCollection WordSpans { get; set; }  
    SnapshotSpan? CurrentWord { get; set; }  
    SnapshotPoint RequestedPoint { get; set; }  
    object updateLock = new object();  
  
    ```  
  
3.  Aggiungere un costruttore che inizializza le proprietà elencate in precedenza e aggiunge <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>e <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged>i gestori eventi.</xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,  
    ITextStructureNavigator textStructureNavigator)  
    {  
        this.View = view;  
        this.SourceBuffer = sourceBuffer;  
        this.TextSearchService = textSearchService;  
        this.TextStructureNavigator = textStructureNavigator;  
        this.WordSpans = new NormalizedSnapshotSpanCollection();  
        this.CurrentWord = null;  
        this.View.Caret.PositionChanged += CaretPositionChanged;  
        this.View.LayoutChanged += ViewLayoutChanged;  
    }  
  
    ```  
  
4.  I gestori eventi entrambi chiamano il `UpdateAtCaretPosition` metodo.  
  
    ```c#  
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        // If a new snapshot wasn't generated, then skip this layout   
        if (e.NewSnapshot != e.OldSnapshot)  
        {  
            UpdateAtCaretPosition(View.Caret.Position);  
        }  
    }  
  
    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)  
    {  
        UpdateAtCaretPosition(e.NewPosition);  
    }  
    ```  
  
5.  È inoltre necessario aggiungere una `TagsChanged` evento che verrà chiamato dal metodo update.  
  
     [!code-cs[VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs) ] 
     [!code-vb [VSSDKHighlightWordTest&#10;](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]  
  
6.  Il `UpdateAtCaretPosition()` metodo trova tutte le parole nel buffer di testo che corrisponde alla parola in cui il cursore è posizionato e crea un elenco di <xref:Microsoft.VisualStudio.Text.SnapshotSpan>oggetti che corrispondono alle occorrenze della parola.</xref:Microsoft.VisualStudio.Text.SnapshotSpan> Viene quindi chiamato `SynchronousUpdate`, che genera il `TagsChanged` evento.  
  
    ```c#  
    void UpdateAtCaretPosition(CaretPosition caretPosition)  
    {  
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);  
  
        if (!point.HasValue)  
            return;  
  
        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it   
        if (CurrentWord.HasValue  
            && CurrentWord.Value.Snapshot == View.TextSnapshot  
            && point.Value >= CurrentWord.Value.Start  
            && point.Value <= CurrentWord.Value.End)  
        {  
            return;  
        }  
  
        RequestedPoint = point.Value;  
        UpdateWordAdornments();  
    }  
  
    void UpdateWordAdornments()  
    {  
        SnapshotPoint currentRequest = RequestedPoint;  
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();  
        //Find all words in the buffer like the one the caret is on  
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);  
        bool foundWord = true;  
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit  
        if (!WordExtentIsValid(currentRequest, word))  
        {  
            //Before we retry, make sure it is worthwhile   
            if (word.Span.Start != currentRequest  
                 || currentRequest == currentRequest.GetContainingLine().Start  
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))  
            {  
                foundWord = false;  
            }  
            else  
            {  
                // Try again, one character previous.    
                //If the caret is at the end of a word, pick up the word.  
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);  
  
                //If the word still isn't valid, we're done   
                if (!WordExtentIsValid(currentRequest, word))  
                    foundWord = false;  
            }  
        }  
  
        if (!foundWord)  
        {  
            //If we couldn't find a word, clear out the existing markers  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);  
            return;  
        }  
  
        SnapshotSpan currentWord = word.Span;  
        //If this is the current word, and the caret moved within a word, we're done.   
        if (CurrentWord.HasValue && currentWord == CurrentWord)  
            return;  
  
        //Find the new spans  
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);  
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;  
  
        wordSpans.AddRange(TextSearchService.FindAll(findData));  
  
        //If another change hasn't happened, do a real update   
        if (currentRequest == RequestedPoint)  
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);  
    }  
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)  
    {  
        return word.IsSignificant  
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));  
    }  
  
    ```  
  
7.  Il `SynchronousUpdate` esegue un aggiornamento sincrono di `WordSpans` e `CurrentWord` le proprietà e genera il `TagsChanged` evento.  
  
    ```vb  
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)  
    {  
        lock (updateLock)  
        {  
            if (currentRequest != RequestedPoint)  
                return;  
  
            WordSpans = newSpans;  
            CurrentWord = newCurrentWord;  
  
            var tempEvent = TagsChanged;  
            if (tempEvent != null)  
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));  
        }  
    }  
    ```  
  
8.  È necessario implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>(metodo).</xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Questo metodo accetta una raccolta di <xref:Microsoft.VisualStudio.Text.SnapshotSpan>gli oggetti e restituisce un'enumerazione degli intervalli di tag.</xref:Microsoft.VisualStudio.Text.SnapshotSpan>  
  
     In c#, implementare questo metodo come un iteratore yield, che consente la valutazione lazy (vale a dire la valutazione del set di solo quando si accede a singoli elementi) dei tag. In Visual Basic, aggiungere i tag a un elenco e restituire l'elenco.  
  
     In questo caso il metodo restituisce un <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>oggetto con una "blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, che fornisce uno sfondo blu.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601>  
  
    ```c#  
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)  
    {  
        if (CurrentWord == null)  
            yield break;  
  
        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same  
        // collection throughout  
        SnapshotSpan currentWord = CurrentWord.Value;  
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;  
  
        if (spans.Count == 0 || wordSpans.Count == 0)  
            yield break;  
  
        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot   
        if (spans[0].Snapshot != wordSpans[0].Snapshot)  
        {  
            wordSpans = new NormalizedSnapshotSpanCollection(  
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));  
  
            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);  
        }  
  
        // First, yield back the word the cursor is under (if it overlaps)   
        // Note that we'll yield back the same word again in the wordspans collection;   
        // the duplication here is expected.   
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))  
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());  
  
        // Second, yield all the other words in the file   
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))  
        {  
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());  
        }  
    }  
    ```  
  
## <a name="creating-a-tagger-provider"></a>Creazione di un Provider Tagger  
 Per creare il tagger, è necessario implementare un <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> Questa classe è un componente MEF, pertanto è necessario impostare gli attributi corretti in modo che questa estensione è riconosciuta.  
  
> [!NOTE]
>  Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>Per creare un provider tagger  
  
1.  Creare una classe denominata `HighlightWordTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>ed esportarlo con una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.</xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> </xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>  
  
    ```c#  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  È necessario importare due servizi di editor, il <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>e <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, per creare un'istanza di tagger.</xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> </xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>  
  
    ```c#  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>per restituire un'istanza di `HighlightWordTagger`.</xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>  
  
    ```c#  
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag  
    {  
        //provide highlighting only on the top buffer   
        if (textView.TextBuffer != buffer)  
            return null;  
  
        ITextStructureNavigator textStructureNavigator =  
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);  
  
        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione HighlightWordTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Per compilare e testare la soluzione HighlightWordTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo in cui le parole sono ripetute, ad esempio, "hello hello hello".  
  
4.  Posizionare il cursore in una delle occorrenze di "hello". Tutte le occorrenze dovrebbero essere evidenziata in blu.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
