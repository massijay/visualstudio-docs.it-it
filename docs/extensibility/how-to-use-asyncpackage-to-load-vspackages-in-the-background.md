---
title: "Procedura: utilizzare AsyncPackage per caricare in Background di VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# Procedura: utilizzare AsyncPackage per caricare in Background di VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Caricamento e l'inizializzazione di un pacchetto Visual Studio può comportare i\/o disco. Se questo tipo i\/o si verifica nel thread dell'interfaccia utente, può causare i problemi di velocità di risposta. Per risolvere questo problema, Visual Studio 2015 è stato introdotto il <xref:Microsoft.VisualStudio.Shell.AsyncPackage> \(classe\) che consente il caricamento del pacchetto in un thread in background.  
  
## Creazione di un AsyncPackage  
 È possibile iniziare creando un progetto VSIX \(**File \/ nuovo \/ progetto \/ Visual c\# \/ Extensibility \/ progetto VSIX**\) e aggiunta al progetto un VSPackage \(fare clic con il pulsante destro sul progetto e **\/Aggiungi nuovo elemento \/ c\# elemento\/estendibilità\/Visual Studio pacchetto**\). È quindi possibile creare servizi e aggiungere tali servizi al pacchetto.  
  
1.  Derivare il pacchetto da <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Se si desidera fornire servizi a cui l'esecuzione di query può causare il pacchetto da caricare:  
  
     Per indicare a Visual Studio che il pacchetto è sicuro per il caricamento in background e consente di partecipare a questo comportamento, il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> deve impostare **AllowsBackgroundLoading** proprietà su true nel costruttore dell'attributo.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Per indicare a Visual Studio che è possibile creare un'istanza del servizio in un thread in background, è necessario impostare il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> impostata su true il <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> costruttore.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Se si sta caricando tramite i contesti dell'interfaccia utente, quindi è necessario specificare **PackageAutoLoadFlags.BackgroundLoad** per il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> o il valore \(0x2\) nei flag scritto con il valore della voce di caricamento automatico del pacchetto.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Nel caso di operazioni di inizializzazione asincrona da eseguire, è necessario eseguire l'override <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Rimuovere il **Initialize \(\)** metodo fornito dal modello di progetto VSIX. \(Il **Initialize \(\)** metodo **AsyncPackage** è sealed\). È possibile utilizzare uno qualsiasi del <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metodi per aggiungere servizi asincroni al pacchetto.  
  
     Nota: Per chiamare **base. InitializeAsync\(\)**, è possibile modificare il codice sorgente per:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  È necessario prestare attenzione a non effettuare le chiamate RPC \(rimuovere Procedure Call\) dal codice di inizializzazione asincrona \(in **InitializeAsync**\). Questi possono verificarsi quando si chiama <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direttamente o indirettamente.  Quando sono necessari i carichi di sincronizzazione, il thread dell'interfaccia utente verrà bloccato tramite <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Il modello di blocco predefinito Disabilita RPC. Ciò significa che se si tenta di utilizzare una chiamata RPC dalle attività asincrone, è un deadlock se il thread dell'interfaccia utente è in attesa per il pacchetto da caricare. L'alternativa generale consiste nell'effettuare il marshalling di codice per il thread dell'interfaccia utente se necessario mediante qualcosa di simile **Factory delle attività attive**del <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> o un altro meccanismo che non utilizza una chiamata RPC.  Non utilizzare **ThreadHelper.Generic.Invoke** o in genere blocca il thread chiamante in attesa di ottenere al thread dell'interfaccia utente.  
  
     Nota: È consigliabile non utilizzare **GetService** o **QueryService** nel **InitializeAsync** metodo. Se è necessario utilizzare tali informazioni, è necessario passare prima al thread dell'interfaccia utente. L'alternativa consiste nell'utilizzare <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> da di **AsyncPackage** \(eseguendo il cast a <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.\)  
  
 In c\#: Creare un AsyncPackage:  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## Convertire un VSPackage esistente AsyncPackage  
 La maggior parte del lavoro è analoga alla creazione di un nuovo **AsyncPackage**. È necessario seguire i passaggi da 1 a 5. Inoltre, è necessario richiedere maggiore attenzione nei casi seguenti:  
  
1.  Ricordarsi di rimuovere il **inizializzare** sostituzione era nel pacchetto.  
  
2.  Evitare i deadlock: possono essere nascosti RPC nel codice che ora si verificano in un thread in background. È necessario assicurarsi che se si effettua una chiamata RPC \(ad esempio **GetService**\), è necessario uno switch \(1\) per il thread principale o \(2\) utilizzare la versione asincrona dell'API, se presente \(ad esempio **GetServiceAsync**\).  
  
3.  Non passare tra i thread troppo di frequente. Provare a localizzare il lavoro che può verificarsi in un thread in background. In questo modo si riduce il tempo di caricamento.  
  
## Esecuzione di query su servizi da AsyncPackage  
 Un **AsyncPackage** può o non è possibile caricare in modo asincrono in base al chiamante. Ad esempio,  
  
-   Se il chiamante chiamato **GetService** o **QueryService** \(entrambe le API sincrona\) o  
  
-   Se il chiamante chiamato **IVsShell::LoadPackage** \(o **IVsShell5::LoadPackageWithContext**\) o  
  
-   Il carico viene attivato da un contesto dell'interfaccia utente, ma non è stato specificato che il meccanismo del contesto dell'interfaccia utente di caricare in modo asincrono  
  
 quindi il pacchetto verrà caricato in modo sincrono.  
  
 Si noti che il pacchetto ancora un'opportunità \(in fase di inizializzazione asincrona\) per eseguire le operazioni dal thread UI, anche se il thread dell'interfaccia utente verrà bloccato per il completamento del lavoro. Se il chiamante utilizza **IAsyncServiceProvider** a query in modo asincrono per il servizio, quindi l'inizializzazione e carico viene eseguiti in modo asincrono supponendo che non bloccare immediatamente nell'oggetto attività risultante.  
  
 In c\#: Come eseguire una query del servizio in modo asincrono:  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```