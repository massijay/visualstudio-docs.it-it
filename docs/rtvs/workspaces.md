---
title: Aree di lavoro in R Tools per Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: it-it
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>Controllo della posizione di esecuzione del codice R con le aree di lavoro

Un'area di lavoro in R Tools per Visual Studio (RTVS) consente di configurare la posizione di esecuzione di una sessione R, che può essere eseguita sia su computer locali che su computer remoti. L'obiettivo è offrire un'esperienza utente simile in entrambi i casi, anche grazie all'uso di computer più potenti nel cloud.

Per aprire la finestra **Aree di lavoro** usare il comando **R Tools > Finestre > Aree di lavoro** o premere Ctrl+9.

![Finestra Aree di lavoro in R Tools per Visual Studio (VS2017)](~/rtvs/media/workspaces-window.png)

In questa finestra il segno di spunta verde indica l'area di lavoro attiva alla quale è associato RTVS. Selezionare una freccia blu per impostare l'area di lavoro attiva. L'icona delle impostazioni (a forma di ingranaggio) sulla destra di ogni area di lavoro consente di modificare il nome, il percorso e gli argomenti della riga di comando dell'area di lavoro. La X rossa rimuove un'area di lavoro aggiunta manualmente.

Contenuto dell'argomento:

- [Salvataggio e reimpostazione di un'area di lavoro](#saving-and-resetting-a-workspace)
- [Aree di lavoro locali](#local-workspaces)
- [Aree di lavoro remote](#remote-workspaces)
- [Passaggio da un'area di lavoro all'altra](#switching-between-workspaces)
- [Directory sui computer locali e remoti](#directories-on-local-and-remote-computers)
- [Copia di file di progetto in aree di lavoro remote](#copying-project-files-to-remote-workspaces)
- [Copia di file da un'area di lavoro remota](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Salvataggio e reimpostazione di un'area di lavoro

Per impostazione predefinita lo stato dell'area di lavoro non viene salvato quando si chiude e si riapre un progetto in RTVS. È tuttavia possibile modificare questa funzionalità mediante le [opzioni dell'area di lavoro](options.md#workspace).

Il comando **R Tools > Sessione > Reimposta** e il pulsante di reimpostazione della barra degli strumenti nella finestra interattiva consentono di reimpostare lo stato dell'area di lavoro in qualsiasi momento. Per le aree di lavoro remote la reimpostazione elimina il profilo utente creato alla prima connessione al server remoto e di fatto elimina anche tutti i file accumulati nel server remoto.

## <a name="local-workspaces"></a>Aree di lavoro locali

Nell'elenco delle aree di lavoro locali vengono visualizzati tutti gli interpreti R installati nel computer in uso. 

RTVS prova a rilevare automaticamente tutte le versioni di R installate, esaminando la chiave del Registro di sistema `HKEY_LOCAL_MACHINE\Software\R-Core\` all'avvio di Visual Studio. Poiché questo controllo viene effettuato solo all'avvio, se si installa un nuovo interprete R è necessario riavviare Visual Studio.

È possibile che un interprete R installato in modo non standard (ad esempio copiando direttamente i file in una cartella invece di eseguire un programma di installazione) non venga rilevato. In questo caso creare manualmente una nuova area di lavoro R locale come segue:

1. Selezionare il pulsante **Aggiungi** nella finestra Aree di lavoro.
1. Immettere un nome per la nuova area di lavoro.
1. Immettere il percorso della cartella radice R, che contiene la cartella `bin` con l'interprete. Immettere anche eventuali argomenti della riga di comando facoltativi da passare all'interprete all'avvio di RTVS.
1. Al termine selezionare **Salva**.

![Aggiunta di una nuova area di lavoro](~/rtvs/media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Aree di lavoro remote

Le aree di lavoro remote consentono di connettersi a una sessione R in un computer remoto. Per informazioni su come configurare un computer a questo scopo, vedere [Impostazione di aree di lavoro remote](workspaces-remote-setup.md).

Le aree di lavoro remote non vengono rilevate automaticamente da RTVS, pertanto è necessario aggiungerle manualmente con il pulsante **Aggiungi** nella finestra Aree di lavoro come descritto nella sezione precedente. In questo caso immettere l'URI del computer remoto anziché un percorso locale.

> [!Important]
> Le aree di lavoro remote sono identificate da un URI che *deve usare il protocollo HTTPS* per garantire la riservatezza e l'integrità delle comunicazioni con il computer remoto. RTVS non si connetterà a un computer remoto che non supporta HTTPS.

> [!Note]
> Le aree di lavoro remote sono una funzionalità in anteprima. È in corso l'elaborazione di un approccio migliore al problema della sincronizzazione file per una versione successiva. Sono benvenuti i commenti e i suggerimenti per migliorare l'usabilità.


## <a name="switching-between-workspaces"></a>Passaggio da un'area di lavoro all'altra

RTVS è associato a una sola area di lavoro alla volta, affiancata da un piccolo segno di spunta verde nella finestra Aree di lavoro. Per impostazione predefinita, RTVS esegue l'associazione all'ultima area di lavoro locale aperta in una sessione precedente.

Per cambiare l'area di lavoro attiva, selezionare la freccia blu accanto all'area di lavoro desiderata. Viene richiesto di salvare la sessione e l'area di lavoro corrente viene chiusa, quindi viene attivata la nuova area di lavoro.

> [!Tip]
> Per disattivare la richiesta di salvataggio selezionare il comando **R Tools > Opzioni** e impostare l'opzione **Mostra finestra di conferma prima di passare da un'area di lavoro all'altra** su `No`. Vedere [Opzioni dell'area di lavoro](options.md#workspace).

Se si prova a passare a un'area di lavoro locale che è stata disinstallata o a un'area di lavoro remota non disponibile, possono verificarsi situazioni in cui un progetto RTVS non è associato a nessuna area di lavoro. Di conseguenza, quando si immette codice nella finestra interattiva o si prova a eseguire codice con altri metodi potrebbe essere visualizzato un errore simile al seguente. Per risolvere il problema è sufficiente passare a un'altra area di lavoro nella finestra Aree di lavoro. Se non è disponibile nessuna area di lavoro, è necessario installare un interprete R. È anche possibile provare a riavviare Visual Studio se è stato installato un interprete durante l'esecuzione di Visual Studio.

![Errore quando nessuna area di lavoro è associata a RTVS](~/rtvs/media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>Passaggio a un'area di lavoro remota

Quando in RTVS si esegue per la prima volta la connessione a un'area di lavoro remota vengono richieste le credenziali, che vengono quindi memorizzate nella cache (tramite la Casella di sicurezza delle credenziali di Windows) per le sessioni successive. Le comunicazioni con il server remoto vengono quindi eseguite in modo sicuro su HTTPS (obbligatorio).

A seconda della configurazione del server, è possibile che venga visualizzato un avviso relativo al certificato: "Il certificato di sicurezza presentato da Remote R Services non consente di dimostrare che l'utente sia effettivamente connesso al computer (nome)".

![Avviso di certificato autofirmato durante la connessione a un'area di lavoro remota](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

Il certificato è un documento che viene presentato a RTVS dal computer a cui si prova a connettersi. Il certificato contiene un campo che identifica l'URI di tale computer. L'avviso viene visualizzato quando in RTVS viene rilevata una mancata corrispondenza tra l'URI del certificato e l'URI usato per la connessione al computer, indice di una possibile violazione della sicurezza del server.

Questo avviso viene tuttavia visualizzato anche quando si usa un *certificato autofirmato* anziché un certificato di un provider attendibile per abilitare HTTPS sul computer remoto. Per altre informazioni, vedere [Impostazione di aree di lavoro remote](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Directory sui computer locali e remoti

Per impostazione predefinita, quando si avvia un nuovo interprete R in un'area di lavoro locale la directory di lavoro corrente è `%userprofile%\Documents`. È possibile cambiare directory in qualsiasi momento mediante il comando **R Tools > Directory di lavoro** o facendo clic con il pulsante destro del mouse in Esplora soluzioni di Visual Studio e selezionando un comando come **Imposta directory di lavoro qui**.

Nei computer remoti RTVS crea automaticamente un profilo utente basato sulle credenziali usate per l'accesso iniziale al server, pertanto la directory di lavoro è la cartella `Documents` nel percorso di quel profilo. Il profilo viene usato per tutte le sessioni remote successive che usano le stesse credenziali. 

Di conseguenza la posizione esatta in cui viene eseguito il codice può essere diversa nelle aree di lavoro locali e remote. Evitare quindi di usare nel codice percorsi assoluti per file di dati ed elementi simili, perché il codice potrebbe non essere portabile tra le aree di lavoro. È preferibile usare percorsi relativi.

Si noti anche che con le aree di lavoro remote tutti i file presenti nella directory di lavoro vengono mantenuti tra le diverse sessioni eseguite con lo stesso profilo utente. Come indicato in precedenza, quando si usa un'area di lavoro remota è possibile eliminare questi file con il comando **R Tools > Sessione > Reimposta** o con il pulsante di reimpostazione nella finestra interattiva. Questa operazione elimina il profilo utente dal server. Il profilo viene creato di nuovo quando si torna a connettersi.

## <a name="copying-project-files-to-remote-workspaces"></a>Copia di file di progetto in aree di lavoro remote

Quando si lavora con progetti R in Visual Studio, i file di progetto più recenti si trovano sempre nel computer locale, anche quando si usa un'area di lavoro remota. In altri termini quando si apre un progetto in Visual Studio (il che in genere equivale ad aprire una soluzione contenente tale progetto), RTVS presuppone che il contenuto del progetto risieda interamente nel computer locale. L'area di lavoro remota è di fatto solo un host temporaneo per i file del progetto e l'eventuale output del codice. Ciò significa ad esempio che quando si carica un file usando `source` nella finestra interattiva, tale file deve già essere presente sul computer remoto nel percorso specificato o deve trovarsi nella directory di lavoro corrente dell'interprete R remoto (impostato con la funzione `setwd()`).

I file vengono copiati nel server remoto come indicato di seguito:

- Per lavorare con i file in modalità remota tramite la finestra interattiva è necessario copiarli manualmente facendo clic con il pulsante destro del mouse su di essi (o sul progetto) in Esplora Soluzioni e scegliendo **Source Selected ** (**Origine selezionata**). I file singoli vengono copiati nella directory di lavoro sul server. Se si copia un progetto viene creata una cartella per il progetto sul server.

- È anche possibile copiare i file selezionandoli in Esplora soluzioni, quindi scegliendo **File di origine selezionati**. Con questa operazione i file vengono caricati nella finestra interattiva ed eseguiti in tale posizione. Se la sessione è connessa a un computer remoto, i file vengono in primo luogo copiati in tale computer.

- Quando RTVS è associato a un'area di lavoro remota e si preme F5, si seleziona **Debug > Avvia debug** o si avvia in un altro modo l'esecuzione del codice, per impostazione predefinita il file del progetto viene copiato automaticamente nell'area di lavoro remota (vedere di seguito informazioni su come gestire questa impostazione).

- Tutti i file già esistenti nel server vengono sovrascritti.

> [!Note]
> Dato che RTVS non intercetta in modo affidabile tutte le chiamate di funzione R, la chiamata di funzioni quali `source()` o `runApp()` (per le applicazioni Shiny) dall'interno della finestra interattiva *non* copia i file nell'area di lavoro remota.

Le [proprietà del progetto](projects.md#project-properties) determinano se i file vengono copiati quando si esegue un progetto e quali file vengono copiati. Per aprire la pagina corrispondente selezionare il comando **Progetto > Proprietà (nome)** o fare clic con il pulsante destro del mouse in Esplora soluzioni e selezionare **Proprietà**.

![Scheda di esecuzione delle proprietà del progetto con le impostazioni di trasferimento file](~/rtvs/media/workspaces-remote-file-transfer-filter-settings.png)

L'opzione **Transfer files on run** (Trasferisci file all'esecuzione) determina se i file di progetto vengono copiati automaticamente. Il valore **Files to transfer** (File da trasferire) consente quindi di filtrare con precisione i file da trasferire. Per impostazione predefinita vengono copiati solo i file `.R`, `.Rmd`, `.sql`, `.md` e `.cpp`. In tal modo si evita la copia accidentale di file di dati di grandi dimensioni nel server a ogni esecuzione. 

## <a name="copying-files-from-a-remote-workspace"></a>Copia di file da un'area di lavoro remota

Se lo script R genera file nel server, è possibile copiare tali file nel client con la funzione `rtvs::fetch_file`. Questa funzione accetta come argomento minimo il percorso remoto del file da copiare nel proprio computer e come argomento facoltativo il percorso in cui copiare tale file nel computer. Se non si specifica un percorso il file viene copiato nella cartella `%userprofile%\Downloads`.

