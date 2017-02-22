---
title: "Aggiunta di una pi&#249; recente di elenco a un sottomenu usati | Microsoft Docs"
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
  - "MRU (elenchi)"
  - "menu, Creazione elenco"
  - "utilizzati più di recente"
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 46
caps.handback.revision: 46
ms.author: "gregvanl"
manager: "ghogen"
---
# Aggiunta di una pi&#249; recente di elenco a un sottomenu usati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata si basa su dimostrazioni in [Aggiunta di un sottomenu a un Menu](../extensibility/adding-a-submenu-to-a-menu.md), e viene illustrato come aggiungere un elenco dinamico di un sottomenu. L'elenco dinamico costituisce la base per la creazione di un elenco usati \(recente\).  
  
 Un elenco di menu dinamico inizia con un segnaposto in un menu. Ogni volta che viene mostrato il menu, l'ambiente di sviluppo integrato \(IDE\) di Visual Studio chiede VSPackage per tutti i comandi che devono essere visualizzati nel segnaposto. Un elenco dinamico può verificarsi in qualsiasi punto in un menu. Tuttavia, gli elenchi dinamici vengono in genere archiviati e visualizzati da soli sottomenu o al fondo del menu. Utilizzando questi modelli di progettazione, si attiva l'elenco dinamico di comandi per espandere e comprimere senza modificare la posizione di altri comandi del menu. In questa procedura dettagliata, l'elenco dinamico di recente viene visualizzato nella parte inferiore di un sottomenu esistente, separato dal resto del sottomenu da una riga.  
  
 Tecnicamente, un elenco dinamico può anche essere applicato a una barra degli strumenti. Tuttavia, che l'utilizzo è sconsigliata perché una barra degli strumenti deve rimanere invariato, a meno che l'utente accetta i passaggi dettagliati per modificarlo.  
  
 Questa procedura dettagliata crea un elenco di quattro elementi che modificarne l'ordine ogni volta che una di esse è selezionata \(l'elemento selezionato si sposta all'inizio dell'elenco\).  
  
 Per ulteriori informazioni sui menu e file. vsct, vedere [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Creazione di un'estensione  
  
-   Seguire le procedure descritte in [Aggiunta di un sottomenu a un Menu](../extensibility/adding-a-submenu-to-a-menu.md) per creare il sottomenu che viene modificato nelle procedure seguenti.  
  
 Le procedure descritte in questa procedura dettagliata si presuppongono che il nome del VSPackage sia `TopLevelMenu`, ovvero il nome utilizzato in [Aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## Creazione di un comando di elenco elemento dinamico  
  
1.  Aprire TestCommandPackage.vsct.  
  
2.  Nel `Symbols` nella sezione di `GuidSymbol` nodo denominato guidTestCommandPackageCmdSet, aggiungere il simbolo per il `MRUListGroup` gruppo e `cmdidMRUList` comando, come indicato di seguito.  
  
    ```c#  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3.  Nel `Groups` sezione, aggiungere il gruppo dichiarato dopo le voci di gruppo esistente.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4.  Nel `Buttons` sezione, aggiungere un nodo per rappresentare il comando appena dichiarato, dopo i movimenti pulsante esistente.  
  
    ```c#  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     Il `DynamicItemStart` flag consente il comando deve essere generato in modo dinamico.  
  
5.  Compilare il progetto e avviare il debug per testare la visualizzazione del nuovo comando.  
  
     Nel **TestMenu** menu, fare clic su nuovo sottomenu, **sottomenu**, per visualizzare il nuovo comando **MRU segnaposto**. Dopo aver implementato un elenco dinamico di comandi nella procedura successiva, questa etichetta comando verrà sostituita da tale elenco ogni volta che viene aperto il sottomenu.  
  
## La compilazione di tale elenco  
  
1.  In TestCommandPackageGuids.cs, aggiungere le righe seguenti dopo l'ID di comando esistenti nel `TestCommandPackageGuids` definizione della classe.  
  
    ```c#  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2.  In TestCommand.cs aggiungere la seguente istruzione using.  
  
    ```c#  
    using System.Collections;  
    ```  
  
3.  Aggiungere il codice seguente nel costruttore TestCommand dopo l'ultima chiamata AddCommand. Il `InitMRUMenu` verranno definiti in un secondo momento  
  
    ```c#  
    this.InitMRUMenu(commandService);  
    ```  
  
4.  Aggiungere il codice seguente alla classe TestCommand. Questo codice inizializza l'elenco di stringhe che rappresentano gli elementi da visualizzare nell'elenco dei file più recenti.  
  
    ```c#  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5.  Dopo il `InitializeMRUList` \(metodo\), aggiungere il `InitMRUMenu` metodo. Consente di inizializzare i comandi di menu dell'elenco dei file più recenti.  
  
    ```c#  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     È necessario creare un oggetto comando di menu per tutti gli elementi possibili in tale elenco. Le chiamate a IDE il `OnMRUQueryStatus` metodo per ogni elemento nell'elenco dei file più recenti fino a quando non sono presenti più voci. Nel codice gestito, l'unico modo per l'IDE di sapere che non sono presenti più voci consiste nel creare innanzitutto tutti gli elementi possibili. Se si desidera, è possibile contrassegnare innanzitutto elementi aggiuntivi come non visibili al utilizzando `mc.Visible = false;` dopo aver creato il comando di menu. Questi elementi possono quindi essere visualizzati in un secondo momento utilizzando `mc.Visible = true;` nel `OnMRUQueryStatus` metodo.  
  
6.  Dopo il `InitMRUMenu` \(metodo\), aggiungere il codice seguente `OnMRUQueryStatus` metodo. Questo è il gestore che imposta il testo per ogni elemento di recente.  
  
    ```c#  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7.  Dopo il `OnMRUQueryStatus` \(metodo\), aggiungere il codice seguente `OnMRUExec` metodo. Questo è il gestore per la selezione di un elemento di recente. Questo metodo consente di spostare l'elemento selezionato nella parte superiore dell'elenco e quindi Visualizza l'elemento selezionato in una finestra di messaggio.  
  
    ```c#  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## TALE elenco di test  
  
#### Per testare l'elenco di menu MRU  
  
1.  Compilare il progetto e avviare il debug  
  
2.  Nel **TestMenu** menu, fare clic su **richiamare TestCommand**. Verrà visualizzata una finestra di messaggio che indica che il comando è stato selezionato.  
  
    > [!NOTE]
    >  Questo passaggio è necessario forzare il package VS per caricare e visualizzare correttamente tale elenco. Se si ignora questo passaggio, tale elenco non viene visualizzato.  
  
3.  Nel **dal Menu Test** menu, fare clic su **sottomenu**. Viene visualizzato un elenco di quattro elementi alla fine del sottomenu, di sotto di un separatore. Quando fa clic su **elemento 3**, una finestra di messaggio deve essere visualizzata e visualizzare il testo "Selected Item 3". \(Se non viene visualizzato l'elenco di quattro elementi, assicurarsi di aver seguito le istruzioni nel passaggio precedente.\)  
  
4.  Aprire di nuovo il sottomenu. Si noti che **elemento 3** è ora nella parte superiore dell'elenco e gli altri elementi sono stati inseriti una posizione verso il basso. Fare clic su **elemento 3** nuovamente e si noti che la finestra di messaggio viene visualizzato "elemento 3", che indica che il testo è stato spostato correttamente nella nuova posizione con l'etichetta del comando selezionato.  
  
## Vedere anche  
 [Aggiunta dinamica di voci di Menu](../extensibility/dynamically-adding-menu-items.md)