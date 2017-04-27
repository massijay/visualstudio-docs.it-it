---
title: Usare i parametri della riga di comando per installare Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
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
ms.sourcegitcommit: 2a6555eb9c0a88b1533428cf2aa932b3fc4960ec
ms.openlocfilehash: e8ddcebccc5a8a949c75a33de6732d42134e6445
ms.lasthandoff: 03/30/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Usare i parametri della riga di comando per installare Visual Studio 2017
Quando si installa Visual Studio 2017 da un prompt dei comandi, è possibile usare diversi parametri della riga di comando per controllare o personalizzare l'installazione. Dalla riga di comando è possibile:
- avviare l'installazione con determinate opzioni preselezionate, 
- automatizzare il processo di installazione,
- creare una cache (layout) dei file di installazione per riutilizzarli in seguito. 

Insieme alle opzioni della riga di comando viene usato il programma di bootstrap dell'installazione, ovvero un file di dimensioni ridotte (circa 1 MB) che avvia il processo di download. Il programma di bootstrap è il primo eseguibile che viene avviato quando si esegue il download dal sito di Visual Studio. Fare clic sui collegamenti seguenti per accedere direttamente al programma di bootstrap della versione più recente per l'edizione del prodotto da installare:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Elenco dei parametri della riga di comando  
 Per i parametri della riga di comando di Visual Studio non viene fatta distinzione tra maiuscole e minuscole.

>  Sintassi: `vs_enterprise.exe [command] <options>...`

(sostituire `vs_enterprise.exe` con l'edizione del prodotto da installare)

| **Comando** | **Descrizione** |
| ----------------------- | --------------- | 
| (vuoto) | Installa il prodotto. | 
| ```modify``` | Modifica un prodotto installato. |
| ```update``` | Aggiorna un prodotto installato. |
| ```repair``` | Ripristina un prodotto installato. |
| ```uninstall``` | Disinstalla un prodotto installato. |


| **Opzione di installazione** | **Descrizione** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | La directory di installazione per l'istanza su cui intervenire. Per il comando di installazione, si tratta della posizione in cui verrà installata l'istanza. Per gli altri comandi, si tratta della posizione in cui era installata l'istanza installata in precedenza. |
| ```--layout <dir>``` | **Facoltativa**: specifica una directory per creare una cache di installazione offline. Selezionando questa opzione verrà aggiunta in modo implicito anche l'opzione '--wait'. Se viene chiamato da un file batch, questo comando verrà completato prima che l'esecuzione passi al comando successivo del file batch. |
| ```--lang <language-locale>``` *[&#60;language-locale&#62; ...]* | **Facoltativa**: viene usata con --layout per preparare una cache di installazione offline con i pacchetti di risorse con le lingue specificate. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| ```--addProductLang <language-locale>``` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da installare nel prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Se non è presente, l'installazione userà le impostazioni locali del computer. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| ```--removeProductLang <language-locale>``` | **Facoltativa**: durante un'operazione di installazione o modifica, determina i Language Pack dell'interfaccia utente da rimuovere dal prodotto. Può essere presente più volte nella riga di comando se vengono aggiunti più Language Pack. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|
| ```--add <workload or component ID>``` *[&#60;workload or component ID&#62; ...]* | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite '--includeRecommended' e/o '--includeOptional'. Per un controllo più capillare, è possibile aggiungere ';includeRecommended' e/o ';includeOptional' all'ID artefatto (ad esempio, '--add Workload1;includeRecommended' o '--add Workload2;includeOptional;includeRecommended'). Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md).|
| ```--remove <workload or component ID>``` *[&#60;workload or component ID&#62; ...]* | **Facoltativa**: uno o più ID di carichi di lavoro o componenti da rimuovere. Per altre informazioni, vedere la pagina [ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md).|
| ```--in <path>``` | **Facoltativa**: URI o percorso di un file di risposta.  |
| ```--all``` | **Facoltativa**: se devono essere installati tutti i carichi di lavoro e i componenti per un prodotto. |
| ```--allWorkloads``` | **Facoltativa**: installa tutti i carichi di lavoro e i componenti necessari, nessun componente consigliato o facoltativo. |
| ```--includeRecommended``` | **Facoltativa**: include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con --allWorkloads o --add. |
| ```--includeOptional``` | **Facoltativa**: include i componenti facoltativi per tutti i carichi di lavoro installati, ma non i componenti consigliati. I carichi di lavoro sono specificati con --allWorkloads o --add.  |
| ```--quiet, -q``` | **Facoltativa**: consente di non visualizzare alcuna interfaccia utente durante l'installazione. |
| ```--passive, -p``` | **Facoltativa**: consente di visualizzare l'interfaccia utente, senza richiedere alcuna interazione da parte dell'utente. |
| ```--norestart``` | **Facoltativa**: se presente, i comandi con --passive o --quiet non riavviano automaticamente il computer (se richiesto). Viene ignorata se non vengono specificate né --passive né --quiet.  |
| ```--nickname <name>``` | **Facoltativa**: definisce il nome alternativo da assegnare a un prodotto installato. La lunghezza del nome alternativo non può superare i 10 caratteri.  |
| ```--productKey``` | **Facoltativa**: definisce il codice Product Key da usare per un prodotto installato. È composto da 25 caratteri alfanumerici in formato 'xxxxx-xxxxx-xxxxx-xxxxx-xxxxx' o 'xxxxxxxxxxxxxxxxxxxxxxxxx'. |
| ```--help, --?, -h, -?``` | Visualizza una versione offline di questa pagina. |

> Nota: quando si specificano più carichi di lavoro e componenti, è necessario ripetere l'opzione della riga di comando `--add` o `--remove` per ogni elemento.

| **Opzioni di installazione avanzate** | **Descrizione** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | **Facoltativa**: ID del canale per l'istanza che verrà installata. È obbligatorio per il comando di installazione e viene ignorato per gli altri comandi se è specificata l'opzione --installPath. |
| ```--channelUri <uri>``` | **Facoltativa**: URI del manifesto del canale. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| ```--installChannelUri <uri>``` | **Facoltativa**: URI del manifesto del canale da usare per l'installazione. L'URI specificato da --channelUri (che deve essere specificata quando si specifica --installChannelUri) verrà usato per rilevare gli aggiornamenti. Se non si vuole ricevere gli aggiornamenti, è necessario specificare --channelUri senza un argomento. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| ```--installCatalogUri <uri>``` | **Facoltativa**: URI del manifesto del catalogo da usare per l'installazione. Se specificato, il gestore del canale tenterà di scaricare il manifesto del catalogo da questo URI prima di usare l'URI nel manifesto del canale di installazione. Questo parametro viene usato per supportare l'installazione offline, in cui verrà creata la cache di layout con il catalogo dei prodotti già scaricato. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| ```--productId <id>``` | ID del prodotto per l'istanza che verrà installata. È obbligatorio per il comando di installazione e viene ignorato per gli altri comandi se è specificata l'opzione --installPath. |
| ```--wait``` | **Facoltativa**: il processo attenderà fino al completamento dell'installazione prima di restituire un codice di uscita. Ciò è utile nell'automazione delle installazioni quando è necessario attendere il completamento dell'installazione per gestire il codice da essa restituito. |
| ```--locale <language-locale>``` | **Facoltativa**: modifica la lingua di visualizzazione dell'interfaccia utente per il programma di installazione. L'impostazione verrà resa persistente. Per altre informazioni, vedere la sezione [Elenco delle impostazioni locali delle lingue](#list-of-language-locales) in questa pagina.|

## <a name="list-of-workload-ids-and-component-ids"></a>Elenco di ID di carichi di lavoro e ID di componenti
Per un elenco degli ID di componenti e carichi di lavoro ordinati per prodotto Visual Studio, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Elenco delle impostazioni locali delle lingue
| **Impostazioni locali** | **Lingua** |
| ----------------------- | --------------- |  
| cs-CZ | Ceco |
| de-DE | Tedesco |
| it-IT | Inglese |
| es-ES | Spagnolo |
| cs-CZ | Ceco |
| fr-FR | Francese |
| it-IT | Italiano |
| ja-JP | Giapponese |
| ko-KR | Coreano |
| pl-PL | Polacco |
| pt-BR | Portoghese (Brasile) |
| ru-RU | Russo |
| tr-TR | Turco |
| zh-CN | Cinese semplificato |
| zh-TW | Cinese tradizionale |


## <a name="error-codes"></a>Codici di errore
A seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` verrà impostata su uno dei valori seguenti:
| **Valore** | **Risultato** |
| --------- | ---------- |
| 0 | L'operazione è riuscita |
| 3010 | L'operazione è riuscita, ma è necessario riavviare per poter usare l'installazione |
| Altro | Si è verificata una condizione di errore. Per altre informazioni, vedere i log |

Durante ogni operazione nella directory `%TEMP%` verranno generati diversi file di log che indicano lo stato di avanzamento dell'installazione. Ordinare la cartella per data e cercare i file che iniziano con `dd_bootstrapper`, `dd_client` e `dd_setup` per individuare quelli che si riferiscono rispettivamente al programma di bootstrap, all'app del programma di installazione e al motore di installazione. 

## <a name="see-also"></a>Vedere anche

 * [Installare Visual Studio](install-visual-studio.md)
 * [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Come segnalare un problema con Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

