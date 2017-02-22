---
title: "Aggiunta di una finestra degli strumenti | Microsoft Docs"
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
  - "esercitazioni"
  - "finestre degli strumenti"
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 52
caps.handback.revision: 52
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiunta di una finestra degli strumenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata è illustrato come creare una finestra degli strumenti e integrarla con Visual Studio nei modi seguenti:  
  
-   Aggiungere un controllo alla finestra dello strumento.  
  
-   Aggiungere una barra degli strumenti a una finestra degli strumenti.  
  
-   Aggiungere un comando alla barra degli strumenti.  
  
-   Implementare i comandi.  
  
-   Impostare la posizione predefinita per la finestra degli strumenti.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di una finestra degli strumenti  
  
1.  Creare un progetto denominato **FirstToolWin** utilizzando il modello di progetto VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzata denominato **FirstToolWindow**.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Aggiungere un controllo alla finestra dello strumento  
  
1.  Rimuovere il controllo predefinito. Aprire FirstToolWindowControl.xaml ed eliminare il **Click Me\!** pulsante.  
  
2.  Nel **della casella degli strumenti**, espandere il **tutti i controlli WPF** sezione e trascinare il **elemento multimediale** controllo il **FirstToolWindowControl** form. Selezionare il controllo e il **proprietà** finestra, denominare l'elemento **mediaElement1**.  
  
## Aggiungere una barra degli strumenti per la finestra degli strumenti  
 Mediante l'aggiunta di una barra degli strumenti nel modo seguente, si garantisce che le sfumature e i colori sono coerenti con il resto dell'IDE.  
  
1.  In **Esplora**, aprire FirstToolWindowPackage.vsct. Il file vsct definisce gli elementi dell'interfaccia utente grafica nella finestra strumento utilizzando XML.  
  
2.  Nel `<Symbols>` sezione, trovare il `<GuidSymbol>` nodo il cui `name` attributo `guidFirstToolWindowPackageCmdSet`. Aggiungere i seguenti due `<IDSymbol>` elementi all'elenco di `<IDSymbol>` elementi in questo nodo per definire una barra degli strumenti e un gruppo della barra degli strumenti.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Sopra il `<Buttons>` sezione, creare un `<Menus>` sezione simile alla seguente:  
  
    ```xml  
    <Menus>  
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">  
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
            <Strings>  
                <ButtonText>Tool Window Toolbar</ButtonText>  
                <CommandName>Tool Window Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Esistono diversi tipi di menu. Questo menu è una barra degli strumenti in una finestra degli strumenti, definito dal relativo `type` attributo. Il `guid` e  `id` Impostazioni costituiscono l'ID completo della barra degli strumenti. In genere, il `<Parent>` di un menu è il gruppo che lo contiene. Tuttavia, una barra degli strumenti è definito come relativo elemento padre. Pertanto, viene utilizzato lo stesso identificatore per il `<Menu>` e `<Parent>` gli elementi. Il `priority` attributo è solo ' 0'.  
  
4.  Barre degli strumenti assomigliare agli elementi di menu in molti modi. Ad esempio, come i gruppi di comandi potrebbe dispone di un menu, barre degli strumenti può avere gruppi. \(Menu, i gruppi di comando sono separati da barre orizzontali. Sulla barra degli strumenti, i gruppi non sono separati da divisori visual.\)  
  
     Aggiungere un `<Groups>` sezione che contiene un `<Group>` elemento. Definisce il gruppo il cui ID è dichiarato nel `<Symbols>` sezione. Aggiungere il `<Groups>` sezione subito dopo il `<Menus>` sezione.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     Impostando l'elemento padre GUID e ID per il GUID e l'ID della barra degli strumenti, aggiungere il gruppo alla barra degli strumenti.  
  
## Aggiungere un comando alla barra degli strumenti  
 Aggiungere un comando alla barra degli strumenti, viene visualizzato come un pulsante.  
  
1.  Nel `<Symbols>` sezione, dichiarare i seguenti elementi IDSymbol subito dopo la barra degli strumenti e barra degli strumenti, le dichiarazioni di gruppo.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Aggiungere un elemento pulsante all'interno di `<Buttons>` sezione. Questo elemento verrà visualizzato sulla barra degli strumenti nella finestra degli strumenti, con un'icona di ricerca \(lente di ingrandimento\).  
  
    ```xml  
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">  
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <Strings>  
            <CommandName>cmdidWindowsMediaOpen</CommandName>  
            <ButtonText>Load File</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Aprire FirstToolWindowCommand.cs e aggiungere le righe seguenti nella classe subito dopo i campi esistenti.  
  
    ```c#  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     In questo modo i comandi disponibili nel codice.  
  
## Aggiungere una proprietà di MediaPlayer a FirstToolWindowControl  
 Dai gestori eventi per i controlli della barra degli strumenti, il codice deve essere in grado di accedere al controllo di Media Player, che è un elemento figlio della classe FirstToolWindowControl.  
  
 In **Esplora**, fare clic su FirstToolWindowControl.xaml, fare clic su **Visualizza codice**, e aggiungere il codice seguente alla classe FirstToolWindowControl.  
  
```c#  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## Creare un'istanza di finestra degli strumenti e barra degli strumenti  
 Aggiungere una barra degli strumenti e un comando di menu che richiama il **Apri** finestra di dialogo e riproduce il file multimediale selezionato.  
  
1.  Aprire FirstToolWindow.cs e aggiungere il codice seguente `using` istruzioni.  
  
    ```c#  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  All'interno della classe FirstToolWindow, aggiungere un riferimento al controllo FirstToolWindowControl pubblico.  
  
    ```c#  
    public FirstToolWindowControl control;  
    ```  
  
3.  Alla fine del costruttore, impostare questa variabile di controllo per il controllo appena creato.  
  
    ```c#  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Creare un'istanza la barra degli strumenti all'interno del costruttore.  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  Il costruttore FirstToolWindow a questo punto dovrebbe essere simile al seguente:  
  
    ```c#  
    public FirstToolWindow() : base(null)  
    {  
        this.Caption = "FirstToolWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
        control = new FirstToolWindowControl();  
        base.Content = control;  
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
            FirstToolWindowCommand.ToolbarID);  
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    }  
    ```  
  
6.  Aggiungere il comando di menu alla barra degli strumenti. Nella classe FirstToolWindowCommand.cs, aggiungere la seguente istruzione using  
  
    ```c#  
    using System.Windows.Forms;  
    ```  
  
7.  Nella classe FirstToolWindowCommand, aggiungere il codice seguente alla fine del metodo ShowToolWindow\(\). Il comando ButtonHandler verrà implementato nella sezione successiva.  
  
    ```c#  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### Per implementare un comando di menu nella finestra degli strumenti  
  
1.  Nella classe FirstToolWindowCommand, aggiungere un metodo ButtonHandler che richiama il **Apri** finestra di dialogo. Quando è stato selezionato un file, viene riprodotto il file multimediale.  
  
2.  Nella classe FirstToolWindowCommand, aggiungere un riferimento alla finestra FirstToolWindow che viene creato nel metodo FindToolWindow\(\) privato.  
  
    ```c#  
    private FirstToolWindow window;  
    ```  
  
3.  Modificare il metodo ShowToolWindow\(\) per impostare la finestra che è definito in precedenza \(in modo che il gestore del comando ButtonHandler può accedere al controllo di finestra. Ecco il metodo ShowToolWindow\(\) completo.  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
                            throw new NotSupportedException("Cannot create tool window");  
        }  
  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
         var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),  
            FirstToolWindowCommand.cmdidWindowsMediaOpen);  
        var menuItem = new MenuCommand(new EventHandler(  
            ButtonHandler), toolbarbtnCmdID);  
        mcs.AddCommand(menuItem);  
    }  
    ```  
  
4.  Aggiungere il metodo ButtonHandler. Crea un oggetto OpenFileDialog all'utente di specificare il file multimediale da riprodurre, quindi riproduce il file selezionato.  
  
    ```c#  
    private void ButtonHandler(object sender, EventArgs arguments)  
    {  
        OpenFileDialog openFileDialog = new OpenFileDialog();  
        DialogResult result = openFileDialog.ShowDialog();  
        if (result == DialogResult.OK)  
        {  
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);  
        }  
    }  
    ```  
  
## Impostare la posizione predefinita per la finestra degli strumenti  
 Successivamente, specificare un percorso predefinito nell'IDE per la finestra degli strumenti. Informazioni di configurazione per la finestra degli strumenti sono nel file FirstToolWindowPackage.cs.  
  
1.  In FirstToolWindowPackage.cs, trovare il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> attributo la `FirstToolWindowPackage` classe, che passa il tipo di FirstToolWindow al costruttore. Per specificare una posizione predefinita, è necessario aggiungere ulteriori parametri del costruttore nell'esempio seguente.  
  
    ```c#  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Il primo parametro denominato `Style` e il valore è `Tabbed`, il che significa che la finestra sarà una scheda in una finestra esistente. La posizione di ancoraggio è specificata per il `Window` parametro, n questo caso, il GUID del **Esplora soluzioni**.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sui tipi di finestre nell'IDE, vedere <xref:EnvDTE.vsWindowType>.  
  
## La finestra degli strumenti di test  
  
1.  Premere F5 per aprire una nuova istanza sperimentale di Visual Studio compilare.  
  
2.  Nel **visualizzazione** dal menu **altre finestre** e quindi fare clic su **prima finestra degli strumenti**.  
  
     Apre la finestra degli strumenti di media player nella stessa posizione **Esplora**. Se viene comunque visualizzato nella stessa posizione come prima, reimpostare il layout di finestra \(**finestra \/ Reimposta Layout finestra**\).  
  
3.  Fare clic sul pulsante \(con l'icona di ricerca\) nella finestra degli strumenti. Selezionare un file di audio o video supportati, ad esempio, C:\\windows\\media\\chimes.wav, quindi premere **aprire**.  
  
     Si dovrebbe ascoltare l'audio xilofono.  
  
## Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)