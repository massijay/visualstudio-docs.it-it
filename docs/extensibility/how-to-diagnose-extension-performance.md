---
title: 'Procedura: diagnosticare estensione prestazioni | Documenti di Microsoft'
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Misurare l'impatto di estensione in avvio

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Concentrarsi sulle prestazioni di estensione in Visual Studio 2017

In base ai suggerimenti dei clienti, una delle aree di interesse per il rilascio di Visual Studio 2017 è stata prestazioni carico soluzione e di avvio. Mentre, come team piattaforma Visual Studio, abbiamo lavorato per migliorare le prestazioni di carico soluzione e di avvio in generale, i dati di telemetria suggerisce le estensioni installate possono anche avere un impatto determinante sulla tali scenari.

Per consentire agli utenti di comprendere l'impatto, abbiamo aggiunto una nuova funzionalità in Visual Studio per inviare notifiche agli utenti di estensioni lenta. Quando Visual Studio rileva una nuova estensione che rallentamento carico soluzione o avvio, gli utenti visualizzeranno una notifica nell'IDE che punta alla nuova finestra di dialogo "Gestione delle prestazioni di Visual Studio". Questa finestra di dialogo è sempre accessibile dal menu della Guida in linea per sfogliare estensioni rilevate in precedenza.

![la gestione delle prestazioni di Visual Studio](media/manage-performance.png)

In questo documento mira a consentire agli sviluppatori di estensioni descrivendo la modalità di calcolo impatto di estensione e come poter analizzare localmente per verificare se un'estensione può essere visualizzata come alcun impatto sull'estensione delle prestazioni.

## <a name="how-extensions-can-impact-startup"></a>Le estensioni del possibile impatto di avvio

Uno dei modi più comuni per le estensioni di impatto sulle prestazioni di avvio è scegliendo di caricamento automatico in uno dei contesti dell'interfaccia utente di avvio noti, ad esempio NoSolutionExists o ShellInitialized. Questi contesti dell'interfaccia utente essere attivati durante l'avvio e tutti i pacchetti che includono l'attributo "ProvideAutoLoad" nella relativa definizione con tali contesti verranno caricati e inizializzati in quel momento.

Quando viene misurata l'impatto di un'estensione, focalizzata principalmente sul tempo impiegato da tali estensioni che sceglie di caricamento automatico in contesti di cui sopra. Misurato volte sarebbero includono ma non può essere limitata a:

* Caricamento degli assembly di estensioni per i pacchetti sincroni
* Tempo trascorso nel costruttore di classe del pacchetto per i pacchetti sincroni
* Tempo impiegato nel metodo Initialize (o SetSite) del pacchetto per i pacchetti sincroni
* Per i pacchetti asincroni le operazioni precedenti eseguite sul thread in background e pertanto vengono esclusi dal monitoraggio
* Tempo impiegato nelle operazioni asincrone pianificate durante l'inizializzazione del pacchetto da eseguire nel thread principale
* Tempo impiegato per i gestori eventi, in particolare l'attivazione contesto shell inizializzata o la modifica dello stato di zombie shell

Sono state aggiunte numerose funzionalità a partire da Visual Studio 2015, per agevolare eliminando la necessità di pacchetti di caricamento automatico, posticipare il loro carico per i casi più specifici in cui sarebbero in grado di utilizzare l'estensione o ridurre l'impatto un'estensione quando si carica automaticamente.

È possibile trovare ulteriori informazioni su queste funzionalità nei documenti seguenti:

[Contesti dell'interfaccia utente basati su regole](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): un motore basato su regole più ricco attraversato contesti dell'interfaccia utente consentono di creare contesti personalizzati basati su tipi di progetto, caratteristiche e funzionalità. Questi contesti personalizzati possono essere utilizzati per caricare un pacchetto durante gli scenari più specifici, ad esempio la presenza di un progetto con una capacità specifica invece di avvio. o consentire [comando visibilità essere vincolati a un contesto personalizzato](https://msdn.microsoft.com/en-us/library/bb166512.aspx) in base alle funzionalità del progetto o altre condizioni disponibili, eliminando la necessità di caricare un pacchetto per registrare un gestore di query dello stato di comando.

[Il supporto asincrono pacchetto](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): la nuova classe di base AsyncPackage in Visual Studio 2015 consente ai pacchetti di Visual Studio da caricare in background in modo asincrono se il caricamento del pacchetto è stato richiesto da un attributo di caricamento automatico o di una query asincrona al servizio. Il caricamento in background consente l'IDE di rispondere mentre l'estensione viene inizializzato in background e non sarebbe interessati scenari critici come carico di avvio e di soluzione.

[Servizi asincroni](how-to-provide-an-asynchronous-visual-studio-service.md): con il supporto asincrono pacchetto, è anche aggiunto il supporto per l'esecuzione di query in modo asincrono i servizi e la possibilità di registrare i servizi asincroni. Stiamo lavorando soprattutto sulla conversione di servizi di Visual Studio per supportare query asincrona in modo che la maggior parte del lavoro in una query asincrona si verifica nel thread in background. SComponentModel (host di Visual Studio MEF) è uno dei principali servizi che ora supporta query asincrona che consentono alle estensioni supportare completamente il caricamento asincrono.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Ridurre l'impatto di auto caricamento estensioni

Se un pacchetto deve ancora essere caricato all'avvio automatico, è importante per ridurre al minimo le operazioni eseguite durante l'inizializzazione di pacchetto per ridurre la possibilità di estensione che hanno un impatto di avvio.

Alcuni esempi che potrebbero causare l'inizializzazione di pacchetto per essere costosa sono:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Utilizzo del caricamento del pacchetto sincrono invece di caricamento del pacchetto asincrona

Perché sono stati caricati pacchetti sincroni sul thread principale per impostazione predefinita, si consiglia ai proprietari di estensione che dispongono di pacchetti caricato automaticamente utilizzata la classe di base asincrona pacchetto come indicato in precedenza. Modifica un pacchetto di caricamento automatico per supportare il caricamento asincrono anche renderà più semplice risolvere i problemi riportati di seguito.

### <a name="synchronous-filenetwork-io-requests"></a>Richieste dei / o sincrono file/rete

Idealmente è consigliabile evitare qualsiasi richiesta dei / o file o di rete sincrona nel thread principale come il loro impatto dipenderà lo stato della macchina e può essere bloccato per lunghi periodi di tempo in alcuni casi.

Utilizzando le API dei / o asincrone e il caricamento del package asincrona deve assicurarsi che l'inizializzazione di pacchetto non blocca il thread principale in questi casi e gli utenti possono continuare a interagire con Visual Studio, mentre le richieste dei / o eseguite in background.

### <a name="early-initialization-of-services-components"></a>Prima inizializzazione dei servizi, componenti

Uno dei modelli comuni nell'inizializzazione del pacchetto consiste nell'inizializzare i servizi utilizzati o fornite da tale pacchetto nel metodo initialize costruttore o un pacchetto. Sebbene in questo modo i servizi sono pronti per essere utilizzato, è anche possibile aggiungere costi non necessari per creare un pacchetto di caricamento se tali servizi non vengono utilizzati immediatamente. Tali servizi invece devono essere inizializzati su richiesta per ridurre al minimo il lavoro svolto nell'inizializzazione del pacchetto.

Per i servizi globali forniti da un pacchetto, è possibile utilizzare metodi AddService che accetta una funzione in modo differito inizializzare il servizio solo quando è richiesto da un componente. Per i servizi utilizzati all'interno del pacchetto, è possibile utilizzare Lazy<T> o AsyncLazy<T> per garantire servizi inizializzato o eseguire una query al primo utilizzo.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Misurare l'impatto di auto caricato estensioni tramite PerfView

Durante l'analisi del codice consentono di identificare i percorsi di codice che possono rallentare l'inizializzazione di pacchetto, è inoltre possibile utilizzare la traccia utilizzando applicazioni, ad esempio PerfView per comprendere l'impatto di un caricamento del pacchetto di avvio di Visual Studio.

PerfView è uno strumento di analisi ampio sistema che consenta di informazioni sui percorsi ricorrenti in un'applicazione a causa di utilizzo della CPU o bloccare le chiamate di sistema. Di seguito è riportato un esempio rapido dall'analisi di un'estensione di esempio usando PerfView disponibile all'indirizzo di [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Esempio di codice:**

Questo esempio è basato sull'esempio caso di codice riportato di seguito, che consente di visualizzare alcune cause comuni di ritardo:

```c#
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Registrazione di una traccia con PerfView:**

Quando si imposta l'ambiente di Visual Studio con l'estensione installata, è possibile registrare una traccia di avvio aprendo PerfView e finestra di dialogo raccolta dal menu "Raccolta".

![menu Raccogli perfview](media/perfview-collect-menu.png)

Le opzioni predefinite fornirà gli stack di chiamate per l'utilizzo della CPU, ma poiché siamo interessati anche la durata del blocco, è inoltre consigliabile abilitare stack "Thread Time". Una volta che le impostazioni sono pronte, è possibile fare clic su "Avvia raccolta" e avviare Visual Studio dopo aver avviata la registrazione.

Prima interrompere la raccolta, si desidera assicurarsi che Visual Studio è completamente inizializzato, la finestra principale è completamente visibile e se l'estensione dispone degli elementi dell'interfaccia utente che viene visualizzata automaticamente, è inoltre visibile. Quando viene inizializzata l'estensione di Visual Studio è stata caricata completamente, è possibile arrestare la registrazione per analizzare la traccia.

**L'analisi di una traccia con PerfView:**

Una volta completata la registrazione PerfView verrà automaticamente aprire la traccia ed espandere le opzioni.

Ai fini di questo esempio, ciò che interessa principalmente nella vista "Thread stack ora", è possibile trovare gruppo"Avanzate". Questa visualizzazione saranno inclusi il tempo totale trascorso in un thread da un metodo inclusi tempo CPU e tempo bloccato, ad esempio IO del disco o in attesa di handle.

 ![ora gli stack dei thread](media/perfview-thread-time-stacks.png)

 Durante l'apertura di visualizzazione "Thread stack ora", è necessario scegliere il processo "devenv" per avviare l'analisi.

PerfView è Guida dettagliata su come leggere thread stack ora il proprio menu della Guida per un'analisi più dettagliata. Ai fini di questo esempio, si desidera filtrare ulteriormente la visualizzazione includendo solo gli stack di thread di avvio e nome del modulo di pacchetti.

1. Impostare "GroupPats" testo vuoto per rimuovere qualsiasi gruppo aggiunto per impostazione predefinita.
2. Set "IncPats" per includere una parte del nome dell'assembly e avvio Thread oltre a filtro di processo esistente. In questo caso, deve essere "devenv; Thread di avvio. MakeVsSlowExtension".

A questo punto la vista mostrerà solo costo associato con gli assembly correlati all'estensione. In questa visualizzazione, ogni volta che elencati nella colonna "SPA" (costo inclusivo) del thread di avvio è correlato al nostro estensione filtrati e sarà alcun impatto sull'avvio.

Per l'esempio precedente alcuni interessano chiamata stack sarebbe:

1. IO utilizzo classe System.IO: costo inclusivo dei frame potrebbe non essere molto costosa nella traccia, sono una potenziale causa un problema poiché la velocità dei / o file può variare da computer a computer.

  ![frame dei / o di sistema](media/perfview-system-io-frames.png)

2. Bloccare le chiamate in attesa di altre operazioni asincrone: In questo caso tempo inclusivo rappresenta l'ora in cui il thread principale è bloccato al completamento del lavoro asincrono.

  ![frame di chiamata di blocco](media/perfview-blocking-call-frames.png)

Una delle altre visualizzazioni nella traccia che risulteranno utili per determinare l'impatto sarà "Immagine carico stack". È possibile applicare gli stessi filtri applicati alla visualizzazione "Thread stack ora" e scoprire tutti gli assembly caricati per il codice eseguito dal pacchetto caricato automaticamente.

È importante per ridurre al minimo numero di assembly caricati all'interno di una routine di inizializzazione del pacchetto come ogni assembly aggiuntivo comporterà la / o disco aggiuntivo che può rallentare l'avvio notevolmente nei computer più lenti.

## <a name="summary"></a>Riepilogo

Avvio di Visual Studio è stata una delle aree che è continuamente ottenere commenti e suggerimenti sul. Il nostro obiettivo come indicato in precedenza è per tutti gli utenti a un avvio coerenza indipendentemente dalle estensioni installati e i componenti e si desidera utilizzare con i proprietari di estensione per aiutarli a consentono di raggiungere tale obiettivo. Le informazioni aggiuntive sopra indicate sono utili in un impatto estensioni all'avvio e di evitare di dover auto carico o per caricare in modo asincrono per ridurre al minimo l'impatto sulla produttività degli utenti.
