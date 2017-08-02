---
title: Ottimizzare il tempo di avvio di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 01/09/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
f1_keywords:
- vs.performancecenter
translationtype: Human Translation
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 27a265dbbb1f9426ba2dd254095c84239bbd0db7
ms.lasthandoff: 03/07/2017

---
# <a name="optimize-visual-studio-startup-time"></a>Ottimizzare il tempo di avvio di Visual Studio
Idealmente, Visual Studio deve sempre essere avviato nel più breve tempo possibile. Tuttavia, estensioni di Visual Studio e finestre degli strumenti aperte possono influire negativamente sul tempo di avvio poiché vengono caricate automaticamente all'avvio. La finestra **Gestisci prestazioni di Visual Studio** consente non solo di visualizzare le estensioni e le funzionalità che influiscono sul tempo di avvio di Visual Studio, ma anche di determinarne il comportamento di caricamento in modo da avere un maggior controllo sulla velocità di avvio di Visual Studio.

## <a name="control-startup-behavior"></a>Controllare il comportamento di avvio

Per evitare di prolungare il tempo di avvio, Visual Studio 2017 evita il caricamento delle estensioni all'avvio usando un approccio di caricamento su richiesta. Ciò significa che le estensioni non si aprono subito dopo l'avvio di Visual Studio, aprendosi invece in modo asincrono in base alle esigenze dopo l'avvio. Inoltre, poiché le finestre degli strumenti lasciate aperte in una sessione precedente di Visual Studio possono rallentare l'avvio, esse vengono aperte in un modo più intelligente per evitare di compromettere il tempo di avvio.

Se Visual Studio rileva un avvio lento, viene visualizzato un messaggio popup che comunica quale estensione o finestra degli strumenti provoca il rallentamento. Il messaggio include anche un collegamento alla finestra di dialogo **Gestisci prestazioni di Visual Studio** che elenca le estensioni e le finestre degli strumenti che compromettono le prestazioni di avvio. Questa finestra di dialogo consente di modificare le impostazioni delle estensioni e delle finestre degli strumenti per migliorare le prestazioni di avvio.

![Gestisci prestazioni di Visual Studio -finestra popup](~/docs/ide/media/vside_perfdialog_popup.PNG "Gestisci prestazioni di Visual Studio - finestra popup")

La finestra di dialogo **Gestisci prestazioni di Visual Studio** include due categorie: **Estensioni** e **Finestre degli strumenti**.

### <a name="control-extensions"></a>Controllare le estensioni
Se un'estensione sta rallentando l'avvio di Visual Studio, essa viene visualizzata nella finestra di dialogo **Gestisci prestazioni di Visual Studio** quando si sceglie uno dei tipi di estensione. Se l'impatto sul tempo di avvio (indicato nella sezione **Impatto**) è eccessivamente elevato, è possibile scegliere di disabilitare sempre l'estensione all'avvio scegliendo il pulsante **Disabilita**. È possibile riabilitare l'estensione per le sessioni future mediante il Gestore estensioni o la finestra di dialogo Gestisci prestazioni di Visual Studio.

![Gestisci prestazioni di Visual Studio -estensioni](~/docs/ide/media/vside_perfdialog_extensions.PNG "Gestisci prestazioni di Visual Studio - estensioni")

Oltre alle estensioni di avvio, è anche possibile disabilitare le estensioni caricate mentre vengono caricate le soluzioni o mentre un utente digita. Scegliere lo scenario per visualizzare un elenco delle estensioni associate.

### <a name="control-tool-windows"></a>Controllare le finestre degli strumenti
Se una finestra degli strumenti sta rallentando l'avvio di Visual Studio, è possibile scegliere di lasciare il comportamento predefinito (senza alcun vantaggio per la velocità di avvio) oppure ignorarlo scegliendo uno dei due comportamenti seguenti:

- **Non visualizzare la finestra all'avvio:** se si sceglie questa opzione, la finestra degli strumenti specificata verrà sempre chiusa all'apertura di Visual Studio, anche se era stata lasciata aperta in una sessione precedente. È possibile aprire la finestra degli strumenti dal menu.
- **Nascondi automaticamente la finestra all'avvio:** se una finestra degli strumenti è stata lasciata aperta in una sessione precedente, scegliendo questa opzione il gruppo della finestra degli strumenti viene compresso all'avvio per evitarne l'inizializzazione. Questa è una scelta ottimale se si usa spesso una finestra degli strumenti, poiché la finestra degli strumenti rimane disponibile senza compromettere il tempo di avvio di Visual Studio.

![Gestisci prestazioni di Visual Studio -finestre degli strumenti](~/docs/ide/media/vside_perfdialog_toolwindows.PNG "Gestisci prestazioni di Visual Studio - finestre degli strumenti")

Se successivamente si cambia idea, è possibile ripristinare una qualsiasi di queste opzioni nella finestra di dialogo **Gestisci prestazioni di Visual Studio**. Per aprire la finestra di dialogo **Gestisci prestazioni di Visual Studio**, nella barra dei menu scegliere **Guida**, **Gestisci prestazioni di Visual Studio**.

## <a name="speed-up-solution-load"></a>Velocizzare il caricamento della soluzione

Visual Studio 2017 introduce una nuova funzionalità denominata **caricamento leggero soluzioni** che riduce la quantità di tempo e memoria necessari per caricare le soluzioni di grandi dimensioni nell'IDE. Se si possiede una soluzione di grandi dimensioni contenente molti progetti C#, VB o C++, è probabile che l'abilitazione del caricamento leggero soluzioni produca sostanziali vantaggi in termini di prestazioni.

Poiché alcune funzionalità IDE non sono completamente disponibili quando è abilitato il caricamento leggero soluzioni, la funzionalità è disattivata per impostazione predefinita. Le sezioni seguenti consentono di decidere se abilitare o meno questa funzionalità.

### <a name="enable-lightweight-solution-load"></a>Abilitare il caricamento leggero soluzioni

È possibile abilitare il caricamento leggero soluzioni per l'IDE nel suo insieme o per singole soluzioni. Per abilitare il caricamento leggero soluzioni per l'intero IDE, andare a **Strumenti**, **Opzioni** e quindi passare alla sezione **Progetti e soluzioni**.

![Finestra di dialogo Strumenti Opzioni](~/docs/ide/media/VSIDE_LightweightSolutionLoad.png)

Per abilitare il caricamento leggero soluzioni per una singola soluzione, scegliere il nodo della soluzione di livello superiore in Esplora soluzioni.  Nella finestra Proprietà, scegliere uno dei seguenti valori per la proprietà **Caricamento leggero**.

- **Abilitato:** il caricamento leggero soluzioni verrà abilitato per questa soluzione indipendentemente dall'impostazione a livello di IDE.
- **Disabilitato:** il caricamento leggero soluzioni verrà disabilitato per questa soluzione indipendentemente dall'impostazione a livello di IDE.
- **Valore predefinito:** il comportamento del caricamento leggero soluzioni verrà rinviato all'impostazione a livello di IDE.

![Esplora soluzioni](~/docs/ide/media/VSIDE_LSL Solution Setting.png)

Quando si modifica l'impostazione del caricamento leggero soluzioni, la modifica diventa effettiva al successivo caricamento della soluzione. Non è necessario riavviare l'IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Abilitare automaticamente il caricamento leggero soluzioni

Quando si apre una soluzione di grandi dimensioni in Visual Studio 2017, potrebbe essere visualizzato un messaggio popup che propone di abilitare il caricamento leggero soluzioni. Il messaggio viene visualizzato solo per le soluzioni che contengono molti progetti C#, VB o C++. Se si sceglie di **abilitare** il comando, il caricamento leggero soluzioni viene abilitato soltanto per quella soluzione. L'impostazione a livello di IDE non cambierà.

![Finestra popup](~/docs/ide/media/VSIDE_LSL Popup.png)

È possibile disabilitare il caricamento leggero soluzioni in un secondo momento nella finestra Proprietà della soluzione.

### <a name="lightweight-solution-load-limitations"></a>Limiti del caricamento leggero soluzioni
La maggior parte delle funzionalità dell'IDE sono completamente disponibili quando è abilitato il caricamento leggero soluzioni. Alcune funzionalità dell'IDE e le estensioni di terze parti potrebbero tuttavia non essere completamente compatibili.  Le funzionalità seguenti non funzionano quando è abilitato il caricamento leggero soluzioni:

#### <a name="third-party-extensions"></a>Estensioni di terze parti
Alcune estensioni potrebbero non comportarsi come previsto quando è abilitato il Caricamento leggero soluzioni.

#### <a name="edit-and-continue"></a>Modifica e continuazione
Modifica e continuazione non funziona nei progetti che non vengono caricati quando si avvia il debug. I file contenuti in tali progetti saranno di sola lettura e se viene tentata una modifica un errore segnala che il progetto non è stato caricato.

#### <a name="f-support"></a>Supporto per F#
Quando è abilitato il caricamento leggero delle soluzioni, è possibile che i progetti F# non vengano compilati correttamente e che i simboli non siano completamente disponibili in GoTo.

