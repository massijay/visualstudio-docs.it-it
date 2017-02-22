---
title: "Esposizione di propriet&#224; nella finestra propriet&#224; | Microsoft Docs"
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
  - "proprietà [Visual Studio SDK], esposizione nel Visualizzatore proprietà"
  - "proprietà [Visual Studio SDK]"
  - "Visualizzatore proprietà, esposizione di proprietà"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
caps.handback.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
---
# Esposizione di propriet&#224; nella finestra propriet&#224;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata espone le proprietà pubbliche di un oggetto per il **proprietà** finestra. Le modifiche apportate a queste proprietà vengono riflesse nel **proprietà** finestra.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Esposizione di proprietà nella finestra proprietà  
 In questa sezione, si crea una finestra degli strumenti e visualizzare le proprietà pubbliche dell'oggetto nel riquadro finestra associata la **proprietà** finestra.  
  
#### Per esporre le proprietà nella finestra proprietà  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene le risorse di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyObjectPropertiesExtension`. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  Aggiungere una finestra degli strumenti aggiungendo un modello di elemento della finestra degli strumenti personalizzata denominato `MyToolWindow`. Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, visitare **elementi Visual c\# \/ Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **nome** campo nella parte inferiore della finestra di dialogo, modificare il nome di file in `MyToolWindow.cs`. Per ulteriori informazioni su come creare una finestra degli strumenti, vedere [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Aprire MyToolWindow.cs e aggiungere la seguente istruzione using:  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  A questo punto aggiungere i campi seguenti per la `MyToolWindow` classe.  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Aggiungere il codice seguente alla classe MyToolWindow.  
  
    ```c#  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     Il `TrackSelection` utilizza proprietà `GetService` per ottenere un `STrackSelection` servizio, che fornisce un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia. Il `OnToolWindowCreated` gestore dell'evento e `SelectList` metodo contribuiscono a creare un elenco degli oggetti selezionati che contiene solo il riquadro oggetto finestra stessa. Il `UpdateSelection` metodo indica il **proprietà** finestra per visualizzare le proprietà pubbliche del riquadro strumenti della finestra.  
  
6.  Compilare il progetto e avviare il debug. L'istanza sperimentale di Visual Studio dovrebbe apparire.  
  
7.  Se il **proprietà** finestra non è visibile, premere F4 per aprirla.  
  
8.  Aprire il **MyToolWindow** finestra. È possibile trovarlo in **Vista o altre finestre**.  
  
     Verrà visualizzata la finestra e le proprietà pubbliche della finestra vengono visualizzati nel **proprietà** finestra.  
  
9. Modifica il **didascalia** proprietà il **proprietà** finestra **le proprietà dell'oggetto My**.  
  
     La didascalia della finestra MyToolWindow cambia di conseguenza.  
  
## Esposizione di proprietà della finestra dello strumento  
 In questa sezione, aggiungere una finestra degli strumenti e le proprietà corrispondenti. Le modifiche apportate alle proprietà vengono riflesse nel **proprietà** finestra.  
  
#### Per esporre le proprietà della finestra dello strumento  
  
1.  Aprire MyToolWindow.cs e aggiungere la proprietà booleana pubblica IsChecked alla classe MyToolWindow.  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Questa proprietà ottiene lo stato dalla casella di controllo WPF che si creerà più avanti.  
  
2.  Aprire MyToolWindowControl.xaml.cs e sostituire il costruttore MyToolWindowControl con il codice seguente.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     In questo modo `MyToolWindowControl` l'accesso alla `MyToolWindow` riquadro.  
  
3.  In MyToolWindow.cs, modificare il `MyToolWindow` costruttore come indicato di seguito:  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Passare alla visualizzazione progettazione di MyToolWindowControl.  
  
5.  Eliminare il pulsante e aggiungere una casella di controllo dal **della casella degli strumenti** all'angolo superiore sinistro.  
  
6.  Aggiungere gli eventi Checked e Unchecked. Selezionare la casella di controllo nella visualizzazione progettazione. Nel **proprietà** finestra, fare clic sul pulsante di gestori eventi \(nella parte superiore destra del **proprietà** finestra\). Trovare **Checked** e il tipo **checkbox\_Checked** nella casella di testo, quindi individuare **Unchecked** e il tipo **checkbox\_Unchecked** nella casella di testo.  
  
7.  Aggiungere i gestori di eventi della casella di controllo:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Compilare il progetto e avviare il debug.  
  
9. Nell'istanza sperimentale, aprire il **MyToolWindow** finestra.  
  
     Cercare le proprietà della finestra nel **proprietà** finestra. Il **IsChecked** proprietà visualizzata nella parte inferiore della finestra, sotto il **proprietà My** categoria.  
  
10. Selezionare la casella di controllo nella **MyToolWindow** finestra.**IsChecked** nel **proprietà** finestra diventa **True**. Deselezionare la casella di controllo di **MyToolWindow** finestra.**IsChecked** nel **proprietà** finestra diventa **False**. Modificare il valore di **IsChecked** nel **proprietà** finestra. La casella di controllo di **MyToolWindow** finestra cambia in base al nuovo valore.  
  
    > [!NOTE]
    >  Se è necessario eliminare l'oggetto che viene visualizzato nel **proprietà** finestra, chiamata `OnSelectChange` con un `null` contenitore selezione prima. Dopo avere eliminato la proprietà o l'oggetto, è possibile modificare in un contenitore di selezione che sono stati aggiornati <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> e <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> sono elencati.  
  
## Modifica degli elenchi di selezione  
 In questa sezione, aggiungere un elenco di selezione per una classe di proprietà di base e utilizzare l'interfaccia della finestra dello strumento per scegliere l'elenco di selezione da visualizzare.  
  
#### Per modificare gli elenchi di selezione  
  
1.  Aprire MyToolWindow.cs e aggiungere una classe pubblica denominata `Simple`.  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Aggiungere una proprietà SimpleObject per la classe MyToolWindow, oltre a due metodi per passare il **proprietà** selezione della finestra tra il riquadro della finestra e `Simple` oggetto.  
  
    ```c#  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  In MyToolWindowControl.cs, sostituire i gestori di casella di controllo con le righe di codice:  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Compilare il progetto e avviare il debug.  
  
5.  Nell'istanza sperimentale, aprire il **MyToolWindow** finestra.  
  
6.  Selezionare la casella di controllo di **MyToolWindow** finestra. Il **proprietà** finestra viene visualizzato il `Simple` proprietà dell'oggetto **SomeText** e **ReadOnly**. Deselezionare la casella di controllo. Le proprietà pubbliche della finestra vengono visualizzati nel **proprietà** finestra.  
  
    > [!NOTE]
    >  Il nome visualizzato del **SomeText** è **testo My**.  
  
## Procedura consigliata  
 In questa procedura dettagliata, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene implementato in modo che la raccolta di oggetti selezionabili e la raccolta di oggetti selezionati sono della stessa raccolta. Solo l'oggetto selezionato viene visualizzato nell'elenco Visualizzatore proprietà. Per un'implementazione di ISelectionContainer più completa, vedere gli esempi Reference.ToolWindow.  
  
 Le finestre di Visual Studio vengono mantenute tra le sessioni di Visual Studio. Per ulteriori informazioni sulla persistenza dello stato della finestra dello strumento, vedere <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Vedere anche  
 [Estensione di proprietà e la finestra proprietà](../extensibility/extending-properties-and-the-property-window.md)