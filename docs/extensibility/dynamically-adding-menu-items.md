---
title: "Aggiunta dinamica di voci di Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "voci di menu, aggiunta dinamica"
  - "menu, aggiunta di elementi dinamici"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# Aggiunta dinamica di voci di Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile aggiungere voci di menu in fase di esecuzione, specificando il `DynamicItemStart` comando flag in una definizione del pulsante segnaposto nel file di comando\-tabella \(vsct\) di Visual Studio, quindi definire \(nel codice\) il numero del menu di elementi da visualizzare e i comandi di gestione. Quando viene caricato il pacchetto Visual Studio, il segnaposto viene sostituito con le voci di menu dinamico.  
  
 Visual Studio utilizza elenchi dinamici nel **usati più di recente** elenco \(MRU\), che visualizza i nomi dei documenti aperti di recente, e **Windows** elenco, che visualizza i nomi di finestre attualmente aperte. Il `DynamicItemStart` flag in una definizione di comando specifica che il comando è un segnaposto finché non viene aperto il VSPackage. Quando viene aperto il package VS, il segnaposto viene sostituito con 0 o più comandi che vengono creati in fase di esecuzione e aggiunto all'elenco dinamico. Potrebbe non essere in grado di visualizzare la posizione nel menu in cui viene visualizzato l'elenco dinamico finché non viene aperto il VSPackage. Per popolare l'elenco dinamico, Visual Studio chiede VSPackage per cercare un comando con un ID i cui caratteri prima sono gli stessi ID del segnaposto. Quando Visual Studio rileva che un comando corrispondente, aggiunge il nome del comando per l'elenco dinamico. Quindi incrementa l'ID e cerca un altro comando corrispondente da aggiungere all'elenco dinamico fino a quando non sono disponibili i comandi non più dinamici.  
  
 Questa procedura dettagliata viene illustrato come impostare il progetto di avvio in una soluzione di Visual Studio con un comando per il **Esplora** sulla barra degli strumenti. Utilizza un controller di menu che dispone di un elenco a discesa dinamico dei progetti nella soluzione attiva. Per evitare che questo comando quando nessuna soluzione è aperta o quando la soluzione aperta ha un solo progetto, il VSPackage verrà caricato solo quando una soluzione con più progetti.  
  
 Per ulteriori informazioni sui file. vsct, vedere [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Creazione di un'estensione con un comando di Menu  
  
1.  Creare un progetto VSIX denominato `DynamicMenuItems`.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato e denominarlo **DynamicMenu**. Per altre informazioni, vedere [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## Impostazione degli elementi nel file. vsct  
 Per creare un controller di menu con gli elementi di menu dinamico su una barra degli strumenti, specificare i seguenti elementi:  
  
-   Due gruppi, uno che contiene il controller di menu e l'altro contenente le voci di menu a discesa di comando  
  
-   Elemento di un menu di tipo `MenuController`  
  
-   Due pulsanti, uno che funge da segnaposto per le voci di menu e un altro che fornisce l'icona e la descrizione comando sulla barra degli strumenti.  
  
1.  In DynamicMenuPackage.vsct, definire gli ID di comando. Passare alla sezione simboli e sostituire gli elementi IDSymbol di **guidDynamicMenuPackageCmdSet** GuidSymbol blocco. È necessario definire gli elementi IDSymbol per i due gruppi, il controller di menu, il comando segnaposto e il comando di ancoraggio.  
  
    ```c#  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  Nella sezione gruppi di eliminare i gruppi esistenti e aggiungere i due gruppi che appena definito:  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     Aggiungere il MenuController. Impostare il flag di comando DynamicVisibility, poiché non è sempre visibile. Non viene visualizzato il ButtonText.  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  Aggiungere due pulsanti, uno come segnaposto per le voci di menu dinamico e uno come ancoraggio per il MenuController.  
  
     L'elemento padre del pulsante segnaposto è il **MyMenuControllerGroup**. Aggiungere i flag di comando DynamicItemStart, DynamicVisibility e testoConsente di modificare il pulsante di segnaposto. Non viene visualizzato il ButtonText.  
  
     Il pulsante di ancoraggio contiene l'icona e testo della descrizione comandi. L'elemento padre del pulsante ancoraggio è anche il **MyMenuControllerGroup**. Aggiungere il flag di comando NoShowOnMenuController per assicurarsi che il pulsante non compare effettivamente nel menu a discesa di controller e il flag di comando FixMenuController per renderlo permanente ancoraggio.  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  Aggiungere un'icona per il progetto \(nella cartella Resources\) e quindi aggiungere il riferimento a esso nel file vsct. In questa procedura dettagliata, utilizziamo l'icona di frecce che è incluso nel modello di progetto.  
  
5.  Aggiungere una sezione VisibilityConstraints all'esterno della sezione comandi appena prima della sezione di simboli. \(È possibile ottenere un avviso se aggiunti dopo i simboli\). Questa sezione garantisce che il controller di menu viene visualizzata solo quando viene caricata una soluzione con più progetti.  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## Implementazione del comando di menu dinamico  
 Creare una classe di comando di menu dinamico che eredita da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>. In questa implementazione, il costruttore viene specificato un predicato da utilizzare per la corrispondenza di comandi. È necessario eseguire l'override di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodo da utilizzare il predicato per impostare il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> proprietà, che identifica il comando da richiamare.  
  
1.  Creare un nuovo file classe c\# denominato DynamicItemMenuCommand.cs e aggiungere una classe denominata **DynamicItemMenuCommand** che eredita da <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  Aggiungere le seguenti istruzioni using:  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Aggiungere un campo privato per archiviare il predicato di corrispondenza:  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  Aggiungere un costruttore che eredita il <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> costruttore e specifica un gestore del comando e un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> gestore. Aggiungere un predicato per la corrispondenza il comando:  
  
    ```c#  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  Eseguire l'override di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> metodo in modo che venga chiamato le corrispondenze predicato e imposta la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> proprietà:  
  
    ```c#  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## Aggiunge il comando  
 Il costruttore DynamicMenu è in cui impostare i comandi di menu, menu dinamici e voci di menu.  
  
1.  In DynamicMenuPackageGuids.cs, aggiungere il GUID del set di comandi e l'ID di comando:  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  Nel file DynamicMenu.cs, aggiungere le seguenti istruzioni using:  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Aggiungere un campo privato nella classe DynamicMenu **dte2**.  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  Aggiungere un campo privato rootItemId:  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  Nel costruttore DynamicMenu, aggiungere il comando di menu. Nella sezione successiva verrà definiamo il gestore del comando, il `BeforeQueryStatus` gestore dell'evento e il predicato di corrispondenza.  
  
    ```c#  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## Implementazione di gestori  
 Per implementare le voci di menu dinamico in un controller di menu, è necessario gestire il comando quando si fa clic su un elemento dinamico. È inoltre necessario implementare la logica che imposta lo stato della voce di menu. Aggiungere i gestori per la classe DynamicMenu.  
  
1.  Per implementare il **Imposta progetto di avvio** comando, aggiungere il **OnInvokedDynamicItem** gestore dell'evento. Il progetto il cui nome corrisponde al testo del comando che è stato richiamato e lo imposta come progetto di avvio impostando il relativo percorso assoluto in cerca di <xref:EnvDTE.SolutionBuild.StartupProjects%2A> proprietà.  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  Aggiungere il `OnBeforeQueryStatusDynamicItem` gestore dell'evento. Questo è il gestore chiamato prima che un `QueryStatus` evento. Determina se la voce di menu è un elemento "reale", vale a dire, non l'elemento segnaposto, e se l'elemento è già selezionato \(vale a dire che il progetto è già impostato come progetto di avvio\).  
  
    ```c#  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## Implementare il predicato di corrispondenza ID di comando  
  
1.  A questo punto, implementare il predicato di corrispondenza. È necessario stabilire due cose: innanzitutto, se l'ID di comando è valido \(è maggiore o uguale all'ID di comando dichiarato\) e il secondo, se specifica un progetto possibili \(è inferiore al numero di progetti nella soluzione\).  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## Impostazione di caricare solo quando una soluzione con più progetti VSPackage  
 Poiché il **Imposta progetto di avvio** comando non ha senso solo se la soluzione attiva dispone di più di un progetto, è possibile impostare il pacchetto Visual Studio al caricamento automatico solo in quel caso. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> con il contesto dell'interfaccia utente <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>. Nel file DynamicMenuPackage.cs aggiungere gli attributi seguenti alla classe DynamicMenuPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## Il comando Imposta progetto di avvio di test  
 È ora possibile testare il codice.  
  
1.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe apparire.  
  
2.  Nell'istanza sperimentale, aprire una soluzione che contiene più di un progetto.  
  
     Si noterà sull'icona della freccia di **Esplora** sulla barra degli strumenti. Quando si espande, dovrebbero apparire voci di menu che rappresentano i diversi progetti nella soluzione.  
  
3.  Quando si seleziona uno dei progetti, diventa il progetto di avvio.  
  
4.  Quando si chiude la soluzione, o aprire una soluzione che contiene un solo progetto, l'icona della barra degli strumenti deve essere nascosto.  
  
## Vedere anche  
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)