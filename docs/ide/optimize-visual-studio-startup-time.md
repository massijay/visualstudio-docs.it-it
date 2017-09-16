---
title: Ottimizzare il tempo di avvio di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 8/31/2017
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
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Ottimizzare il tempo di avvio di Visual Studio
Idealmente, Visual Studio deve sempre essere avviato nel più breve tempo possibile. Tuttavia, estensioni di Visual Studio e finestre degli strumenti aperte possono influire negativamente sul tempo di avvio poiché vengono caricate automaticamente all'avvio. La finestra **Gestisci prestazioni di Visual Studio** consente di visualizzare le estensioni e le funzionalità che influiscono sul tempo di avvio di Visual Studio, nonché di controllarne il comportamento di caricamento.

Per suggerimenti generali su come migliorare le prestazioni, vedere [Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="control-startup-behavior"></a>Controllare il comportamento di avvio

Per evitare di prolungare il tempo di avvio, Visual Studio 2017 evita il caricamento delle estensioni all'avvio usando un approccio di caricamento su richiesta. Questo comportamento significa che le estensioni non si aprono subito dopo l'avvio di Visual Studio, ma all'occorrenza dopo l'avvio. Inoltre, poiché le finestre degli strumenti lasciate aperte in una sessione precedente di Visual Studio possono rallentare l'avvio, esse vengono aperte in un modo più intelligente per evitare di compromettere il tempo di avvio.

Se Visual Studio rileva un avvio lento, viene visualizzato un messaggio popup che comunica quale estensione o finestra degli strumenti provoca il rallentamento. Il messaggio include anche un collegamento alla finestra di dialogo **Gestire le prestazioni di Visual Studio**. È possibile aprire questa finestra anche usando il comando di menu **Guida > Gestisci prestazioni di Visual Studio**.

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

## <a name="speed_up_solution_load"></a>Caricare più rapidamente soluzioni di grandi dimensioni in Visual Studio 2017

Visual Studio 2017 introduce una nuova funzionalità denominata caricamento leggero delle soluzioni che riduce la quantità di tempo e memoria necessaria per caricare soluzioni di grandi dimensioni nell'IDE. Se si possiede una soluzione di grandi dimensioni contenente molti progetti C#, VB o C++, è probabile che l'abilitazione del caricamento leggero soluzioni produca sostanziali vantaggi in termini di prestazioni. Per informazioni dettagliate sui vantaggi di cui è possibile usufruire usando questa funzionalità, vedere [Ottimizzare il caricamento delle soluzioni](../ide/optimize-solution-loading-in-visual-studio).

> [!NOTE]
> Questo contenuto si applica a Visual Studio 2017 Update 3.

### <a name="enable-or-disable-lightweight-solution-load"></a>Abilitare o disabilitare il caricamento leggero delle soluzioni

È possibile fare clic con il pulsante destro del mouse sul nome della soluzione in Esplora soluzioni e selezionare **Abilita il caricamento leggero delle soluzioni**. Dopo aver selezionato l'opzione, è necessario chiudere e riaprire la soluzione per attivare il carico leggero delle soluzioni.

![Esplora soluzioni](../ide/media/VSIDE_LSL_Solution_Setting.png)

Per configurare le impostazioni globali per il carico leggero delle soluzioni, vedere [Ottimizzare il caricamento delle soluzioni](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings).

## <a name="see-also"></a>Vedere anche
[Suggerimenti sulle prestazioni di Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)

