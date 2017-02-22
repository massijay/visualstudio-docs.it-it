---
title: "Creazione di un&#39;estensione con un comando di Menu | Microsoft Docs"
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
  - "scrivere un vspackage"
  - "package VS"
  - "esercitazioni"
  - "pacchetto di Visual studio"
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
caps.latest.revision: 56
caps.handback.revision: 56
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un&#39;estensione con un comando di Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata viene illustrato come creare un'estensione con un comando di menu che consente di avviare il blocco note.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un comando di Menu  
  
1.  Creare un progetto VSIX denominato **FirstMenuCommand**. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **FirstCommand**. Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c\# \/ Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **FirstCommand.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Verrà visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [L'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, aprire il  **Strumenti \/ estensioni e aggiornamenti** finestra. Verrà visualizzato il **FirstMenuCommand** estensione qui. \(Se si apre **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstMenuCommand**\).  
  
     Passare ora al **strumenti** menu nell'istanza sperimentale. Dovrebbe essere **richiamare FirstCommand** comando. A questo punto viene semplicemente visualizzata una finestra di messaggio che afferma "FirstCommandPackage all'interno di FirstMenuCommand.FirstCommand.MenuItemCallback\(\)". Vedremo come effettivamente avviare Blocco note di questo comando nella sezione successiva.  
  
## Modificare il gestore di comandi di Menu  
 Ora aggiornare il gestore del comando per avviare il blocco note.  
  
1.  Arrestare il debug e tornare all'istanza di lavoro di Visual Studio. Aprire il file FirstCommand.cs e aggiungere la seguente istruzione using:  
  
    ```c#  
    using System.Diagnostics;  
    ```  
  
2.  Individuare il costruttore FirstCommand privato. Questo è il comando è collegato al servizio di comando e viene specificato il gestore del comando. Modificare il nome del gestore comando per StartNotepad, come indicato di seguito:  
  
    ```c#  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Rimuovere il metodo MenuItemCallback e aggiungere un metodo StartNotepad che verrà semplicemente avviare Blocco note:  
  
    ```c#  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Provare ora a eseguire l'operazione. Quando si avvia il debug del progetto e fare clic su **Strumenti \/ richiamare FirstCommand**, si dovrebbe essere visualizzata un'istanza del blocco note.  
  
     È possibile utilizzare un'istanza di <xref:System.Diagnostics.Process> classe per l'esecuzione di qualsiasi file eseguibile, non solo il blocco note. Provare con calc.exe, ad esempio.  
  
## Pulizia ambiente sperimentale  
 Se si siano sviluppando più estensioni, o semplicemente esplorare i risultati con diverse versioni del codice dell'estensione, l'ambiente sperimentale potrebbe smettere di funzionare nel modo desiderato. In questo caso, è necessario eseguire lo script di reimpostazione. Viene chiamato **Reimposta istanza sperimentale di Visual Studio 2015**, e fornito come parte di Visual Studio SDK. Questo script rimuove tutti i riferimenti per le estensioni dell'ambiente sperimentale, in modo da iniziare da zero.  
  
 È possibile ottenere questo script in uno dei due modi:  
  
1.  Dal desktop, trovare **Reimposta istanza sperimentale di Visual Studio 2015**.  
  
2.  Dalla riga di comando, eseguire le operazioni seguenti:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## Distribuzione dell'estensione  
 Ora che avete l'estensione di uno strumento in esecuzione nel modo desiderato, è necessario preoccuparsi di condividerla con amici e colleghi. Che è facile, purché hanno installato Visual Studio 2015. È necessario effettuare è inviare file con estensione VSIX è stato compilato. \(Assicurarsi di compilare la soluzione in modalità di rilascio.\)  
  
 È possibile trovare il file con estensione VSIX per questa estensione nella directory bin FirstMenuCommand. In particolare, se che è stata compilata la configurazione di rilascio, sarà:  
  
 **\< directory del codice \> \\FirstMenuCommand\\FirstMenuCommand\\bin\\Release\\ FirstMenuCommand.vsix**  
  
 Per installare l'estensione, l'amico deve chiudere tutte le istanze aperte di Visual Studio, quindi fare doppio clic sul file con estensione VSIX, che visualizza il **programma di installazione di VSIX**. I file vengono copiati il **%LocalAppData%\\Microsoft\\VisualStudio\\14.0\\Extensions** directory.  
  
 Quando l'amico Visualizza nuovamente Visual Studio, sarà disponibile l'estensione FirstMenuCommand in **Strumenti \/ estensioni e aggiornamenti**. È possibile passare a **estensioni e aggiornamenti** per disinstallare o disabilitare l'estensione, troppo.  
  
## Passaggi successivi  
 Questa procedura dettagliata è stato illustrato solo una piccola parte delle quali è possibile eseguire con un'estensione di Visual Studio. Ecco un breve elenco di altre operazioni \(relativamente semplice\) con le estensioni di Visual Studio:  
  
1.  È possibile eseguire molte altre operazioni con un comando di menu semplice:  
  
    1.  Aggiungere un'icona personalizzata: [Aggiunta di icone ai comandi di Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Modificare il testo del comando di menu: [Modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Aggiungere un collegamento nel menu a un comando: [Scelte rapide da tastiera di associazione di voci di Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Aggiungere diversi tipi di comandi, menu e barre degli strumenti: [Estensione menu e comandi](../extensibility/extending-menus-and-commands.md)  
  
3.  Aggiungere finestre degli strumenti ed estendere le finestre degli strumenti di Visual Studio incorporate: [Estensione e personalizzazione di finestre degli strumenti](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Aggiungere altre funzionalità IntelliSense e i suggerimenti di codice agli editor di codice esistente: [Estensione dell'Editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Aggiungere l'estensione di pagine delle proprietà e le opzioni e impostazioni utente: [Estensione di proprietà e la finestra proprietà](../extensibility/extending-properties-and-the-property-window.md) e [Opzioni e impostazioni utente estensione](../extensibility/extending-user-settings-and-options.md)  
  
 Altri tipi di estensioni richiedono un po' più operazioni, ad esempio creare un nuovo tipo di progetto \([Estensione di progetti](../extensibility/extending-projects.md)\), creare un nuovo tipo di editor \([Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)\), o l'implementazione dell'estensione in una shell isolata: [Visual Studio isolato Shell](../extensibility/visual-studio-isolated-shell.md)