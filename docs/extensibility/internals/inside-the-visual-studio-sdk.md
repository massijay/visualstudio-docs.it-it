---
title: "All&#39;interno di Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Guida di orientamento, integrazione di Visual Studio SDK"
  - "Roadmap SDK di Visual Studio integration"
  - "roadmap di integrazione, Visual Studio SDK"
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "gregvanl"
manager: "ghogen"
---
# All&#39;interno di Visual Studio SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questa sezione fornisce informazioni approfondite sulle estensioni di Visual Studio, tra cui architettura di Visual Studio, componenti, servizi, schemi, utilità e simili.  
  
## Architettura di estendibilità  
 Nella figura seguente viene illustrata l'architettura di estendibilità di Visual Studio. Package VS fornisce funzionalità di applicazione, che vengono condivise come servizi all'interno dell'IDE. L'IDE standard offre inoltre una vasta gamma di servizi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che consentono di accedere alla funzionalità di windowing IDE.  
  
 ![Rappresentazione grafica dell'architettura dell'ambiente](../../extensibility/internals/media/environment.png "environment")  
Visualizzazione generalizzato dell'architettura di Visual Studio  
  
## Package VS  
 Package VS sono moduli software che compongono ed estendono Visual Studio con gli elementi dell'interfaccia utente, servizi, progetti, gli editor e finestre di progettazione. Package VS sono l'unità centrale dell'architettura di Visual Studio. Per altre informazioni, vedere [Package VS](../../extensibility/internals/vspackages.md).  
  
## Visual Studio Shell  
 Shell di Visual Studio fornisce funzionalità di base e supporto tecnico di comunicazione incrociata tra le estensioni VSPackage e MEF del componente. Per altre informazioni, vedere [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## Linee guida sull'esperienza utente  
 Se si intende progettare nuove funzionalità per Visual Studio, è consigliabile dare un'occhiata a queste linee guida per i suggerimenti di progettazione e l'utilizzo: [Linee guida sull'esperienza utente di Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## Comandi  
 I comandi sono funzioni che eseguono attività, ad esempio la stampa del documento, aggiornamento di una vista o la creazione di un nuovo file.  
  
 Quando si estende Visual Studio, è possibile creare comandi e registrarlo con la shell di Visual Studio. È possibile specificare come questi comandi verranno visualizzati nell'IDE, ad esempio, un menu o una barra degli strumenti. In genere è presente un comando personalizzato di **strumenti** menu e un comando per visualizzare una finestra degli strumenti vengono visualizzate nel **altre finestre** sottomenu del **visualizzazione** menu.  
  
 Quando si crea un comando, è necessario creare anche un gestore eventi per esso. Il gestore eventi determina quando il comando non è visibile o abilitato, è possibile modificare il testo e garantisce che il comando risponda correttamente quando viene attivata. Nella maggior parte dei casi, l'IDE gestisce i comandi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi in Visual Studio vengono gestiti a partire dal contesto del comando più interna, in base alla selezione locale e procedere con il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo script.  
  
 Per altre informazioni, vedere [I comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## Menu e barre degli strumenti  
 Menu e barre degli strumenti consentono agli utenti di richiamare i comandi. I menu sono righe o colonne di comandi che in genere vengono visualizzate come singoli elementi di testo nella parte superiore di una finestra degli strumenti. Sottomenu sono menu secondari visualizzato quando un utente sceglie i comandi che includono una piccola freccia. Menu di scelta rapida visualizzato quando l'utente fa clic alcuni elementi dell'interfaccia utente. Alcuni nomi di menu comuni **File**, **modificare**, **visualizzazione**, e **finestra**. Per altre informazioni, vedere [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Barre degli strumenti sono righe o colonne di pulsanti e altri controlli, ad esempio caselle di testo, caselle di riepilogo e caselle combinate. Pulsanti della barra degli strumenti sono in genere le immagini icona, ad esempio un'icona di cartella per un **Apri** comando o una stampante per una **Stampa** comando. Tutti gli elementi della barra degli strumenti sono associati i comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene eseguito il comando associato. Nel caso di un controllo elenco a discesa, ogni elemento nell'elenco a discesa è associata a un comando diverso. Alcuni controlli della barra degli strumenti, ad esempio un controllo splitter, sono ibridi. Un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza comandi diversi quando viene selezionato.  
  
## Finestre degli strumenti  
 Finestre degli strumenti vengono utilizzate nell'IDE per visualizzare le informazioni.**Della casella degli strumenti**, **Esplora**, **proprietà** finestra e **Browser Web** sono esempi di finestre degli strumenti.  
  
 Finestre degli strumenti offrono in genere vari controlli con cui l'utente può interagire. Ad esempio, il **proprietà** finestra consente all'utente di impostare le proprietà degli oggetti che assolvono a una funzione particolare. Il **proprietà** finestra è specializzato in questo senso, ma anche generale in quanto può essere utilizzato in molte situazioni diverse. Analogamente, il **Output** finestra è specializzata in quanto fornisce output basato su testo, ma generale perché molti sottosistemi in Visual Studio possono utilizzarlo per fornire output all'utente di Visual Studio.  
  
 Prendere in considerazione l'immagine seguente di Visual Studio, che contiene diverse finestre degli strumenti.  
  
 ![Schermata](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Alcune delle finestre degli strumenti sono ancorate insieme in un unico riquadro che visualizza la finestra degli strumenti di Esplora soluzioni e nasconde le altre finestre ma li rende disponibili facendo clic sulle schede. Nella figura sono illustrate due altre finestre degli strumenti, la **elenco errori** e **Output** finestra ancorata insieme a un unico riquadro.  
  
 Viene inoltre illustrato il riquadro principale del documento, che illustra diverse finestre dell'editor. Sebbene le finestre degli strumenti sono in genere una sola istanza \(ad esempio, è possibile aprire solo una **Esplora**\), finestre dell'editor possono avere più istanze, ognuno dei quali è possibile modificare un documento separato, ma che sono ancorati nello stesso riquadro. La figura mostra un riquadro del documento che dispone di due finestre dell'editor, una finestra di progettazione di form e una finestra del browser che mostra la pagina iniziale. Tutte le finestre nel riquadro del documento sono disponibili facendo clic sulle schede, ma la finestra dell'editor che contiene file EditorPane.cs è visibile e attivo.  
  
 Quando si estende Visual Studio, è possibile creare lo strumento windows che consentono agli utenti di Visual Studio interagire con l'estensione. È inoltre possibile creare il proprio editor che consentono agli utenti di Visual Studio modificare i documenti. Poiché l'editor e finestre degli strumenti verrà integrato in Visual Studio, non devi programmarli per ancorare o vengono visualizzati correttamente in una scheda. Quando si sono registrati correttamente in Visual Studio, si avranno automaticamente le funzionalità tipiche di finestre degli strumenti e finestre di documento in Visual Studio. Per altre informazioni, vedere [Estensione e personalizzazione di finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## Finestre di documento  
 Una finestra del documento è una finestra cornice figlio di una finestra di interfaccia a documenti multipli \(MDI\). Finestre di documento in genere vengono utilizzate per ospitare gli editor di testo, editor di form \(noto anche come finestre di progettazione\) o i controlli di modifica, ma che possono ospitare anche altri tipi di funzionalità. Il **Nuovo File** la finestra di dialogo sono inclusi esempi di finestre di documento fornite da Visual Studio.  
  
 La maggior parte degli editor sono specifici per un linguaggio di programmazione o a un tipo di file, ad esempio pagine HTML, pagine con frame, file di C\+\+ o file di intestazione. Selezionando un modello di **Nuovo File** nella finestra di dialogo in modo dinamico un utente crea una finestra del documento per l'editor per il tipo di file che viene associato al modello. Una finestra del documento viene creata anche quando un utente apre un file esistente.  
  
 Finestre di documento sono limitate all'area client MDI. Ogni finestra del documento contiene una scheda nella parte superiore e l'ordine di tabulazione è collegato ad altre finestre che possono essere aperte nell'area MDI. Pulsante destro del mouse sulla scheda di una finestra del documento consente di visualizzare un menu di scelta rapida che include le opzioni per dividere l'area MDI in più gruppi di schede orizzontali o verticali. Suddivisione area MDI consente di visualizzare contemporaneamente più file. Per altre informazioni, vedere [Finestre di documento](../../extensibility/internals/document-windows.md).  
  
## Editor  
 Editor di Visual Studio consente di personalizzare e utilizzare per il proprio tipo di contenuto mediante Managed Extensibility Framework \(MEF\). In molti casi non è necessario creare un VSPackage per estendere l'editor, ma se si desidera includere funzionalità dalla shell \(ad esempio, un comando di menu o un tasto di scelta rapida\), è possibile combinare un'estensione MEF con un VSPackage.  
  
 È inoltre possibile creare un editor personalizzato, ad esempio se si desidera leggere e scrivere in un database o se si desidera utilizzare una finestra di progettazione. È inoltre possibile utilizzare un editor esterno, ad esempio Blocco note o WordPad Microsoft. Per altre informazioni, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
## Servizi di linguaggio  
 Se si desidera che l'editor di Visual Studio per supportare nuove parole chiave di programmazione o anche un nuovo linguaggio di programmazione, si crea un servizio di linguaggio. Ogni servizio di linguaggio può implementare determinate funzionalità dell'editor completamente, parzialmente o non è affatto. A seconda del modo in cui è configurato, il servizio di linguaggio possa fornire evidenziazione della sintassi, corrispondenza parentesi graffe, il supporto IntelliSense e altre funzionalità dell'editor.  
  
 Il fulcro di un servizio di linguaggio sono uno scanner e parser. Uno scanner \(o lexer\) divide un file di origine in elementi che sono note come token e un parser stabilisce le relazioni tra tali token. Quando si crea un servizio di linguaggio, è necessario implementare il parser e il programma antivirus in modo che Visual Studio possono comprendere i token e la grammatica del linguaggio. È possibile creare servizi di linguaggio gestito o non gestito. Per altre informazioni, vedere [Estensibilità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## Progetti  
 In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare e compilare il codice sorgente e altre risorse. Progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a servizi Web e database e altre risorse. Package VS possibile estendere il sistema di progetto Visual Studio fornisce tipi di progetto, sottotipi di progetto e strumenti personalizzati.  
  
 I progetti possono inoltre essere acquisiti in una soluzione, ovvero un raggruppamento di uno o più progetti che interagiscono per creare un'applicazione. Informazioni di progetto e lo stato relativo alla soluzione vengono archiviate in due file di soluzione, il file di soluzione basata su testo \(con estensione sln\) e il file di soluzione binario utente opzione \(con estensione suo\). Questi file sono simili ai file di gruppo \(VBG\) utilizzati nelle versioni precedenti di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], e l'area di lavoro \(DSW\) e le opzioni utente file \(OPT\) utilizzati nelle versioni precedenti di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Per altre informazioni, vedere [Progetti](../../extensibility/internals/projects.md) e [Soluzioni](../../extensibility/internals/solutions.md).  
  
## Progetto e modelli di elemento  
 Visual Studio include modelli di progetto predefiniti e i modelli di progetto. È possibile inoltre rendere i propri modelli o acquisire modelli dalla community e quindi integrarle in Visual Studio. Il [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) è la fonte per modelli e le estensioni.  
  
 Modelli contengono la struttura del progetto e file di base necessari per compilare un particolare tipo di applicazione, controllo, libreria o classe. Quando si desidera sviluppare software che è simile a uno dei modelli, creare un progetto che si basa sul modello e quindi modificare i file del progetto.  
  
> [!NOTE]
>  L'architettura dei modelli non è supportato per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti. Per informazioni su come creare [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelli di progetto, vedere [Progettazione di una procedura guidata](/visual-cpp/ide/designing-a-wizard).  
  
 Per altre informazioni, vedere [Aggiunta di progetto e i modelli di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## Proprietà e le opzioni  
 Il **proprietà** finestra Visualizza le proprietà di uno o più elementi selezionati: [Estensione delle proprietà](../../extensibility/internals/extending-properties.md) Opzioni pagine contenenti set di opzioni che riguardano un particolare componente, ad esempio un linguaggio di programmazione o un VSPackage: [Opzioni e le pagine di opzioni](../../extensibility/internals/options-and-options-pages.md). Le impostazioni sono le funzionalità in genere correlati dell'interfaccia utente che possono essere importate ed esportate: [Supporto per le impostazioni utente](../../extensibility/internals/support-for-user-settings.md).  
  
## Servizi Visual Studio  
 Un servizio fornisce un set specifico di interfacce per i componenti da utilizzare. Visual Studio fornisce un set di servizi che può essere utilizzato da tutti i componenti, incluse le estensioni. Ad esempio, i servizi di Visual Studio consentono finestre essere mostrati o nascosti in modo dinamico, consentire l'accesso alla Guida, barra di stato o gli eventi dell'interfaccia utente. Editor di Visual Studio fornisce anche servizi che possono essere importati da estensioni dell'editor. Per altre informazioni, vedere [Utilizzo e servizi](../../extensibility/using-and-providing-services.md).  
  
## Debugger  
 Il debugger è l'interfaccia utente per i componenti di debug specifiche della lingua. Se è stato creato un nuovo servizio di linguaggio, sarà necessario creare un motore di debug specifico per associare il debugger. Per altre informazioni, vedere [Estensibilità del Debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Controllo del codice sorgente  
 Per informazioni sull'implementazione di un plug\-in del controllo del codice sorgente o VSPackage, vedere [Controllo del codice sorgente](../../extensibility/internals/source-control.md).  
  
## Procedure guidate  
 È possibile creare una procedura guidata in combinazione con un nuovo tipo di progetto, in modo che la procedura guidata consente agli utenti Prendi le giuste decisioni durante la creazione di un nuovo progetto di quel tipo. Per altre informazioni, vedere [Procedure guidate](../../extensibility/internals/wizards.md).  
  
## Strumenti personalizzati  
 Strumenti personalizzati consentono di associare uno strumento a un elemento in un progetto ed eseguire lo strumento ogni volta che il file viene salvato. Per altre informazioni, vedere [Strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## Utilità VSSDK  
 VSSDK include un set di utilità che potrebbe essere necessario per poter funzionare con diversi aspetti del package VS. Per altre informazioni, vedere [Utilità VSSDK](../../extensibility/internals/vssdk-utilities.md).  
  
## Utilizzo di Windows Installer  
 In alcuni casi potrebbe essere necessario utilizzare il programma di installazione di Windows anziché il programma di installazione VSIX: ad esempio, potrebbe essere necessario scrivere nel Registro di sistema. Per informazioni sull'utilizzo di Windows Installer con le estensioni, vedere [L'installazione di VS con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## Il Visualizzatore della Guida  
 È possibile integrare i propri help e pagine F1 nel Visualizzatore della Guida in linea. Per altre informazioni, vedere [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).