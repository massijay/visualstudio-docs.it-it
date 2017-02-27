---
title: "Estendere il filtro di Esplora soluzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Esplora soluzioni, estensione"
  - "estensibilità [Visual Studio], progetti e soluzioni"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Estendere il filtro di Esplora soluzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile estendere **Esplora** per mostrare o nascondere i file di diversi funzionalità di filtro. Ad esempio, è possibile creare un filtro che mostra solo classe factory file c\# il **Esplora**, come illustrato in questa procedura dettagliata.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Creare un progetto di pacchetto Visual Studio  
  
1.  Creare un progetto VSIX denominato `FileFilter`. Aggiungere un modello di elemento di comando personalizzato denominato **FileFilter**. Per altre informazioni, vedere [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Aggiungere un riferimento a `System.ComponentModel.Composition` e `Microsoft.VisualStudio.Utilities`.  
  
3.  Impostare il comando di menu venga visualizzato il **Esplora** sulla barra degli strumenti. Aprire il file FileFilterPackage.vsct.  
  
4.  Modifica il `<Button>` blocco per le operazioni seguenti:  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### Aggiornare il File manifesto  
  
1.  Nel file source.extension.vsixmanifest, aggiungere un asset che è un componente MEF.  
  
2.  Nel **asset** scheda, scegliere il **nuovo** pulsante.  
  
3.  Nel **tipo** scegliere **Microsoft.VisualStudio.MefComponent**.  
  
4.  Nel **origine** selezionare **un progetto nella soluzione corrente**.  
  
5.  Nel **progetto** selezionare **FileFilter**, quindi scegliere il **OK** pulsante.  
  
### Aggiungere il codice di filtro  
  
1.  Aggiungere alcuni GUID per il file FileFilterPackageGuids.cs:  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Aggiungere un file di classe al progetto FileFilter denominato FileNameFilter.cs.  
  
3.  Sostituire con il codice seguente alla classe vuota e lo spazio dei nomi vuoto.  
  
     Il `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` accetta la raccolta che contiene la radice della soluzione \(`rootItems`\) e restituisce la raccolta di elementi da includere nel filtro.  
  
     Il `ShouldIncludeInFilter` metodo filtra gli elementi di **Esplora** gerarchia in base a condizione che si specifica.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Composition;  
    using System.Text.RegularExpressions;  
    using System.Threading.Tasks;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
  
    namespace FileFilter  
    {  
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component  
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]  
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider  
        {  
            SVsServiceProvider svcProvider;  
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
            // Constructor required for MEF composition  
            [ImportingConstructor]  
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)  
            {  
                this.svcProvider = serviceProvider;  
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
            }  
  
            // Returns an instance of Create filter class.  
            protected override HierarchyTreeFilter CreateFilter()  
            {  
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);  
            }  
  
            // Regex pattern for CSharp factory classes  
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";  
  
            // Implementation of file filtering  
            private sealed class FileNameFilter : HierarchyTreeFilter  
            {  
                private readonly Regex regexp;  
                private readonly IServiceProvider svcProvider;  
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;  
  
                public FileNameFilter(  
                    IServiceProvider serviceProvider,  
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,  
                    string fileNamePattern)  
                {  
                    this.svcProvider = serviceProvider;  
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;  
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);  
                }  
  
                // Gets the items to be included from this filter provider.   
                // rootItems is a collection that contains the root of your solution  
                // Returns a collection of items to be included as part of the filter  
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)  
                {  
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);  
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;  
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(  
                                        root.HierarchyIdentity.NestedHierarchy,  
                                        CancellationToken);  
  
                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(  
                        sourceItems,  
                        ShouldIncludeInFilter,  
                        CancellationToken);  
                    return includedItems;  
                }  
  
                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>  
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)  
                {  
                    if (hierarchyItem == null)  
                    {  
                        return false;  
                    }  
                    return this.regexp.IsMatch(hierarchyItem.Text);  
                }  
            }  
        }  
    }  
  
    ```  
  
4.  In FileFilter.cs, rimuovere il codice di posizionamento e la gestione di comando dal costruttore FileFilter. Il risultato dovrebbe essere simile al seguente:  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Rimuovere anche il metodo ShowMessageBox\(\).  
  
5.  In FileFilterPackage, cs, sostituire il codice nel metodo Initialize \(\) con il codice seguente:  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### Test del codice  
  
1.  Compilare ed eseguire il progetto. Verrà visualizzata una seconda istanza di Visual Studio. Si tratta l'istanza sperimentale.  
  
2.  Nell'istanza sperimentale di Visual Studio, aprire un progetto c\#.  
  
3.  Cercare il pulsante che nella barra degli strumenti Esplora soluzioni è stato aggiunto. Deve essere il quarto pulsante da sinistra.  
  
4.  Quando si fa clic sul pulsante, tutti i file devono essere filtrati e dovrebbe essere "tutti gli elementi sono stati filtrati dalla visualizzazione". in Esplora soluzioni.