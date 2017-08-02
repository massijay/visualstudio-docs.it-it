---
title: Ottimizzare il tempo di avvio di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/20/2017
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
ms.translationtype: HT
ms.sourcegitcommit: c3521e1de25854db012cb91bbe09d9463ecb42c7
ms.openlocfilehash: af1ff0dbeeb30e6b3169c6a94dab8da50085bf20
ms.contentlocale: it-it
ms.lasthandoff: 07/21/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Ottimizzare il tempo di avvio di Visual Studio
Idealmente, Visual Studio deve sempre essere avviato nel più breve tempo possibile. Tuttavia, estensioni di Visual Studio e finestre degli strumenti aperte possono influire negativamente sul tempo di avvio poiché vengono caricate automaticamente all'avvio. La finestra **Gestisci prestazioni di Visual Studio** consente di visualizzare le estensioni e le funzionalità che influiscono sul tempo di avvio di Visual Studio, nonché di controllarne il comportamento di caricamento.

## <a name="control-startup-behavior"></a>Controllare il comportamento di avvio

Per evitare di prolungare il tempo di avvio, Visual Studio 2017 evita il caricamento delle estensioni all'avvio usando un approccio di caricamento su richiesta. Questo comportamento significa che le estensioni non si aprono subito dopo l'avvio di Visual Studio, ma all'occorrenza dopo l'avvio. Inoltre, poiché le finestre degli strumenti lasciate aperte in una sessione precedente di Visual Studio possono rallentare l'avvio, esse vengono aperte in un modo più intelligente per evitare di compromettere il tempo di avvio.

Se Visual Studio rileva un avvio lento, viene visualizzato un messaggio popup che comunica quale estensione o finestra degli strumenti provoca il rallentamento. Il messaggio include anche un collegamento alla finestra di dialogo **Gestisci prestazioni di Visual Studio** che può essere aperta anche tramite il comando di menu **Guida > Gestisci prestazioni di Visual Studio**.

![Popup di Gestisci prestazioni di Visual Studio con il messaggio 'È stato notato che l'estensione ... rallenta Visual Studio'](../ide/media/vside_perfdialog_popup.png)

La finestra di dialogo elenca le estensioni e le finestre degli strumenti che compromettono le prestazioni di avvio. Questa finestra di dialogo consente di modificare le impostazioni delle estensioni e delle finestre degli strumenti per migliorare le prestazioni di avvio.

### <a name="change-extension-settings"></a>Modificare le impostazioni delle estensioni

Se un'estensione sta rallentando l'avvio di Visual Studio, essa viene visualizzata nella finestra di dialogo **Gestisci prestazioni di Visual Studio** quando si sceglie uno dei tipi di estensione. La finestra di dialogo mostra le estensioni che influiscono sulle prestazioni all'avvio, durante il caricamento di una soluzione e durante la digitazione nell'editor.

![Gestisci prestazioni di Visual Studio - visualizzazione delle estensioni](../ide/media/vside_perfdialog_extensions.png)

Se l'impatto sull'avvio, sul caricamento della soluzione o sui tempi di digitazione è eccessivamente elevato, è possibile disabilitare l'estensione per tale scenario selezionando il pulsante **Disabilita**. È sempre possibile riabilitare l'estensione per le sessioni future mediante il Gestore estensioni o la finestra di dialogo Gestisci prestazioni di Visual Studio.

### <a name="change-tool-window-settings"></a>Modificare le impostazioni della finestra degli strumenti

Se una finestra degli strumenti rallenta l'avvio di Visual Studio e si vuole modificare l'impatto, è possibile modificarne il comportamento scegliendo una di due opzioni al posto di **Usa comportamento predefinito**:

- **Non visualizzare la finestra all'avvio:** la finestra degli strumenti specificata viene sempre chiusa alla successiva apertura di Visual Studio, anche se era stata lasciata aperta in una sessione precedente. È possibile aprire la finestra degli strumenti dal menu appropriato.
- **Nascondi automaticamente la finestra all'avvio:** se una finestra degli strumenti è stata lasciata aperta in una sessione precedente, questa opzione consente di comprimere il gruppo della finestra degli strumenti all'avvio per evitarne l'inizializzazione. Questa opzione è una scelta ottimale se si usa spesso una finestra degli strumenti, poiché la finestra degli strumenti rimane disponibile senza compromettere il tempo di avvio di Visual Studio.

![Gestisci prestazioni di Visual Studio - visualizzazione delle finestre degli strumenti](../ide/media/vside_perfdialog_toolwindows.png)

È sempre possibile tornare a questa finestra di dialogo in qualsiasi momento per modificare l'impostazione per qualsiasi finestra degli strumenti.

## <a name="speed-up-solution-load"></a>Velocizzare il caricamento della soluzione

Visual Studio 2017 supporta il **caricamento leggero delle soluzioni** che riduce la quantità di tempo e memoria necessari per caricare soluzioni di grandi dimensioni nell'IDE. Per una soluzione di grandi dimensioni contenente molti progetti C#, VB e/o C++, è probabile che l'abilitazione del caricamento leggero delle soluzioni produca sostanziali vantaggi in termini di prestazioni.

Poiché alcune funzionalità IDE non sono completamente disponibili quando è abilitato il caricamento leggero soluzioni, la funzionalità è disattivata per impostazione predefinita. Le sezioni seguenti consentono di decidere se abilitare o meno questa funzionalità.

### <a name="enable-lightweight-solution-load"></a>Abilitare il caricamento leggero soluzioni

È possibile abilitare il caricamento leggero soluzioni per l'IDE nel suo insieme o per singole soluzioni.

Per modificare le impostazioni per il caricamento leggero delle soluzioni per tutti i progetti e le soluzioni, passare a **Strumenti > Opzioni > Progetti e soluzioni > Generale** e selezionare una delle tre opzioni di caricamento:

![Finestra di dialogo Strumenti Opzioni](../ide/media/VSIDE_LightweightSolutionLoad.png)

- **Consenti a Visual Studio di scegliere l'opzione migliore per la soluzione**: Visual Studio determina se applicare il caricamento leggero delle soluzioni analizzando ogni soluzione all'apertura. 
- **Abilita:** il caricamento leggero delle soluzioni viene abilitato per questa soluzione indipendentemente dall'impostazione a livello di IDE.
- **Disabilita:** il caricamento leggero delle soluzioni viene disabilitato per questa soluzione indipendentemente dall'impostazione a livello di IDE.

Per abilitare il caricamento leggero delle soluzioni per una singola soluzione, selezionare il nodo della soluzione di primo livello in Esplora soluzioni. Nella finestra **Proprietà** scegliere **Predefinito**, **Abilitato** o **Disabilitato** per la proprietà **Caricamento leggero**.

![Esplora soluzioni](../ide/media/VSIDE_LSL Solution Setting.png)

È anche possibile fare clic con il pulsante destro del mouse sul nodo della soluzione di primo livello in Esplora soluzioni e scegliere **Abilita il caricamento leggero delle soluzioni** (se la funzionalità è attualmente disabilitata) o **Disabilita il caricamento leggero delle soluzioni** (se la funzionalità è attualmente abilitata):

Quando si modifica l'impostazione del caricamento leggero soluzioni, la modifica diventa effettiva al successivo caricamento della soluzione. Non è necessario riavviare l'IDE.

### <a name="automatically-enable-lightweight-solution-load"></a>Abilitare automaticamente il caricamento leggero soluzioni

Quando si apre una soluzione di grandi dimensioni in Visual Studio 2017, potrebbe essere visualizzato un messaggio popup che propone di abilitare il caricamento leggero soluzioni. Il messaggio viene visualizzato solo per le soluzioni che contengono molti progetti C#, VB o C++. La scelta di **Abilita** attiva il caricamento leggero delle soluzioni solo per quella soluzione. L'impostazione a livello di IDE non viene cambiata.

![Finestra popup](../ide/media/VSIDE_LSL Popup.png)

È possibile disabilitare il caricamento leggero delle soluzioni in un secondo momento nella finestra **Proprietà** della soluzione.

### <a name="limitations"></a>Limitazioni

La maggior parte delle funzionalità dell'IDE sono completamente disponibili quando è abilitato il caricamento leggero soluzioni. Alcune funzionalità dell'IDE e le estensioni di terze parti potrebbero tuttavia non essere completamente compatibili.  Le funzionalità seguenti non funzionano quando è abilitato il caricamento leggero soluzioni:

- Alcune estensioni di terze parti potrebbero non comportarsi come previsto quando è abilitato il caricamento leggero delle soluzioni.
- Modifica e continuazione non funziona nei progetti che non vengono caricati quando si avvia il debug. I file contenuti in tali progetti sono di sola lettura e se viene tentata una modifica un errore segnala che il progetto non è stato caricato.
- Quando è abilitato il caricamento leggero delle soluzioni, è possibile che i progetti F# non vengano compilati correttamente e che i simboli non siano completamente disponibili in GoTo.

