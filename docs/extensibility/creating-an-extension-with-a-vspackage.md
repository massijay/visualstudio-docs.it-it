---
title: "Creazione di un&#39;estensione con un VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione di un&#39;estensione con un VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata viene illustrato come creare un progetto VSIX e aggiungere un elemento di progetto VSPackage. Utilizzeremo il package VS per ottenere il servizio Shell dell'interfaccia utente per visualizzare una finestra di messaggio.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un VSPackage  
  
1.  Creare un progetto VSIX denominato **FirstPackage**. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di pacchetto di Visual Studio denominato **FirstPackage**. Nel **Esplora**, del mouse sul nodo del progetto e scegliere **Aggiungi \/ nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c\# \/ Extensibility** e selezionare **pacchetto Visual Studio**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **FirstPackage.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Verrà visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [L'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, aprire il **Strumenti \/ estensioni e aggiornamenti** finestra. Verrà visualizzato il **FirstPackage** estensione qui. \(Se si apre **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstPackage**\).  
  
## Caricamento di VSPackage  
 A questo punto l'estensione non viene caricato, poiché non c'è nulla che causa il caricamento. In genere, è possibile caricare un'estensione quando si interagisce con la relativa interfaccia utente \(facendo clic su un comando di menu, aprire una finestra degli strumenti\) oppure specificando che il VSPackage verrà caricato in un contesto dell'interfaccia utente specifico. Per ulteriori informazioni sul caricamento dei contesti di VSPackage e dell'interfaccia utente, vedere [Caricamento VS](../extensibility/loading-vspackages.md). Per questa procedura, mostreremo come caricare un VSPackage quando una soluzione è aperta.  
  
1.  Aprire il file FirstPackage.cs. Cerca la dichiarazione della classe FirstPackage. Sostituire gli attributi esistenti con i seguenti:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Aggiungere un messaggio che ci consente di sapere che VSPackage sia stato caricato. Si usa metodo Initialize \(\) del VSPackage a tale scopo, è possibile ottenere servizi di Visual Studio solo dopo aver posizionato il package VS. \(Per ulteriori informazioni su servizi, vedere [Procedura: ottenere un servizio](../Topic/How%20to:%20Get%20a%20Service.md).\) Sostituire il metodo Initialize \(\) di FirstPackage con il codice che ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, ottiene il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e chiama il relativo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> metodo.  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale.  
  
4.  Aprire una soluzione nell'istanza sperimentale. Verrà visualizzato un messaggio che afferma **Initialize \(\) all'interno del pacchetto prima**.