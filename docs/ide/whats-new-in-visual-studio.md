---
title: "Novità di Visual Studio 2017 RC | Microsoft Docs"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 4fb097ab0ee0d45fd5727e3170db3393392abf23
ms.openlocfilehash: dc1941fd755c28039560b608733067b1da365c3a

---
# <a name="what39s-new-in-visual-studio-2017"></a>Novità di Visual Studio 2017
Visual Studio 2017 RC è una suite integrata di strumenti di produttività per sviluppatori, servizi cloud ed estensioni che consentono all'utente e al suo team di creare app e giochi di grande impatto per il Web, Windows Store, il desktop, Android e iOS.  

In questa versione finale candidata (RC) della versione più recente di Visual Studio l'attenzione si è concentrata sui miglioramenti delle prestazioni e della produttività. In termini di prestazioni, Visual Studio si avvia più rapidamente, ha una maggiore capacità di risposta e usa meno memoria rispetto al passato. In termini di produttività, sono state aggiunte o aggiornate funzionalità che consentono di essere più efficienti quando si usa Visual Studio.

> [!TIP]
> Per un esempio della nuova versione RC, guardare il video sulle [novità di Visual Studio](https://channel9.msdn.com/events/connect/2016/159) su Channel 9.   

Di seguito è riportato un riepilogo generale delle modifiche apportate:

* **Produttività ottimizzata**. I miglioramenti di esplorazione del codice, IntelliSense, refactoring, correzioni del codice e debug consentono di risparmiare tempo e sforzi nelle attività quotidiane, indipendentemente dal linguaggio o dalla piattaforma. Per i team che adottano DevOps, Visual Studio 2017 semplifica inoltre il ciclo interno per gli sviluppatori, accelerando il flusso del codice con le nuovissime funzionalità in tempo reale, come Live Unit Testing e convalida delle dipendenze architetturali in tempo reale.
* **Concetti fondamentali ridefiniti**.  C'è una rinnovata attenzione al miglioramento dell'efficienza delle attività fondamentali che gli sviluppatori incontrano quotidianamente. Da una nuovissima installazione leggera e modulare, personalizzata in base alle esigenze dell'utente, un IDE più veloce dall'avvio all'arresto, fino a un nuovo modo di visualizzare, modificare ed eseguire il debug di qualsiasi codice senza progetti e soluzioni, Visual Studio 2017 consente agli sviluppatori di concentrarsi sul quadro generale.
* **Sviluppo di Azure semplificato**. Una suite di strumenti Azure predefiniti consente agli sviluppatori di creare facilmente applicazioni per cloud con tecnologia Microsoft Azure. Visual Studio facilita la configurazione, la creazione, il debug, l'inserimento in pacchetti e la distribuzione di applicazioni e servizi in Microsoft Azure direttamente dall'IDE.
* **Sviluppo di app di alto livello per dispositivi mobili**. Con gli strumenti avanzati di debug e profilatura e le funzionalità di generazione di unit test, Visual Studio 2017 con Xamarin facilita e accelera più che mai la creazione, la connessione e l'ottimizzazione delle app per dispositivi mobili per Android, iOS e Windows. Gli sviluppatori possono anche scegliere di sviluppare app per dispositivi mobili con lo sviluppo di librerie multipiattaforma di Apache Cordova o Visual C++ in Visual Studio.  

Di seguito sono riportate altre informazioni sulle modifiche più significative.

> [!NOTE]
> Per un elenco completo delle nuove funzionalità in Visual Studio 2017 RC e nel relativo aggiornamento RC successivo, vedere le [Note sulla versione](https://www.visualstudio.com/news/vs2015-vs). Per un elenco di problemi e soluzioni alternative, vedere la sezione [Problemi noti](https://www.visualstudio.com/news/vs2015-vs#knownissues) delle Note sulla versione.   

## <a name="performance-improvements"></a>Miglioramenti delle prestazioni

### <a name="a-new-setup-experience"></a>Una nuova esperienza di installazione  
[Scaricare Visual Studio Enterprise 2017 RC](https://aka.ms/vs/15/preview/vs_enterprise) o [verificare i requisiti di sistema di Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)

 L'esperienza di installazione di Visual Studio è stata riprogettata ed è ancora più semplice installare solo le funzionalità necessarie, quando è necessario. È anche stato ridotto il footprint minimo, in modo che sia possibile installare Visual Studio più rapidamente con un minore impatto sul sistema. E in più la disinstallazione non presenta problemi.

 La modifica più importante che si nota quando si installa Visual Studio è la nuova esperienza di installazione. Nella scheda **Carichi di lavoro** sono visualizzate le opzioni di installazione raggruppate in modo da rappresentare i framework, i linguaggi e le piattaforme più comuni, in grado di supportare qualsiasi attività, dallo sviluppo desktop .NET all'analisi scientifica dei dati con R, Python e F#.  

 ![Finestra di dialogo di installazione di Visual Studio 2017 RC](../ide/media/willow1.png "VS2017RC_Setup_screen")

Scegliere i carichi di lavoro necessari e modificarli quando è necessario. L'installazione minima ha una dimensione di poche centinaia di megabyte, ma contiene comunque il supporto per le modifiche di base del codice per più di venti linguaggi, oltre alle funzionalità di controllo del codice sorgente.

Sono state anche aggiunte modalità di installazione diverse per Visual Studio. Si vuole scegliere i propri componenti anziché usare i carichi di lavoro? Basta selezionare la scheda **Singoli componenti** nel programma di installazione. Si vuole installare i Language Pack anche senza modificare l'opzione lingua di Windows? Scegliere la scheda **Language Pack** del programma di installazione.  

Per altre informazioni sulla nuova esperienza di installazione, incluse le istruzioni dettagliate per eseguirla, vedere la pagina [Installare Visual Studio](../install/install-visual-studio.md).


### <a name="start-visual-studio-faster"></a>Avviare Visual Studio più rapidamente
Se Visual Studio rileva che l'avvio dell'IDE è lento, offre un Controllo prestazioni per Visual Studio che consente di velocizzare le operazioni. In Controllo prestazioni sono elencate tutte le estensioni e le finestre degli strumenti che rallentano l'avvio dell'IDE. È possibile usare la funzionalità per migliorare le prestazioni di avvio, stabilendo quando avviare le estensioni o se le finestre degli strumenti vengono aperte all'avvio.

### <a name="decrease-solution-load-time"></a>Ridurre i tempi di caricamento delle soluzioni
Lavorare su soluzioni che contengono fino a 100 progetti non significa che è necessario usare tutti i file o progetti contemporaneamente. Ora è possibile modificare ed eseguire il debug senza attendere che Visual Studio carichi ogni progetto. Per provare questa procedura con i progetti gestiti, attivare il **caricamento leggero delle soluzioni** da Strumenti-> Opzioni-> Progetti e soluzioni.

  ![Finestra di dialogo Opzioni in Visual Studio 2017 RC](../ide/media/vs2017ide-LightweightSolutionLoad.PNG "Finestra di dialogo Opzioni VS2017RC - Caricamento leggero soluzioni")

### <a name="faster-on-demand-loading-of-extensions"></a>Caricamento su richiesta delle estensioni più rapido
L'idea è semplice: caricare le estensioni quando sono necessarie anziché all'avvio di Visual Studio. Per prima cosa, le estensioni Python e Xamarin sono state spostate nel caricamento su richiesta ed è in corso lo spostamento in questo modello di tutte le estensioni accluse a Visual Studio e delle estensioni di fornitori di terze parti. Le informazioni sulle estensioni che hanno un impatto sulle prestazioni di avvio, caricamento delle soluzioni e digitazione, sono disponibili in ? -> Gestisci prestazioni di Visual Studio.

  ![Finestra di dialogo Opzioni in Visual Studio 2017 RC](../ide/media/vs2017ide-ManageVSperf.png "Finestra di dialogo Guida di VS2017RC - Gestisci prestazioni")

## <a name="productivity-improvements"></a>Miglioramenti della produttività

### <a name="sign-in-across-multiple-accounts"></a>Accedere a più account  
È stato introdotto in Visual Studio 2017 RC un nuovo servizio di identità che consente di condividere gli account utente in più strumenti di sviluppo Microsoft, ad esempio Team Explorer, strumenti di Azure, pubblicazione in Windows Store e altri.

È anche possibile restare connessi più a lungo: non verrà chiesto di accedere nuovamente ogni 12 ore. Per altre informazioni, vedere il post del blog relativo alla [riduzione del numero di richieste di accesso a Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/08/15/fewer-visual-studio-sign-in-prompts/).

### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>Gestire le estensioni con Gestione roaming estensioni
Ora è ancora più semplice configurare ogni ambiente di sviluppo usando le estensioni preferite quando si accede a Visual Studio. Il nuovo strumento Gestione roaming estensioni tiene traccia di tutte le estensioni preferite creando un elenco sincronizzato nel cloud.  

Per visualizzare rapidamente un elenco delle estensioni in Visual Studio, fare clic su Strumenti > Estensioni e aggiornamenti e quindi scegliere Gestione roaming estensioni.

![Visual Studio 2017 - Finestra di dialogo Estensioni e aggiornamenti](../ide/media/vs2017ide-ExtensionsAndUpdates.png "Visual Studio 2017 - Strumenti > finestra di dialogo Estensioni e aggiornamenti")

Gestione roaming estensioni tiene traccia di tutte le estensioni installate, ma è possibile scegliere quelle che si vuole aggiungere all'elenco di roaming.

![Visual Studio 2017 - Finestra di dialogo Estensioni e aggiornamenti](../ide/media/vs2017ide-RoamingExtensionManager.png "Visual Studio 2017 - Gestione roaming estensioni")

Quando si usa Gestione roaming estensioni si noteranno tre tipi di icona nell'elenco:
* ![Icona con roaming](../ide/media/vs2017ide-roamedicon.png "Icona con roaming") ***Icona con roaming***: un'estensione che fa parte dell'elenco di roaming, ma non è installata nel computer.
  Per eseguire l'installazione usare il pulsante **Download**.
* ![Icona con roaming e installazione](../ide/media/vs2017ide-roamedinstalledicon.png "Icona con roaming e installazione") ***Icona con roaming e installazione***: tutte le estensioni incluse nell'elenco di roaming e installate nell'ambiente di sviluppo.
  Se si decide di evitare il roaming, è possibile rimuovere le estensioni usando il pulsante **Arresta roaming**.
* ![Icona con installazione](../ide/media/vs2017ide-installedicon.png "Icona con installazione") ***Icona con installazione***: tutte le estensioni installate nell'ambiente, ma non incluse nell'elenco di roaming.
  Per aggiungere le estensioni all'elenco di roaming, usare il pulsante **Avvia roaming**.

Queste icone indicano lo stato corrente dell'elenco. È possibile includere qualsiasi estensione con qualsiasi stato, personalizzandole in base alle proprie esigenze. In alternativa, è possibile usare le procedure automatiche. Qualsiasi estensione scaricata quando si è connessi verrà aggiunta all'elenco come **con roaming e installazione** e sarà inclusa nell'elenco di roaming. In questo modo sarà possibile accedere all'estensione da qualsiasi altro computer.

### <a name="experience-live-architecture-dependency-validation-and-live-unit-testing"></a>Convalida delle dipendenze architetturali in tempo reale e Live Unit Testing

In Visual Studio Enterprise 2017 RC, se sono stati configurati diagrammi di convalida delle dipendenze, detti anche diagrammi di livello, è ora possibile ricevere notifiche tempo reale in caso di violazioni delle regole di dipendenza architetturale durante la digitazione di codice nell'Editor del codice.

Gli errori vengono visualizzati nell'Elenco errori e le linee a zigzag nell'editor di testo indicano la posizione esatta di una violazione. Ora le probabilità di introdurre dipendenze indesiderate sono più ridotte.

![Convalida dell'architettura in tempo reale](../ide/media/vs2017ide-LiveArchitectureDepedendencyValidation.png "Convalida dell'architettura in tempo reale")

#### <a name="live-unit-testing"></a>Live Unit Testing:

Live Unit Testing è una nuova funzionalità appena introdotta che è presente solo nell'edizione Enterprise di Visual Studio. Questa funzionalità mostra i risultati dei test unità e del code coverage direttamente nell'editor mentre si scrive il codice. Funziona con i progetti C#/VB per .NET Framework e supporta tre framework di test di MSTest, xUnit e NUnit.

### <a name="visual-studio-ide-enhancements"></a>Miglioramenti dell'IDE di Visual Studio
#### <a name="interact-with-git"></a>Interagire con Git:
I controlli nell'angolo inferiore dell'IDE di Visual Studio consentono di eseguire il commit e pubblicare rapidamente i progetti Git e di gestire i repository Git.

![Finestra di dialogo di installazione di Visual Studio 2017 RC](../ide/media/vsIDE-GitInteraction.png "Git-tools-in-the-VS2017RC-IDE")

#### <a name="view-and-navigate-code-with-structure-visualizer"></a>Visualizzare ed esplorare il codice con il visualizzatore di struttura:
Nell'editor del codice di Visual Studio è disponibile una nuova funzionalità per la visualizzazione della struttura. La funzionalità consente di visualizzare linee guida verticali tra le aree annidate del codice, rendendo più semplici la visualizzazione e l'esplorazione del codice. Questa funzionalità è disponibile per tutti i linguaggi supportati da TextMate e per Visual C#, Visual Basic e XAML.

![Finestra di dialogo installazione di Visual Studio 2017 RC](../ide/media/vsIDE-StructureVisualizer.png "struttura visualizzatore in VS2017RC")

#### <a name="experience-an-improved-navigate-to"></a>Miglioramento della funzione Passa a:
La funzione Passa a è stata migliorata. La finestra Passa a è stata semplificata ed è stato aggiunto il supporto per caratteri di filtro aggiuntivi che consentono di limitare le ricerche di codice.

#### <a name="create-apps-in-even-more-programming-languages"></a>Creare app con ancora più linguaggi di programmazione:
È possibile creare app in Visual Studio usando una gamma più ampia di linguaggi di programmazione rispetto alle versioni precedenti e soluzioni e progetti non sono più necessari. Il codice ottiene la colorazione della sintassi, il completamento delle istruzioni di base e, in alcuni casi, la funzione Passa a e altri tipi di supporto. Se il linguaggio preferito non è supportato, è possibile creare il relativo supporto usando le grammatiche TextMate.

### <a name="visual-c"></a>Visual C++
In Visual Studio 2017 RC sono stati inclusi numerosi aggiornamenti e correzioni per l'ambiente Visual C++. Sono stati corretti più di 250 bug e problemi nel compilatore e negli strumenti, molti dei quali sono stati segnalati dai clienti attraverso [Microsoft Connect](https://connect.microsoft.com/VisualStudio "Microsoft Connect").

Sono stati inoltre apportati numerosi miglioramenti, tra cui la distribuzione delle istruzioni di base di C++ con Visual Studio, l'aggiornamento del compilatore aggiungendo un supporto avanzato per le funzionalità di C++11 e C++, l'aggiunta e l'aggiornamento di funzionalità nelle librerie di C++, il miglioramento delle prestazioni dell'IDE e dei carichi di lavoro di installazione di C++ e altro ancora.

Per informazioni dettagliate, vedere la pagina [Novità di Visual C++ in Visual 2017 RC](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio).  


### <a name="debugging-and-diagnostics"></a>Debug e diagnostica
Il debug ora è più rapido e non causa ritardi durante la modifica.

Ad esempio, in una versione precedente di Visual Studio è stato introdotto il cosiddetto processo di hosting per i progetti di WPF, Windows Form e console gestita per rendere il debug più rapido creando un processo in background da usare nella sessione di debug successiva. Sebbene la funzionalità in sé sia corretta, Visual Studio non rispondeva per alcuni secondi quando si interrompeva il debug o si usava Visual Studio al termine della sessione di debug.

In Visual Studio 2017 il processo di hosting è stato disattivato e il debug è stato ottimizzato in modo da essere altrettanto rapido senza il processo di hosting e ancora più rapido per i progetti che non hanno mai usato il processo di hosting, ad esempio i progetti ASP.NET, Universale di Windows e C++.

#### <a name="run-to-click"></a>Eseguire fino alla riga selezionata:
Durante il debug è ora sufficiente fare clic sull'icona accanto a una riga di codice per eseguire tale riga. Non è più necessario impostare punti di interruzione temporanei ed eseguire diversi passaggi per eseguire il codice fino a una determinata riga.

![Visual Studio 2017 RC Debug - Esecuzione fino alla riga selezionata](../ide/media/vs2017ide-RunToClick.png "Esecuzione fino alla riga selezionata in debug e diagnostica di Visual Studio 2017")

#### <a name="the-new-exception-helper"></a>Nuovo supporto eccezione:

Il nuovo supporto eccezione consente di visualizzare rapidamente le informazioni relative alle eccezioni in una finestra di dialogo compatta, non modale e con accesso immediato alle eccezioni interne.

È possibile individuare rapidamente i riferimenti Null direttamente nel supporto eccezione durante la diagnostica di NullReferenceException.

Ora si può escludere l'interruzione per i tipi di eccezione generati da moduli specifici facendo clic sulla casella di controllo per aggiungere una condizione durante l'arresto in corrispondenza di un'eccezione generata.

![Nuova finestra di dialogo del supporto eccezioni](../ide/media/vs2017ide-ExceptionHelper.png "Nuova finestra di dialogo del supporto eccezioni")

Per altre informazioni, vedere il post del blog relativo all'[uso del nuovo supporto eccezione in Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2016/03/31/using-the-new-exception-helper-in-visual-studio-15-preview/).

## <a name="talk-to-us"></a>Comunicazioni con Microsoft  
 È possibile inviare commenti e suggerimenti al team di Visual Studio. Microsoft prende infatti in seria considerazione i commenti e suggerimenti ricevuti dai clienti, usandoli per migliorare i propri prodotti.  

Per inoltrare suggerimenti su come migliorare Visual Studio o per segnalare un problema, consultare la pagina [Comunicazioni con Microsoft](../ide/talk-to-us.md) per altri dettagli.  

### <a name="report-a-problem"></a>Segnalare un problema  
 A volte un messaggio non è sufficiente per comunicare il reale impatto di un problema riscontrato. Se si verifica un blocco, un arresto anomalo del sistema o un altro problema di prestazioni, è possibile condividere facilmente con Microsoft la procedura per riprodurre il problema e i file di supporto, ad esempio le schermate e i file dump di traccia e heap, usando lo strumento **Segnala un problema**. Per altre informazioni su come utilizzare questo strumento, vedere la pagina relativa alla [segnalazione dei problemi](how-to-report-a-problem-with-visual-studio-2017.md).  

### <a name="track-your-issue-in-connect"></a>Tenere traccia del problema in Connect  
 Se si vuole tenere traccia dello stato dei commenti inviati su Visual Studio, accedere a [Connect](http://connect.microsoft.com/) e segnalare il bug. Dopo aver effettuato la segnalazione è possibile tornare a Connect per tenere traccia dello stato.  

## <a name="see-also"></a>Vedere anche  
* [Novità di Visual C++](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [Novità di C#](https://docs.microsoft.com/en-us/dotnet/articles/csharp/csharp-7)  
* [What's New for Team Foundation Server](https://www.visualstudio.com/en-us/docs/whats-new) (Novità per Team Foundation Server)
* [Note sulla versione di Visual Studio](https://www.visualstudio.com/news/vs2015-vs)



<!--HONumber=Feb17_HO4-->


