---
title: 'Procedura dettagliata: Utilizzo di un comando della Shell con un&quot;estensione di Editor | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
caps.latest.revision: 46
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
ms.openlocfilehash: 14ac62df46d3edaa93a18d5d2a2e717c7f0ba2de
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-using-a-shell-command-with-an-editor-extension"></a>Procedura dettagliata: Utilizzo di un comando della Shell con un'estensione di Editor
Da un pacchetto Visual Studio, è possibile aggiungere funzionalità quali i comandi di menu nell'editor. Questa procedura dettagliata viene illustrato come aggiungere un'area di controllo per una visualizzazione nell'editor di testo tramite la chiamata di un comando di menu.  
  
 Questa procedura dettagliata viene illustrato l'utilizzo di un package VS insieme a un componente Managed Extensibility Framework (MEF). È necessario utilizzare un VSPackage per registrare il comando di menu con la shell di Visual Studio e utilizzare il comando per accedere alla parte componente MEF.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Creazione di un'estensione con un comando di Menu  
 Creare un package VS che inserisce un comando di menu denominato **aggiungere Adornment** sul **strumenti** menu.  
  
1.  Creare un progetto VSIX c# denominato `MenuCommandTest`e aggiungere il nome di un modello di elemento personalizzato comando **AddAdornment**. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Viene aperta una soluzione denominata MenuCommandTest. Il file MenuCommandTestPackage è il codice che crea il comando di menu e lo inserisce nel **strumenti** menu. A questo punto, il comando che consente solo una finestra di messaggio da visualizzare. Passaggi successivi viene illustrato come modificare questa opzione per visualizzare l'area di controllo di commento.  
  
3.  Aprire il file source.extension.vsixmanifest nell'Editor manifest VSIX. Il `Assets` scheda deve avere una riga per un Microsoft.VisualStudio.VsPackage denominato MenuCommandTest.  
  
4.  Salvare e chiudere il file Source.extension.vsixmanifest.  
  
## <a name="adding-a-mef-extension-to-the-command-extension"></a>Aggiunta di un'estensione MEF all'estensione di comando  
  
1.  In **Esplora**, pulsante destro del mouse sul nodo della soluzione, fare clic su **Aggiungi**, quindi fare clic su **nuovo progetto**. Nel **Aggiungi nuovo progetto** la finestra di dialogo, fare clic su **estendibilità** in **Visual c#**, quindi **progetto VSIX**. Denominare il progetto `CommentAdornmentTest`.  
  
2.  Poiché questo progetto interagirà con l'assembly di VSPackage sicuro, è necessario firmare l'assembly. È possibile riutilizzare il file di chiave già creato per l'assembly di VSPackage.  
  
    1.  Aprire le proprietà del progetto e selezionare il **firma** scheda.  
  
    2.  Selezionare **firmare l'assembly**.  
  
    3.  In **Scegli un file chiave con nome sicuro**, selezionare il file snk che è stato generato per l'assembly MenuCommandTest.  
  
## <a name="referring-to-the-mef-extension-in-the-vspackage-project"></a>Riferimento all'estensione di MEF nel progetto di VSPackage  
 Poiché si sta aggiungendo un componente MEF VSPackage, è necessario specificare entrambi i tipi di asset nel manifesto.  
  
> [!NOTE]
>  Per ulteriori informazioni su MEF, vedere [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Per fare riferimento al componente MEF nel progetto di VSPackage  
  
1.  Nel progetto MenuCommandTest, aprire il file source.extension.vsixmanifest nell'Editor del manifesto VSIX.  
  
2.  Nel **asset** scheda, fare clic su **nuovo**.  
  
3.  Nel **tipo** scegliere **Microsoft.VisualStudio.MefComponent**.  
  
4.  Nel **origine** scegliere **un progetto nella soluzione corrente**.  
  
5.  Nel **progetto** scegliere **CommentAdornmentTest**.  
  
6.  Salvare e chiudere il file source.extension.vsixmanifest.  
  
7.  Assicurarsi che il progetto MenuCommandTest contenga un riferimento al progetto CommentAdornmentTest.  
  
8.  Nel progetto CommentAdornmentTest, impostare il progetto per generare un assembly. Nel **Esplora soluzioni**, selezionare il progetto ed esaminare il **proprietà** finestra per la **copia Output di compilazione per OutputDirectory** proprietà e impostarlo su **true**.  
  
## <a name="defining-a-comment-adornment"></a>Definizione di un'area di controllo di commento  
 L'area di controllo di commento stesso è costituito da un <xref:Microsoft.VisualStudio.Text.ITrackingSpan>che registra il testo selezionato e alcune stringhe che rappresentano l'autore e la descrizione del testo.</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
#### <a name="to-define-a-comment-adornment"></a>Per definire un'area di controllo di commento  
  
1.  Nel progetto CommentAdornmentTest, aggiungere un nuovo file di classe e denominarla `CommentAdornment`.  
  
2.  Aggiungere i riferimenti seguenti:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Aggiungere il codice seguente `using` istruzione.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Il file deve contenere una classe denominata `CommentAdornment`.  
  
    ```  
    internal class CommentAdornment  
    ```  
  
5.  Aggiungere tre campi per il `CommentAdornment` classe per il <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, l'autore e la descrizione.</xref:Microsoft.VisualStudio.Text.ITrackingSpan>  
  
    ```c#  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Aggiungere un costruttore che inizializza i campi.  
  
    ```c#  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="creating-a-visual-element-for-the-adornment"></a>Creazione di un elemento visivo per l'area di controllo  
 È inoltre necessario definire un elemento visivo per l'area di controllo. Per questa procedura dettagliata, definire un controllo che eredita dalla classe di Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.</xref:System.Windows.Controls.Canvas>  
  
1.  Creare una classe nel progetto CommentAdornmentTest e denominarla `CommentBlock`.  
  
2.  Aggiungere le istruzioni `using` riportate di seguito.  
  
    ```c#  
    using Microsoft.VisualStudio.Text;  
    using System;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Media;  
    using System.Windows.Shapes;  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Rendere il `CommentBlock` classe ereditare da <xref:System.Windows.Controls.Canvas>.</xref:System.Windows.Controls.Canvas>  
  
    ```c#  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Aggiungere alcuni campi privati per definire gli aspetti visivi dell'area di controllo.  
  
    ```c#  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Aggiungere un costruttore che definisce l'area di controllo di commento e aggiunge il testo corrispondente.  
  
    ```c#  
    public CommentBlock(double textRightEdge, double viewRightEdge,   
            Geometry newTextGeometry, string author, string body)  
    {  
        if (brush == null)  
        {  
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));  
            brush.Freeze();  
            Brush penBrush = new SolidColorBrush(Colors.Green);  
            penBrush.Freeze();  
            solidPen = new Pen(penBrush, 0.5);  
            solidPen.Freeze();  
            dashPen = new Pen(penBrush, 0.5);  
            dashPen.DashStyle = DashStyles.Dash;  
            dashPen.Freeze();  
        }  
  
        this.textGeometry = newTextGeometry;  
  
        TextBlock tb1 = new TextBlock();  
        tb1.Text = author;  
        TextBlock tb2 = new TextBlock();  
        tb2.Text = body;  
  
        const int MarginWidth = 8;  
        this.commentGrid = new Grid();  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        this.commentGrid.RowDefinitions.Add(new RowDefinition());  
        ColumnDefinition cEdge = new ColumnDefinition();  
        cEdge.Width = new GridLength(MarginWidth);  
        ColumnDefinition cEdge2 = new ColumnDefinition();  
        cEdge2.Width = new GridLength(MarginWidth);  
        this.commentGrid.ColumnDefinitions.Add(cEdge);  
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());  
        this.commentGrid.ColumnDefinitions.Add(cEdge2);  
  
        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();  
        rect.RadiusX = 6;  
        rect.RadiusY = 3;  
        rect.Fill = brush;  
        rect.Stroke = Brushes.Green;  
  
            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);  
            tb1.Measure(inf);  
            tb2.Measure(inf);  
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);  
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;  
  
        Grid.SetColumn(rect, 0);  
        Grid.SetRow(rect, 0);  
         Grid.SetRowSpan(rect, 2);  
        Grid.SetColumnSpan(rect, 3);  
        Grid.SetRow(tb1, 0);  
        Grid.SetColumn(tb1, 1);  
        Grid.SetRow(tb2, 1);  
        Grid.SetColumn(tb2, 1);  
        this.commentGrid.Children.Add(rect);  
        this.commentGrid.Children.Add(tb1);  
        this.commentGrid.Children.Add(tb2);  
  
        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));  
         Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);  
  
        this.Children.Add(this.commentGrid);  
    }  
    ```  
  
6.  Anche implementare un <xref:System.Windows.Controls.Panel.OnRender%2A>gestore eventi che consente di disegnare l'area di controllo.</xref:System.Windows.Controls.Panel.OnRender%2A>  
  
    ```c#  
    protected override void OnRender(DrawingContext dc)  
    {  
        base.OnRender(dc);  
        if (this.textGeometry != null)  
        {  
            dc.DrawGeometry(brush, solidPen, this.textGeometry);  
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);  
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);  
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);  
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);  
            dc.DrawLine(dashPen, p1, p2);  
            dc.DrawLine(dashPen, p2, p3);  
        }  
    }  
    ```  
  
## <a name="adding-an-iwpftextviewcreationlistener"></a>Aggiunta di un IWpfTextViewCreationListener  
 Il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>è un componente MEF che è possibile utilizzare per l'ascolto per visualizzare gli eventi di creazione.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>  
  
1.  Aggiungere un file di classe al progetto CommentAdornmentTest e denominarla `Connector`.  
  
2.  Aggiungere le istruzioni `using` riportate di seguito.  
  
    ```c#  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Dichiarare una classe che implementa <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>ed esportarlo con una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>"text" e un <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>.</xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> </xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> </xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> L'attributo di tipo di contenuto specifica il tipo di contenuto a cui si applica il componente. Il tipo di testo è il tipo base per tutti i tipi di file non binari. Pertanto, quasi ogni visualizzazione di testo che viene creato sarà di questo tipo. L'attributo di ruolo visualizzazione di testo specifica il tipo di visualizzazione di testo a cui si applica il componente. Visualizzare i ruoli testo documento in genere visualizza il testo che è composto da righe e viene archiviato in un file.  
  
     [!code-vb[VSSDKMenuCommandTest&#11;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb) ] 
     [!code-cs [VSSDKMenuCommandTest&#11;](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>metodo in modo che venga chiamato il metodo statico `Create()` evento il `CommentAdornmentManager`.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>  
  
    ```c#  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Aggiungere un metodo che è possibile utilizzare per eseguire il comando.  
  
    ```c#  
    static public void Execute(IWpfTextViewHost host)  
    {  
        IWpfTextView view = host.TextView;  
        //Add a comment on the selected text.   
        if (!view.Selection.IsEmpty)  
        {  
            //Get the provider for the comment adornments in the property bag of the view.  
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));  
  
            //Add some arbitrary author and comment text.   
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;  
            string comment = "Four score....";  
  
            //Add the comment adornment using the provider.  
            provider.Add(view.Selection.SelectedSpans[0], author, comment);  
        }  
    }  
    ```  
  
## <a name="defining-an-adornment-layer"></a>Definizione di un livello di area di controllo  
 Per aggiungere una nuova area di controllo, è necessario definire un livello di area di controllo.  
  
#### <a name="to-define-an-adornment-layer"></a>Per definire un livello di area di controllo  
  
1.  Nel `Connector` classe, dichiarare un campo pubblico di tipo <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute>che specifica un nome univoco per il livello di area di controllo e un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute>che definisce la relazione nell'ordine Z di questo livello di area di controllo per gli altri livelli di visualizzazione testo (testo, del punto di inserimento e selezione).</xref:Microsoft.VisualStudio.Utilities.OrderAttribute> </xref:Microsoft.VisualStudio.Utilities.NameAttribute> </xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>  
  
    ```c#  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="providing-comment-adornments"></a>Fornisce informazioni ulteriori commento  
 Quando si definisce un'area di controllo, anche implementare un provider di adornment commento e un gestore dell'area di controllo di commento. Il provider adornment commento mantiene un elenco di aree di controllo di commento, è in ascolto <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>gli eventi nel buffer di testo sottostante e le eliminazioni commento grafici quando viene eliminato il testo sottostante.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
1.  Aggiungere un nuovo file di classe al progetto CommentAdornmentTest e denominarla `CommentAdornmentProvider`.  
  
2.  Aggiungere le istruzioni `using` riportate di seguito.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Aggiungere una classe denominata `CommentAdornmentProvider`.  
  
    ```c#  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Aggiungere campi privati per il buffer di testo e l'elenco di grafici di commento relative al buffer.  
  
    ```c#  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  Aggiungere un costruttore per `CommentAdornmentProvider`. Questo costruttore deve disporre dell'accesso privato perché il provider viene creata un'istanza per il `Create()` metodo. Il costruttore aggiunge la `OnBufferChanged` gestore eventi per il <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>eventi.</xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed>  
  
    ```c#  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Aggiungere il metodo `Create()`.  
  
    ```c#  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Aggiungere il metodo `Detach()`.  
  
    ```c#  
    public void Detach()  
    {  
        if (this.buffer != null)  
        {  
            //remove the Changed listener   
            this.buffer.Changed -= OnBufferChanged;  
            this.buffer = null;  
        }  
    }  
    ```  
  
8.  Aggiungere il `OnBufferChanged` gestore dell'evento.  
  
    ```c#  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-cs[Numero&21; VSSDKMenuCommandTest](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs) ] 
     [!code-vb [VSSDKMenuCommandTest numero&21;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Aggiungere una dichiarazione per un `CommentsChanged` evento.  
  
    ```c#  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Creare un `Add()` metodo per aggiungere l'area di controllo.  
  
    ```c#  
    public void Add(SnapshotSpan span, string author, string text)  
    {  
        if (span.Length == 0)  
            throw new ArgumentOutOfRangeException("span");  
        if (author == null)  
            throw new ArgumentNullException("author");  
        if (text == null)  
            throw new ArgumentNullException("text");  
  
        //Create a comment adornment given the span, author and text.  
        CommentAdornment comment = new CommentAdornment(span, author, text);  
  
        //Add it to the list of comments.   
        this.comments.Add(comment);  
  
        //Raise the changed event.  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
        if (commentsChanged != null)  
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));  
    }  
  
    ```  
  
11. Aggiungere un `RemoveComments()` metodo.  
  
    ```c#  
    public void RemoveComments(SnapshotSpan span)  
    {  
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;  
  
        //Get a list of all the comments that are being kept   
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith.   
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
            {  
                //Raise the change event to delete this comment.   
                if (commentsChanged != null)  
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));  
            }  
            else  
                keptComments.Add(comment);  
        }  
  
        this.comments = keptComments;  
    }  
    ```  
  
12. Aggiungere un `GetComments()` metodo che restituisce tutti i commenti in un intervallo di snapshot specificato.  
  
    ```c#  
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)  
    {  
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();  
        foreach (CommentAdornment comment in this.comments)  
        {  
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))  
                overlappingComments.Add(comment);  
        }  
  
        return new Collection<CommentAdornment>(overlappingComments);  
    }  
    ```  
  
13. Aggiungere una classe denominata `CommentsChangedEventArgs`, come indicato di seguito.  
  
    ```c#  
    internal class CommentsChangedEventArgs : EventArgs  
    {  
        public readonly CommentAdornment CommentAdded;  
  
        public readonly CommentAdornment CommentRemoved;  
  
        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)  
        {  
            this.CommentAdded = added;  
            this.CommentRemoved = removed;  
        }  
    }  
    ```  
  
## <a name="managing-comment-adornments"></a>La gestione di aree di controllo di commento  
 La gestione dell'area di controllo commento Crea area di controllo e lo aggiunge al livello dell'area di controllo. È in ascolto per il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>gli eventi in modo che non possono spostare o eliminare l'area di controllo.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> È inoltre in ascolto per il `CommentsChanged` evento generato dal provider adornment commento quando i commenti vengono aggiunti o rimossi.  
  
1.  Aggiungere un file di classe al progetto CommentAdornmentTest e denominarla `CommentAdornmentManager`.  
  
2.  Aggiungere le istruzioni `using` riportate di seguito.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Aggiungere una classe denominata `CommentAdornmentManager`.  
  
    ```c#  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Aggiungere alcuni campi privati.  
  
    ```c#  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Aggiungere un costruttore che sottoscrive il gestore per il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>degli eventi e anche al `CommentsChanged` eventi.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> </xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> Il costruttore è privato perché il gestore viene creata un'istanza per il metodo statico `Create()` metodo.  
  
    ```c#  
    private CommentAdornmentManager(IWpfTextView view)  
    {  
        this.view = view;  
        this.view.LayoutChanged += OnLayoutChanged;  
        this.view.Closed += OnClosed;  
  
        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");  
  
        this.provider = CommentAdornmentProvider.Create(view);  
        this.provider.CommentsChanged += OnCommentsChanged;  
    }  
    ```  
  
6.  Aggiungere il `Create()` metodo che ottiene un provider o ne crea uno se necessario.  
  
    ```c#  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Aggiungere il `CommentsChanged` gestore.  
  
    ```c#  
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)  
    {  
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag).   
        if (e.CommentRemoved != null)  
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);  
  
        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout).   
        if (e.CommentAdded != null)  
            this.DrawComment(e.CommentAdded);  
    }  
    ```  
  
8.  Aggiungere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>gestore.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed>  
  
    ```c#  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Aggiungere il <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>gestore.</xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>  
  
    ```c#  
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)  
    {  
        //Get all of the comments that intersect any of the new or reformatted lines of text.  
        List<CommentAdornment> newComments = new List<CommentAdornment>();  
  
        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.    
        //Use the latter to find the comments that intersect the new or reformatted lines of text.   
        foreach (Span span in e.NewOrReformattedSpans)  
        {  
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));  
        }  
  
        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not.   
        //Sort the list and skip duplicates.  
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });  
  
        CommentAdornment lastComment = null;  
        foreach (CommentAdornment comment in newComments)  
        {  
            if (comment != lastComment)  
            {  
                lastComment = comment;  
                this.DrawComment(comment);  
            }  
        }  
    }  
    ```  
  
10. Aggiungere il metodo privato che disegna il commento.  
  
     [!code-cs[N.&35; VSSDKMenuCommandTest](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs) ] 
     [!code-vb [VSSDKMenuCommandTest n.&35;](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="using-the-menu-command-to-add-the-comment-adornment"></a>Utilizzo del comando di Menu per aggiungere l'area di controllo di commento  
 È possibile utilizzare il comando di menu per creare un'area di controllo di commento implementando il `MenuItemCallback` metodo del VSPackage.  
  
1.  Aggiungere i riferimenti seguenti al progetto MenuCommandTest:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Aprire il file AddAdornment.cs e aggiungere il codice seguente `using` istruzioni.  
  
    ```c#  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Eliminare il metodo ShowMessageBox() e aggiungere il seguente gestore del comando.  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Aggiungere codice per ottenere la visualizzazione attiva. È necessario ottenere il `SVsTextManager` della shell di Visual Studio per ottenere attivo `IVsTextView`.  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Se questa visualizzazione di testo è un'istanza di una visualizzazione di testo dell'editor, è possibile eseguirne il cast <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>dell'interfaccia e ottenere <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>e relativi associati <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> </xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> Utilizzare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>per chiamare il `Connector.Execute()` (metodo), che ottiene il provider dell'area di controllo di commento e aggiunge l'area di controllo.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Il gestore del comando dovrebbe essere simile al seguente:  
  
    ```c#  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
        IVsUserData userData = vTextView as IVsUserData;  
         if (userData == null)  
        {  
            Console.WriteLine("No text view is currently open");  
                            return;  
        }  
        IWpfTextViewHost viewHost;  
        object holder;  
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;  
        userData.GetData(ref guidViewHost, out holder);  
        viewHost = (IWpfTextViewHost)holder;  
        Connector.Execute(viewHost);  
    }  
    ```  
  
6.  Impostare il metodo AddAdornmentHandler come gestore per il comando AddAdornment nel costruttore AddAdornment.  
  
    ```c#  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1.  Compilare la soluzione e avviare il debug. L'istanza sperimentale dovrebbe apparire.  
  
2.  Creare un file di testo. Digitare un testo e quindi selezionarlo.  
  
3.  Nel **strumenti** menu, fare clic su **richiamare Adornment aggiungere**. Un fumetto deve essere visualizzato sul lato destro della finestra testo e deve contenere testo simile al testo seguente.  
  
     Nome utente  
  
     Fourscore...  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
