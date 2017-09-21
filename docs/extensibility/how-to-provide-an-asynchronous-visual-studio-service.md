---
title: "Procedura: fornire un servizio asincrono Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Procedura: fornire un servizio asincrono Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si desidera ottenere un servizio senza bloccare il thread dell'interfaccia utente, è necessario creare un servizio asincrono e caricare il pacchetto in un thread in background. A questo scopo è possibile utilizzare un <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anziché <xref:Microsoft.VisualStudio.Shell.Package>, aggiungere il servizio con metodi asincroni speciale del pacchetto asincrona  
  
 Per informazioni sulla fornitura di servizi di Visual Studio sincroni, vedere [Procedura: fornire un servizio](../extensibility/how-to-provide-a-service.md).  
  
## Implementazione di un servizio asincrono  
  
1.  Creare un progetto VSIX \(**File \/ nuovo \/ progetto \/ Visual c\# \/ Extensiblity \/ progetto VSIX**\). Denominare il progetto **TestAsync**.  
  
2.  Aggiungere un VSPackage al progetto. Selezionare il nodo del progetto nel **Esplora** e fare clic su **Aggiungi \/ nuovo elemento \/ elementi di Visual c\# \/ estendibilità \/ pacchetto di Visual Studio**. Nome del file **TestAsyncPackage.cs**.  
  
3.  In TestAsyncPackage.cs, modificare il pacchetto da cui ereditare AsyncPackage anziché pacchetto:  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Per implementare un servizio, è necessario creare tre tipi:  
  
    -   Un'interfaccia che descrive il servizio. Molte di queste interfacce sono vuoti, vale a dire non hanno alcun metodo.  
  
    -   Un'interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include metodi per l'implementazione.  
  
    -   Una classe che implementa l'interfaccia del servizio sia il servizio.  
  
5.  Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio. In questo esempio si aggiungerà solo il servizio al file di codice del pacchetto.  
  
6.  Aggiungere le seguenti istruzioni using al file del pacchetto:  
  
    ```c#  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Di seguito è l'implementazione del servizio asincrona. Si noti che è necessario impostare il provider del servizio asincrono anziché il provider del servizio sincrone nel costruttore:  
  
    ```  
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## La registrazione di un servizio  
 Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> per il pacchetto che fornisce il servizio. Vi sono due differenze la registrazione di un servizio sincrone da:  
  
-   Se si è il caricamento automatico il pacchetto, è necessario aggiungere il <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> valore BackgroundLoad all'attributo. Per ulteriori informazioni su VSPackages il caricamento automatico, vedere [Caricamento VS](../extensibility/loading-vspackages.md).  
  
-   È necessario aggiungere il **AllowsBackgroundLoading \= true** campo di <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Per ulteriori informazioni sui PackageRegistrationAttribute, vedere [Package VS della registrazione e annullamento della registrazione](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Di seguito è riportato un esempio di un AsyncPackage con una registrazione del servizio asincrona:  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## Aggiunta di un servizio  
  
1.  In TestAsyncPackage.cs, rimuovere il `Initialize()` ed eseguire l'override di `InitializeAsync()` metodo. Aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Di seguito è riportato un esempio dell'inizializzazione asincrona aggiunta di un servizio:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementare il metodo di callback come un metodo asincrono che crea e restituisce il servizio.  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## Utilizzo di un servizio  
 A questo punto è possibile ottenere il servizio e utilizzarne i metodi.  
  
1.  Vi mostreremo questa nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto che si desidera utilizzare il servizio.  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Non dimenticare di modificare *\< userpath \>* a un nome e il percorso appropriato nel computer in uso.  
  
2.  Compilare ed eseguire il codice. Quando viene visualizzata l'istanza sperimentale di Visual Studio, aprire una soluzione. In questo modo AsyncPackage per caricare automaticamente. Quando è stata eseguita l'inizializzatore, si deve trovare un file nel percorso specificato.  
  
## Utilizzo di un servizio asincrono in un gestore del comando  
 Di seguito è riportato un esempio di come utilizzare un servizio asincrono in un comando di menu. È possibile utilizzare la procedura qui illustrata per utilizzare il servizio in altri metodi non asincrona.  
  
1.  Aggiungere un comando di menu al progetto. \(Nel **Esplora**, selezionare il nodo del progetto, pulsante destro del mouse e selezionare **Aggiungi \/ nuovo elemento \/ Extensibility comando personalizzato**.\) Nome del file di comando **TestAsyncCommand.cs.**  
  
2.  Il modello di comando personalizzato aggiunge nuovamente il `Initialize()` metodo al file TestAsyncPackage.cs per inizializzare il comando. Nel metodo Initialize \(\), copiare la riga che inizializza il comando. Dovrebbe essere simile al seguente:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Spostare questa riga per il `InitializeAsync()` metodo nel file AsyncPackageForService.cs. Poiché si tratta di un'inizializzazione asincrona, è necessario passare al thread principale prima di inizializzare il comando usando <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Dovrebbe essere simile al seguente:  
  
    ```c#  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  Eliminare il `Initialize()` metodo.  
  
4.  Nel file TestAsyncCommand.cs, individuare il `MenuItemCallback()` metodo. Eliminare il corpo del metodo.  
  
5.  Aggiungere un tramite istruzione:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Aggiungere un metodo asincrono denominato `GetAsyncService()`, che ottiene il servizio e utilizza i metodi:  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Chiamare questo metodo dal `MenuItemCallback()` metodo:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Compilare la soluzione e avviare il debug. Quando viene visualizzata l'istanza sperimentale di Visual Studio, vedere il **strumenti** menu e cercare il **richiamare TestAsyncCommand** voce di menu. Quando viene selezionata, il TextWriterService scrive il file specificato. \(È necessario aprire una soluzione, poiché il comando inoltre richiamando il pacchetto da caricare.\)  
  
## Vedere anche  
 [Utilizzo e servizi](../extensibility/using-and-providing-services.md)