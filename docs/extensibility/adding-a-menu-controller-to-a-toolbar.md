---
title: "Aggiunta di un Controller di Menu per una barra degli strumenti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "barre degli strumenti [Visual Studio], aggiunta di controller di menu"
  - "menu, aggiunta di controller di menu in barre degli strumenti"
  - "controller di menu, aggiunta di barre degli strumenti"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# Aggiunta di un Controller di Menu per una barra degli strumenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata si basa sul [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) procedura dettagliata e viene illustrato come aggiungere un controller di menu per la finestra degli strumenti. I passaggi illustrati di seguito è possibile applicare anche alla barra degli strumenti creata nella [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md) procedura dettagliata.  
  
 Un controller di menu è un controllo di divisione. Il lato sinistro del controller di menu viene visualizzato il comando utilizzato per ultimo e può essere eseguito facendovi clic sopra. La parte destra del controller di menu è una freccia che, quando si fa clic, viene visualizzato l'elenco di comandi aggiuntivi. Quando si sceglie un comando nell'elenco, l'esecuzione del comando, e sostituisce il comando sul lato sinistro del controller di menu. In questo modo, il controller menu opera come un pulsante di comando che mostra sempre il comando utilizzato per ultimo da un elenco.  
  
 Controller di menu possono essere visualizzati nei menu ma vengono spesso usati nelle barre degli strumenti.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un Controller di Menu  
  
#### Per creare un controller di menu  
  
1.  Seguire le procedure descritte in [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md) per creare una finestra degli strumenti con una barra degli strumenti.  
  
2.  In TWTestCommandPackage.vsct, passare alla sezione simboli. Nell'elemento GuidSymbol denominato **guidTWTestCommandPackageCmdSet**, dichiarare il controller di menu, il gruppo di controller di menu e tre voci di menu.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  Nella sezione Menus, dopo l'ultima voce di menu, definire il controller di menu come menu.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Il `TextChanges` e `TextIsAnchorCommand` flag devono essere inclusi per consentire al controller di menu in modo da riflettere l'ultimo comando selezionato.  
  
4.  I gruppi di sezione, dopo l'ultima voce di gruppo, aggiungere il gruppo di controller di menu.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     Impostando il controller di menu come elemento padre, tutti i comandi in modalità di questo gruppo verranno visualizzato nel controller di menu. Il `priority` attributo viene omesso, che imposta il valore predefinito pari a 0, perché sarà l'unico gruppo nel controller di menu.  
  
5.  Nella sezione pulsanti, dopo l'ultima voce pulsante, aggiungere un elemento Button per ognuna delle voci di menu.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  A questo punto, è possibile esaminare il controller di menu. Compilare il progetto e avviare il debug. Dovrebbe essere l'istanza sperimentale.  
  
    1.  Nel **Vista o altre finestre** dal menu **degli strumenti di Test**.  
  
    2.  Il controller di menu viene visualizzato sulla barra degli strumenti nella finestra degli strumenti.  
  
    3.  Fare clic sulla freccia a destra del controller di menu per visualizzare i tre comandi possibili.  
  
     Si noti che quando si sceglie un comando, il titolo del controller di menu cambia per visualizzare il comando. Nella sezione successiva, si aggiungerà il codice per attivare i comandi seguenti.  
  
## Implementazione dei comandi di Menu Controller  
  
1.  In TWTestCommandPackageGuids.cs, aggiungere gli ID di comando per le tre voci di menu dopo l'ID di comando esistenti.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  In TWTestCommand.cs, aggiungere il codice seguente all'inizio della classe TWTestCommand.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  Nel costruttore TWTestCommand, dopo l'ultima chiamata per il `AddCommand` \(metodo\), aggiungere codice per inviare gli eventi per ogni comando tramite i gestori stesso.  
  
    ```c#  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  Aggiungere un gestore eventi alla classe TWTestCommand per contrassegnare il comando selezionato come selezionato.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  Aggiungere un gestore eventi che visualizza una finestra di messaggio quando l'utente seleziona un comando nel controller di menu:  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## Il Menu Controller di test  
  
1.  Compilare il progetto e avviare il debug. Dovrebbe essere l'istanza sperimentale.  
  
2.  Aprire il **degli strumenti di Test** sul **visualizzazione \/ altre finestre** menu.  
  
     Il controller di menu viene visualizzato nella barra degli strumenti nella finestra degli strumenti e Visualizza **MC Item 1**.  
  
3.  Fare clic sul pulsante di controller dal menu a sinistra della freccia.  
  
     Dovrebbe essere tre elementi, il primo dei quali è selezionato e include una casella di evidenziazione intorno relativa icona. Fare clic su **MC elemento 3**.  
  
     Viene visualizzata una finestra di dialogo con messaggio **selezionato controller Menu Item 3**. Si noti che il messaggio corrisponde al testo del pulsante controller menu. Visualizza il pulsante di menu controller **MC elemento 3**.  
  
## Vedere anche  
 [Aggiunta di una barra degli strumenti a una finestra degli strumenti](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [Aggiunta di una barra degli strumenti](../extensibility/adding-a-toolbar.md)