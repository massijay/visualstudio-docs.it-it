---
title: "Procedura: fornire un servizio | Microsoft Docs"
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
  - "servizi, che forniscono"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: fornire un servizio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un VSPackage può fornire servizi che possono utilizzare altri VSPackage. Per fornire un servizio, un VSPackage deve registrare il servizio con Visual Studio e aggiungere il servizio.  
  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe implementa sia <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> e <xref:System.ComponentModel.Design.IServiceContainer>.<xref:System.ComponentModel.Design.IServiceContainer> contiene metodi di callback che forniscono servizi su richiesta.  
  
 Per ulteriori informazioni sui servizi, vedere [Funzionalità fondamentali del servizio](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Quando un VSPackage sta per essere scaricato, Visual Studio attende finché tutte le richieste per i servizi che fornisce un VSPackage sono state recapitate. Non consente nuove richieste per tali servizi. Non è necessario chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodo revocare un servizio durante lo scaricamento.  
  
#### Implementazione di un servizio  
  
1.  Creare un progetto VSIX \(**File \/ nuovo \/ progetto \/ Visual c\# \/ Extensiblity \/ progetto VSIX**\).  
  
2.  Aggiungere un VSPackage al progetto. Selezionare il nodo del progetto nel **Esplora** e fare clic su **Aggiungi \/ nuovo elemento \/ elementi di Visual c\# \/ estendibilità \/ pacchetto di Visual Studio**.  
  
3.  Per implementare un servizio, è necessario creare tre tipi:  
  
    -   Un'interfaccia che descrive il servizio. Molte di queste interfacce sono vuoti, vale a dire non hanno alcun metodo.  
  
    -   Un'interfaccia che descrive l'interfaccia del servizio. Questa interfaccia include metodi per l'implementazione.  
  
    -   Una classe che implementa l'interfaccia del servizio sia il servizio.  
  
     Nell'esempio seguente viene illustrata un'implementazione di base dei tre tipi. Il costruttore della classe del servizio deve impostare il provider del servizio.  
  
    ```c#  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### La registrazione di un servizio  
  
1.  Per registrare un servizio, aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> a pacchetto che fornisce il servizio. Di seguito è riportato un esempio:  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Questo attributo consente di registrare `SMyService` con Visual Studio.  
  
    > [!NOTE]
    >  Per registrare un servizio che sostituisce un altro servizio con lo stesso nome, utilizzare il <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Si noti che un solo la sostituzione di un servizio è consentita.  
  
### Aggiunta di un servizio  
  
1.  1.	Nell'inizializzatore VSPackage, aggiungere il servizio e aggiungere un metodo di callback per creare i servizi. Ecco la modifica da apportare al <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo:  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementare il metodo di callback, che deve creare e restituire il servizio o null se non può essere creata.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio può rifiutare una richiesta per fornire un servizio. Ciò avviene se un altro VSPackage fornisce già il servizio.  
  
3.  A questo punto è possibile ottenere il servizio e utilizzarne i metodi. Vi mostreremo questa nell'inizializzatore, ma è possibile ottenere il servizio in qualsiasi punto che si desidera utilizzare il servizio.  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Il valore di `helloString` deve essere "Hello".  
  
## Vedere anche  
 [Procedura: ottenere un servizio](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Utilizzo e servizi](../extensibility/using-and-providing-services.md)   
 [Funzionalità fondamentali del servizio](../extensibility/internals/service-essentials.md)