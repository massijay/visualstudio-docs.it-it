---
title: Ambienti Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8876f8c1-4770-44dc-97d8-bf0035ae8196
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 9140ca7549eefc3ac221f3ca0aa54fde482c8623
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---

# <a name="python-environments"></a>Ambienti Python

Python in Visual Studio consente di gestire facilmente più ambienti Python e di passare da uno all'altro per progetti diversi. 

Nota: se non si è esperti di Python in Visual Studio, vedere prima di tutto gli argomenti seguenti su cui si basa il contenuto di questo articolo:

    - [Uso di Python in Visual Studio](python-in-visual-studio.md)
    - [Installazione del supporto di Python in Visual Studio](installation.md)

Un *ambiente* Python, in cui si esegue sempre codice Python, è costituito da un interprete, una libreria (in genere quella standard Python) e un set di pacchetti installati. L'insieme di questi componenti determina la sintassi e i costrutti di linguaggio validi, le funzionalità accessibili del sistema operativo e i pacchetti che è possibile usare.

In Visual Studio, un ambiente include anche un database di IntelliSense per le librerie di un ambiente, in modo che digitando un'istruzione come `import` nell'editor di Visual Studio venga automaticamente visualizzato un elenco delle librerie disponibili, nonché i moduli in esse presenti.

Gli sviluppatori usano spesso un unico ambiente Python globale, ma può capitare che altri debbano gestire più ambienti globali, ambienti specifici del progetto e probabilmente anche ambienti virtuali come illustrato in questo argomento:

- [Selezione e installazione di interpreti Python](#selecting-and-installing-python-interpreters)
- [Gestione di ambienti Python in Visual Studio](#managing-python-environments-in-visual-studio)
- [Ambienti globali](#global-environments)
- [Ambienti specifici del progetto](#project-specific-environments)
- [Ambienti virtuali](#virtual-environments)
- [Gestione dei pacchetti necessari](#managing-required-packages)
- [Percorsi di ricerca](#search-paths)

Per un video introduttivo, vedere [Visual Studio Python Tutorial Deep Dive: Interpreters](https://youtu.be/KY1GEOo3qy0) (Esercitazione approfondita su Python in Visual Studio: interpreti) su youtube.com (durata: 13 minuti e 27 secondi).

> [!VIDEO https://www.youtube.com/embed/KY1GEOo3qy0]

## <a name="selecting-and-installing-python-interpreters"></a>Selezione e installazione di interpreti Python

Ad eccezione di Visual Studio 2017, il supporto per Python non include un interprete Python ed è quindi necessario installare uno degli interpreti seguenti per eseguire il codice. In generale, Visual Studio rileva automaticamente i nuovi interpreti installati e configura un ambiente appositamente per essi. In caso contrario, vedere [Creazione di un ambiente per un interprete esistente](#creating-an-environment-for-an-existing-interpreter) più avanti.

| Interprete | Descrizione | 
| --- | --- | 
| [CPython](https://www.python.org/) | Interprete "nativa" più comunemente usato, disponibile nelle versioni a 32 e a 64 bit (consigliata la versione a 32 bit). Include le funzionalità più recenti del linguaggio e offre la massima compatibilità con i pacchetti Python, nonché il supporto completo per il debug e l'interoperabilità con [IPython](http://ipython.org/). Vedere anche: [Should I use Python 2 or Python 3?](http://wiki.python.org/moin/Python2orPython3) (Differenze tra Python 2 e Python 3). |
| [IronPython](http://ironpython.codeplex.com/) | Implementazione .NET di Python, disponibili nelle versioni a 32 e a 64 bit, che offre interoperabilità con C#/F# e Visual Basic, accesso alle API .NET, debug Python standard (ma non debug C++ in modalità mista) e debug IronPython/C# in modalità mista. IronPython non supporta però gli ambienti virtuali. | 
| [Anaconda](https://www.continuum.io) | Piattaforma Open Data Science basata su Python che include la versione più recente di CPython e la maggior parte dei pacchetti difficili da installare. È la piattaforma consigliata se non è possibile sceglierne una diversa. |
| [PyPy](http://www.pypy.org/) | Implementazione JIT di traccia ad alte prestazioni di Python, ideale per applicazioni a esecuzione prolungata e situazioni in cui si verificano problemi di prestazioni, ma non si riesce a trovare altre soluzioni. Funziona con Visual Studio, ma offre supporto limitato per le funzionalità avanzate di debug. |
| [Jython](http://www.jython.org/) | Implementazione di Python in Java Virtual Machine (JVM). Analogamente a IronPython, il codice in esecuzione in Jython può interagire con librerie e classi Java, ma potrebbe non essere in grado di usare molte librerie destinate a CPython. Funziona con Visual Studio, ma offre supporto limitato per le funzionalità avanzate di debug. |

Se si intende offrire nuove forme di rilevamento per gli ambienti Python, vedere [PTVS Environment Detection](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments) (Rilevamento degli ambienti PTVS) su github.com.

## <a name="managing-python-environments-in-visual-studio"></a>Gestione di ambienti Python in Visual Studio

Per aprire la finestra Ambienti Python, eseguire una delle operazioni seguenti:

1. Selezionare il comando di menu **Visualizza > Altre finestre > Ambienti Python**.
1. Fare clic con il pulsante destro del mouse su **Ambienti Python** per un progetto in Esplora soluzioni e scegliere **Visualizza tutti gli ambienti Python**:

    ![Comando Visualizza tutti gli ambienti Python in Esplora soluzioni](media/environments-view-all.png)
    
In entrambi i casi, la finestra Ambienti Python viene visualizzata come una scheda di pari livello in Esplora soluzioni:

![Finestra Ambienti Python](media/environments-default-view.png)

L'esempio precedente mostra che oltre a Python 3.4 (CPython a 32 bit) sono installate le versioni a 32 e a 64 bit di IronPython 2.7. In questo caso, l'ambiente predefinito in grassetto è Python 3.4, che verrà usato per tutti i nuovi progetti. Se l'elenco visualizzato non include tutti gli ambienti, significa che Python Tools for Visual Studio è installato in Visual Studio 2015 o versione precedente, ma non è stato installato un interprete Python (vedere sopra [Selezione e installazione di interpreti Python](#selecting-and-installing-python-interpreters)). 

> [!Tip]
> Quando la finestra **Ambienti Python* è ridotta, come illustrato in precedenza, gli ambienti vengono elencati nella parte superiore e le diverse schede nella parte inferiore. Se si espande sufficientemente la finestra, però verrà aperta una visualizzazione più ampia in cui è possibile lavorare più comodamente.
>
> ![Visualizzazione espansa della finestra Ambienti Python](media/environments-expanded-view.png)

> [!Note]
> Anche se Visual Studio rispetta l'opzione dei pacchetti dei siti di sistema, non consente di modificarla da Visual Studio.

### <a name="creating-an-environment-for-an-existing-interpreter"></a>Creazione di un ambiente per un interprete esistente

Visual Studio individua in genere la presenza di un interprete Python installato controllando il Registro di sistema, ma potrebbe non individuarla se l'interprete è installato in modalità non standard. In questi casi è possibile impostare Visual Studio in modo che punti direttamente all'interprete come illustrato di seguito:

1. Selezionare **+ Personalizzato** nella finestra Ambienti Python per creare un nuovo ambiente e aprire la [scheda **Configura**](#configure-tab) descritta di seguito.

    ![Visualizzazione predefinita per un nuovo ambiente personalizzato](media/environments-custom-1.png)

1. Immettere un nome per l'ambiente nel campo **Descrizione**.
1. Immettere o selezionare il percorso dell'interprete nel campo **Percorso di prefisso**.
1. Selezionare **Rilevamento automatico** per fare in modo che Visual Studio completi automaticamente i campi rimanenti oppure completarli manualmente.
1. Selezionare **Applica** per salvare l'ambiente.
1. Se è necessario rimuovere l'ambiente, selezionare il comando **Rimuovi** nella scheda **Configura**.

### <a name="overview-tab"></a>Scheda Panoramica

Include informazioni di base e comandi per l'ambiente, ad esempio per impostarlo come predefinito, aprire un [finestra interattiva (REPL)](interactive-repl.md) con tale ambiente e passare alla finestra di dialogo per configurare la finestra interattiva. È possibile eseguire queste operazioni anche selezionando il comando di menu **Strumenti > Opzioni**, **Strumenti Python > Finestre interattive** e infine il nome dell'ambiente.

![Scheda Panoramica di Ambienti Python](media/environments-overview-tab.png)

> [!Note]
> Se si cambia l'ambiente attivo, è possibile che Visual Studio non risponda per un breve periodo finché non viene caricato il database di IntelliSense. Gli ambienti che contengono molti pacchetti potrebbero non rispondere per un periodo più lungo.

### <a name="configure-tab"></a>Scheda Configura

Se visualizzata, contiene i dettagli descritti nella tabella seguente. Se questa scheda non è presente, Visual Studio gestisce automaticamente tutti i dettagli.

![Scheda Configura di Ambienti Python](media/environments-configure-tab.png)

| Campo | Descrizione |
| --- | --- |
| **Descrizione** | Nome da assegnare all'ambiente. |
| **Percorso di prefisso** | Percorso della cartella di base dell'interprete. Se si compila questo campo e si fa clic su **Rilevamento automatico**, Visual Studio prova a compilare automaticamente gli altri campi. |
| **Percorso dell'interprete** | Percorso del file eseguibile dell'interprete, costituito in genere dal percorso di prefisso seguito da `python.exe`. |
| **Interprete con finestra** | Percorso del file eseguibile non di console, spesso costituito dal percorso di prefisso seguito da `pythonw.exe`. |
| **Percorso della libreria** | Radice della libreria standard. Questo valore può essere ignorato se Visual Studio è in grado di richiedere un percorso più accurato all'interprete. |
| **Versione del linguaggio** | Selezionata dal menu a discesa. |
| **Architettura** | In genere rilevata e inserita automaticamente; in caso contrario, il valore da specificare è 32 bit o 64 bit. |
| **Variabile di ambiente del percorso** | Variabile di ambiente usata dall'interprete per trovare i percorsi di ricerca. All'avvio di Python, Visual Studio modifica il valore della variabile in modo che contenga i percorsi di ricerca del progetto. In genere questa proprietà deve essere impostata su `PYTHONPATH`, ma alcuni interpreti usano un valore diverso. |

### <a name="pip-tab"></a>Scheda pip

Consente di gestire i pacchetti installati nell'ambiente, nonché di cercare e installare quelli nuovi (incluse eventuali dipendenze). Oltre a cercare [PyPI](https://pypi.python.org), durante la ricerca verranno filtrati i pacchetti attualmente installati. È anche possibile immettere direttamente qualsiasi comando `pip install` nella casella di ricerca, compresi i flag, come `--user` o `--no-deps`.

![Scheda pip di Ambienti Python](media/environments-pip-tab.png)

### <a name="intellisense-tab"></a>Scheda IntelliSense

Mostra lo stato corrente del database di completamento IntelliSense:

![Scheda IntelliSense di Ambienti Python](media/environments-intellisense-tab.png)

Il database contiene i metadati relativi a tutte le librerie dell'ambiente e consente di migliorare la velocità di IntelliSense riducendo la memoria utilizzata. Quando Visual Studio rileva un nuovo ambiente (o ne viene aggiunto uno), avvia automaticamente la compilazione del database analizzando i file di origine della libreria. Questo processo può avvenire ovunque e richiedere da un minuto a oltre un'ora a seconda dei componenti installati. Anaconda include ad esempio molte librerie, di conseguenza la compilazione del database può richiedere molto tempo. Al termine dell'operazione, si otterranno informazioni IntelliSense dettagliate e non sarà necessario aggiornare di nuovo il database (con il pulsante **Aggiorna database**) fino a quando non si installano altre librerie.

Le librerie i cui dati non sono stati compilati vengono contrassegnate con un punto esclamativo (**!**). È presente un punto esclamativo (**!**) anche accanto al database di un ambiente non completo nell'elenco degli ambienti principale.

## <a name="global-environments"></a>Ambienti globali

Gli ambienti globali (o a livello di sistema) sono disponibili per tutti i progetti presenti in un computer. Visual Studio rileva in genere automaticamente gli ambienti globali, che vengono visualizzati nella finestra Ambienti Python. In caso contrario, è possibile aggiungere un ambiente manualmente come descritto in precedenza in [Gestione di ambienti Python in Visual Studio](#managing-python-environments-in-visual-studio).

Visual Studio usa l'ambiente predefinito per tutti i nuovi progetti per l'esecuzione, il debug, il controllo della sintassi, la visualizzazione di completamenti per importazioni e membri e per eventuali altre attività che richiedono un ambiente. La modifica dell'ambiente predefinito influirà su tutti i progetti per i quali non è stato aggiunto un [ambiente specifico del progetto](#project-specific-environments), come descritto di seguito.

## <a name="project-specific-environments"></a>Ambienti specifici del progetto

Gli ambienti specifici del progetto assicurano che un progetto venga sempre eseguito in un ambiente specifico, ignorando l'ambiente globale predefinito. Se ad esempio l'ambiente predefinito globale è CPython, ma per un progetto sono richiesti IronPython e alcune librerie non installate nell'ambiente globale, è necessario un ambiente specifico del progetto.

Gli ambienti di progetto sono elencati nel nodo Ambienti Python in Esplora soluzioni. La voce in grassetto è quella attualmente attiva e verrà usata per il debug, i completamenti per importazioni e membri, il controllo della sintassi e altre attività che richiedono un ambiente:

![Ambienti di progetto visualizzati in Esplora soluzioni](media/environments-project.png)

Per attivare un ambiente diverso per il progetto, fare clic con il pulsante destro del mouse sull'ambiente e scegliere **Attiva ambiente**.

Per aggiungere un qualsiasi ambiente globale come ambiente del progetto, fare clic con il pulsante destro del mouse su **Ambienti Python** e scegliere **Aggiungi/Rimuovi ambienti Python**. Nell'elenco visualizzato è possibile selezionare o deselezionare gli ambienti disponibili nel progetto.

![Finestra Aggiungi/Rimuovi ambienti Python](media/environments-add-remove.png)

In Esplora soluzioni è anche possibile espandere l'ambiente per visualizzarne i pacchetti installati, ovvero quelli che è possibile importare e usare nel codice quando l'ambiente è attivo:

![Pacchetti Python per un ambiente in Esplora soluzioni](media/environments-installed-packages.png)

Per installare nuovi pacchetti, fare clic con il pulsante destro del mouse sull'ambiente, scegliere **Installa pacchetto Python** e immettere il nome del pacchetto desiderato. I pacchetti e le dipendenze vengono scaricati dall'[indice dei pacchetti Python (PyPI)](https://pypi.python.org/pypi), in cui è anche possibile cercare i pacchetti disponibili. Le informazioni sull'installazione sono visualizzate sulla barra di stato e nella finestra di output di Visual Studio. Per disinstallare un pacchetto, fare clic con il pulsante del destro sul pacchetto e scegliere **Rimuovi**.

> [!Note]
> Il team di sviluppo Python principale sta attualmente lavorando allo sviluppo del supporto per la gestione di pacchetti di Python. È possibile che le voci visualizzate non siano sempre accurate e che l'installazione e la disinstallazione non siano disponibili o affidabili. Visual Studio usa la funzionalità di gestione dei pacchetti pip, se disponibile, scaricandola e installandola quando necessario. Visual Studio può anche usare la funzionalità di gestione pacchetti easy_install. Vengono visualizzati anche i pacchetti installati con pip o easy_install dalla riga di comando.

> [!Tip]
> Può capitare spesso che pip non riesca a installare un pacchetto quando questo include il codice sorgente per i componenti nativi in file `*.pyd`. Se non è installata la versione richiesta di Visual Studio, pip non riuscirà a compilare questi componenti. Il messaggio di errore visualizzato in questa situazione è `error: Unable to find vcvarsall.bat.` `easy_install` è spesso in grado di scaricare file binari precompilati ed è possibile scaricare un compilatore appropriato per le versioni precedenti di Python all'indirizzo [http://aka.ms/VCPython27](http://aka.ms/VCPython27). Per altre informazioni, vedere [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Come gestire l'errore "vcvarsallbat non trovato") nel blog del team degli strumenti Python.


## <a name="virtual-environments"></a>Ambienti virtuali

Dal momento che i pacchetti installati in un ambiente globale sono disponibili per tutti i progetti che usano tale ambiente, possono verificarsi conflitti quando due progetti richiedono versioni diverse dello stesso pacchetto o pacchetti non compatibili. Per evitare questi conflitti, Visual Studio consente di creare *ambienti virtuali*, che sono in genere specifici di un progetto.

Analogamente a qualsiasi altro ambiente Python, un ambiente virtuale è costituito da un interprete Python, da una libreria e da un set di pacchetti. In questo caso, però, l'ambiente virtuale usa l'interprete e la libreria di uno degli ambienti globali (purché supportino gli ambienti virtuali), mentre i pacchetti sono separati e isolati dall'ambiente globale e da tutti gli altri ambienti virtuali. Anche questa soluzione consente di evitare conflitti e di ridurre al minimo il footprint dell'ambiente virtuale, impostandolo sulle dimensioni approssimative dei relativi pacchetti. 

Per creare un ambiente virtuale:

1. Fare clic con il pulsante destro del mouse su **Ambienti Python** in Esplora soluzioni e scegliere **Aggiungi ambiente virtuale** per visualizzare la finestra seguente:

    ![Creazione di un ambiente virtuale](media/environments-add-virtual-1.png)

1. Specificare un nome per creare l'ambiente virtuale nel percorso di progetto oppure un percorso completo per crearlo altrove. Per garantire la massima compatibilità con altri strumenti, usare solo numeri e lettere nel nome.

1. Selezionare un ambiente globale come interprete di base e fare clic su **Crea**. Se i pacchetti `pip` e `virtualenv` o `venv` non sono disponibili, verranno scaricati e installati.

    Se il percorso specificato è un ambiente virtuale esistente, verrà rilevato l'interprete di base e il pulsante Crea diventerà **Aggiungi**:

    ![Aggiunta di un ambiente virtuale esistente](media/environments-add-virtual-2.png)

Per aggiungere un ambiente virtuale esistente, è anche possibile fare clic con il pulsante destro del mouse su **Ambienti Python** in Esplora soluzioni e scegliere **Aggiungi ambiente virtuale esistente**. Visual Studio rileva automaticamente l'interprete di base usando il file `orig-prefix.txt` nella directory `lib` dell'ambiente.

Dopo essere stato aggiunto al progetto, l'ambiente virtuale viene visualizzato nella finestra **Ambienti Python** ed è possibile attivarlo come qualsiasi altro ambiente, nonché gestirne i pacchetti. Se si fa clic con il pulsante destro del mouse sul progetto e si sceglie **Rimuovi**, è possibile rimuovere il riferimento all'ambiente oppure eliminare l'ambiente e tutti i relativi file sul disco, ma naturalmente non l'interprete di base.

Uno degli svantaggi degli ambienti virtuali è che contengono percorsi di file hardcoded, di conseguenza non possono essere facilmente condivisi o trasportati in altri computer di sviluppo. Per fortuna, è possibile usare il file `requirements.txt` come descritto nella sezione successiva.

## <a name="managing-required-packages"></a>Gestione dei pacchetti necessari

Se si condivide un progetto con altri utenti usando un sistema di compilazione oppure si intende [pubblicarlo in Microsoft Azure](template-azure-cloud-service.md), è necessario specificare i pacchetti esterni richiesti. L'approccio consigliato prevede l'uso di un [file requirements.txt](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files) (readthedocs.org), che contiene un elenco dei comandi per pip e che consentirà di installare le versioni richieste di pacchetti dipendenti.

Dal punto di vista tecnico, per tenere traccia dei requisiti è possibile usare un qualsiasi nome file (usando `-r <full path to file>` quando si installa un pacchetto), ma Visual Studio fornisce supporto specifico per `requirements.txt`:

- Se è stato caricato un progetto che contiene `requirements.txt` e si vogliono installare tutti i pacchetti elencati nel file, fare clic con il pulsante destro del mouse sul progetto e scegliere **Installa da requirements.txt**:

    ![Installa da requirements.txt](media/environments-requirements-txt-install.png)

- Quando tutti i pacchetti necessari sono installati in un progetto, è possibile fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere **Genera requirements.txt** per creare il file necessario. Se il file esiste già, verrà chiesto come aggiornarlo:

    ![Opzioni per l'aggiornamento di requirements.txt](media/environments-requirements-txt-replace.png)

    - **Sostituisci intero file**: rimuove tutti gli elementi, i commenti e le opzioni esistenti.
    - **Aggiorna voci esistenti**: rileva i requisiti del pacchetto e aggiorna gli identificatori di versione in base alla versione attualmente installata.
    - **Aggiorna e aggiungi voci**: aggiorna eventuali requisiti trovati e aggiunge tutti gli altri pacchetti alla fine del file.

Dal momento che i file `requirements.txt` servono a bloccare i requisiti del progetto, vengono indicate le versioni precise per tutti i pacchetti installati. In questo modo sarà possibile riprodurre facilmente l'ambiente in un altro computer. I pacchetti vengono inclusi anche se sono stati installati con un intervallo di versioni, come dipendenza di un altro pacchetto o con un programma di installazione diverso da pip.

Se, quando si aggiunge un nuovo ambiente virtuale, esiste un file ` requirements.txt`, nella finestra di dialogo **Aggiungi ambiente virtuale** viene visualizzata un'opzione per installare automaticamente i pacchetti, in modo da ricreare facilmente un ambiente in un altro computer:

![Creazione di un ambiente virtuale con requirements.txt](media/environments-requirements-txt.png)

Se pip non riesce a installare un pacchetto e questo è presente in un file `requirements.txt`, l'intera installazione non riuscirà. In questo caso, modificare manualmente il file in modo da escludere questo pacchetto oppure usare le [opzioni di pip](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format) in modo che facciano riferimento a una versione installabile del pacchetto. È ad esempio possibile che si preferisca usare [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html) per compilare una dipendenza e aggiungere l'opzione `--find-links <path>` al file `requirements.txt`:

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

# <a name="search-paths"></a>Percorsi di ricerca

Quando Python viene usato normalmente, il percorso di ricerca predefinito per i file di modulo viene fornito dalla variabile di ambiente `PYTHONPATH` (o `IRONPYTHONPATH` e così via). Quando si usa un'istruzione `import <name>`, quindi, Python cerca nome corrispondente prima nei moduli predefiniti, successivamente nella cartella che contiene il codice Python in esecuzione e infine nel percorso di ricerca del modulo definito dalla variabile di ambiente applicabile. Vedere [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Percorso di ricerca del modulo) e [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Variabili di ambiente) nella documentazione principale di Python.

La variabile di ambiente del percorso di ricerca viene però ignorata da Visual Studio, anche se è stata impostata per l'intero sistema. In realtà, viene ignorata proprio *perché* è impostata per l'intero sistema e non consente di fornire automaticamente una risposta a domande di questo tipo: i moduli di riferimento sono validi per Python 2.7 o per Python 3.3? Sostituiranno i moduli di libreria standard? Lo sviluppatore è a conoscenza di questo comportamento o si tratta di un tentativo di hijack effettuato da utenti malintenzionati?

Il supporto per Python in Visual Studio consente quindi di specificare direttamente i percorsi di ricerca sia negli ambienti che nei progetti. I percorsi vengono passati come valore di `PYTHONPATH` (o equivalente) quando si esegue il debug o si esegue lo script da Visual Studio. Quando si aggiungono percorsi di ricerca, Visual Studio controlla le librerie in questi percorsi e crea i database di IntelliSense corrispondenti. Questa operazione potrebbe richiedere alcuni minuti a seconda del numero di librerie.

Per aggiungere un percorso di ricerca, fare clic con il pulsante destro del mouse sull'elemento **Percorsi di ricerca** in Esplora soluzioni, scegliere **Aggiungi cartella al percorso di ricerca** e selezionare la cartella da includere. Questo percorso viene usato per qualsiasi ambiente associato al progetto.

È possibile aggiungere come percorsi di ricerca i file con estensione `.zip` o `.egg`, selezionando **Aggiungi archivio ZIP al percorso di ricerca**. Come con le cartelle, il contenuto di questi file viene analizzato e reso disponibile per IntelliSense.

> [!Note]
> È possibile aggiungere un percorso di ricerca ai moduli di Python 2.7 mentre si usa Python 3.3, ma potrebbero verificarsi errori.

Se si usa regolarmente gli stessi percorsi di ricerca e il contenuto non cambia spesso, può risultare più comodo eseguire l'installazione nella cartella dei pacchetti del sito. Questa verrà quindi analizzata e archiviata nel database di IntelliSense e sarà sempre associata all'ambiente di destinazione indicato. Non sarà inoltre più necessario aggiungere un percorso di ricerca per ogni progetto.

