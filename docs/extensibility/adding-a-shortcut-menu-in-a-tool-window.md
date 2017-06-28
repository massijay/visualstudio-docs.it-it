---
title: Aggiunta di un Menu di scelta rapida in una finestra degli strumenti | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 37
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
ms.openlocfilehash: ab921bec73528be7207baebdf9cb31885e2253fd
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>Aggiunta di un Menu di scelta rapida in una finestra degli strumenti
Questa procedura dettagliata di inserire un menu di scelta rapida in una finestra degli strumenti. Menu di scelta rapida è un menu che viene visualizzato quando un utente fa un pulsante, una casella di testo o sfondo della finestra. Comandi del menu di scelta rapida si comportano come i comandi in altri menu e barre degli strumenti. Per supportare un menu di scelta rapida, specificarlo nel file vsct e visualizzarlo in risposta a destro del mouse.  
  
 Una finestra degli strumenti è costituito da un controllo utente WPF in una classe della finestra degli strumenti personalizzata che eredita da <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.</xref:Microsoft.VisualStudio.Shell.ToolWindowPane>  
  
 Questa procedura dettagliata viene illustrato come creare un menu di scelta rapida di un menu di Visual Studio, dichiarando le voci di menu file vsct, e quindi utilizzando Managed Package Framework di implementazione nella classe che definisce la finestra degli strumenti. Questo approccio facilita l'accesso ai comandi di Visual Studio, elementi dell'interfaccia utente e modello a oggetti di automazione.  
  
 In alternativa, se il menu di scelta rapida non accede a funzionalità di Visual Studio, è possibile utilizzare il <xref:System.Windows.FrameworkElement.ContextMenu%2A>proprietà di un elemento XAML nel controllo utente.</xref:System.Windows.FrameworkElement.ContextMenu%2A> Per ulteriori informazioni, vedere [ContextMenu](http://msdn.microsoft.com/Library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d).  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>Creazione del pacchetto di Menu di scelta rapida finestra dello strumento  
  
1.  Creare un progetto VSIX denominato `TWShortcutMenu` e aggiungere un modello di finestra strumento denominato **menu scelta rapida** a esso. Per ulteriori informazioni sulla creazione di una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Specifica il Menu di scelta rapida  
 Menu di scelta rapida, ad esempio quella illustrata in questa procedura dettagliata consente all'utente di selezionare da un elenco di colori utilizzati per riempire lo sfondo della finestra degli strumenti.  
  
1.  In ShortcutMenuPackage.vsct, trovare l'elemento GuidSymbol denominato guidShortcutMenuPackageCmdSet e dichiarare il menu di scelta rapida, il gruppo di menu di scelta rapida e le opzioni di menu. L'elemento GuidSymbol dovrebbe essere simile al seguente:  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2.  Prima dell'elemento di pulsanti, creare un elemento menu, quindi definire il menu di scelta rapida in essa contenuti.  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     Menu di scelta rapida non ha un padre perché non fa parte di un menu o una barra degli strumenti.  
  
3.  Creare un elemento di gruppi con un elemento di gruppo che contiene le voci di menu di scelta rapida e associare il gruppo di menu di scelta rapida.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  Nell'elemento pulsanti, definire i singoli comandi che verranno visualizzato il menu di scelta rapida. L'elemento pulsanti dovrebbe essere simile al seguente:  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5.  In ShortcutMenuPackageGuids.cs, aggiungere che le definizioni per il comando set GUID, il menu di scelta rapida e le voci di menu.  
  
    ```c#  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Questi sono gli stessi ID di comando che sono definiti nella sezione Symbols del file ShortcutMenuPackage.vsct. Il gruppo di contesto non è incluso in questo caso perché è necessario solo nel file vsct.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementazione di Menu di scelta rapida  
 In questa sezione implementa il menu di scelta rapida e i relativi comandi.  
  
1.  In ShortcutMenu.cs, la finestra degli strumenti è possibile ottenere il servizio di comando di menu, ma non il controllo che contiene. La procedura seguente viene illustrato come rendere il servizio di comando di menu disponibili per il controllo utente.  
  
2.  In ShortcutMenu.cs, aggiungere le seguenti istruzioni using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Eseguire l'override di metodo Initialize () della finestra degli strumenti per ottenere il servizio di comando di menu e aggiungere il controllo, passando il servizio di comando di menu per il costruttore:  
  
    ```c#  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  Nel costruttore della finestra strumento menu scelta rapida, rimuovere la riga che aggiunge il controllo. Il costruttore dovrebbe essere simile al seguente:  
  
    ```c#  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  Nel ShortcutMenuControl.xaml.cs, aggiungere un campo privato per il servizio di comando di menu e modificare il costruttore di controllo per rendere il servizio di comando di menu. Utilizzare quindi il servizio di comando di menu per aggiungere i comandi di menu di contesto. Il costruttore ShortcutMenuControl dovrebbe essere simile al seguente codice. Il gestore del comando verrà definito in un secondo momento.  
  
    ```c#  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  In ShortcutMenuControl.xaml, aggiungere una <xref:System.Windows.UIElement.MouseRightButtonDown>evento al livello superiore <xref:System.Windows.Controls.UserControl>elemento.</xref:System.Windows.Controls.UserControl> </xref:System.Windows.UIElement.MouseRightButtonDown> Il file XAML dovrebbe essere simile al seguente:  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7.  In ShortcutMenuControl.xaml.cs, aggiungere uno stub per il gestore dell'evento.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Aggiungere le seguenti istruzioni using al file stesso:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implementare il `MyToolWindowMouseRightButtonDown` evento come indicato di seguito.  
  
    ```c#  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Verrà creata una <xref:System.ComponentModel.Design.CommandID>oggetto per il menu di scelta rapida, identifica la posizione di clic del mouse e apre il menu di scelta rapida in tale percorso utilizzando il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> </xref:System.ComponentModel.Design.CommandID>  
  
10. Implementare il gestore del comando.  
  
    ```c#  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     In questo caso, un solo metodo gestisce gli eventi per tutte le voci di menu identificando il <xref:System.ComponentModel.Design.CommandID>e impostare il colore di sfondo di conseguenza.</xref:System.ComponentModel.Design.CommandID> Se le voci di menu conteneva comandi non correlati, si dovrebbero essere stati creati un gestore eventi separati per ogni comando.  
  
## <a name="testing-the-tool-window-features"></a>La funzionalità della finestra strumento di test  
  
1.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
2.  Nell'istanza sperimentale, fare clic su **vista o altre finestre**, quindi fare clic su **menu scelta rapida**. Questa operazione dovrebbe essere visualizzata la finestra degli strumenti.  
  
3.  Pulsante destro del mouse nel corpo della finestra degli strumenti. Verrà visualizzato un menu di scelta rapida che dispone di un elenco di colori.  
  
4.  Fare clic su un colore nel menu di scelta rapida. Modificare il colore di sfondo finestra dello strumento per il colore selezionato.  
  
## <a name="see-also"></a>Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Utilizzo e servizi](../extensibility/using-and-providing-services.md)