---
title: Usare i parametri della riga di comando per installare Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/14/2017
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
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 18a3d03663ac96e0751d4a420244b835be7146bf
ms.lasthandoff: 02/22/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017-rc"></a>Usare i parametri della riga di comando per installare Visual Studio 2017 RC
Quando si installa Visual Studio 2017 RC da un prompt dei comandi è possibile usare i seguenti parametri (detti anche opzioni) della riga di comando.  

## <a name="list-of-command-line-parameters"></a>Elenco dei parametri della riga di comando  
 Per i parametri della riga di comando di Visual Studio non si fa distinzione tra maiuscole e minuscole.  

| **Comando della riga di comando** | **Descrizione** |
| ----------------------- | --------------- |  
| ```modify``` | Modifica un prodotto installato. |
| ```update``` | Aggiorna un prodotto installato. |
| ```repair``` | Ripristina un prodotto installato. |
| ```uninstall``` | Disinstalla un prodotto installato. |

Se non viene specificato alcun comando, installa il prodotto.

| **Opzione della riga di comando** | **Descrizione** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | La directory di installazione per l'istanza su cui intervenire. Per il comando di installazione, si tratta della posizione in cui verrà installata l'istanza. Per gli altri comandi, si tratta della posizione in cui era installata l'istanza installata in precedenza. |
| ```--productId <id>``` | ID del prodotto per l'istanza che verrà installata. È obbligatorio per il comando di installazione e viene ignorato per gli altri comandi se è specificata l'opzione --installPath. |
| ```--layout <dir>``` | Facoltativa: specifica una directory per creare una cache di installazione offline. Selezionando questa opzione verrà aggiunta in modo implicito anche l'opzione '--wait'. |
| ```--lang <language-locale>``` *[&#60;language-locale&#62; ...]* | Facoltativa: installare o disinstallare pacchetti di risorse con le lingue specificate. |
| ```--add <workload or component ID>``` *[&#60;workload or component ID&#62; ...]* | Facoltativa: uno o più ID di carico di lavoro o componente da aggiungere. Vengono installati i componenti necessari dell'elemento, ma non i componenti consigliati o facoltativi. È possibile controllare i componenti aggiuntivi a livello globale tramite '--includeRecommended' e/o '--includeOptional'. Per un controllo più capillare, è possibile aggiungere ';includeRecommended' e/o ';includeOptional' all'ID artefatto (ad esempio, '--add Workload1;includeRecommended' o '--add Workload2;includeOptional;includeRecommended'). |
| ```--remove <workload or component ID>``` *[&#60;workload or component ID&#62; ...]* | Facoltativa: uno o più ID di carico di lavoro o componente da rimuovere. |
| ```--all``` | Facoltativa: se devono essere installati tutti i carichi di lavoro e i componenti per un prodotto. |
| ```--allWorkloads``` | Facoltativa: installa tutti i carichi di lavoro e i componenti necessari, nessun componente consigliato o facoltativo. |
| ```--includeRecommended``` | Facoltativa: include i componenti consigliati per tutti i carichi di lavoro installati, ma non i componenti facoltativi. I carichi di lavoro sono specificati con --allWorkloads o --add. |
| ```--includeOptional``` | Facoltativa: include i componenti facoltativi per tutti i carichi di lavoro installati, ma non i componenti consigliati. I carichi di lavoro sono specificati con --allWorkloads o --add.  |
| ```--quiet, -q``` | Facoltativa: non visualizzare alcuna interfaccia utente durante l'installazione. |
| ```--passive, -p``` | Facoltativa: visualizzare l'interfaccia utente, ma non richiedere alcuna interazione da parte dell'utente. |
| ```--norestart``` | Facoltativa: se presente, i comandi con --passive o --quiet non riavviano automaticamente il computer (se richiesto). Viene ignorata se non vengono specificate né --passive né --quiet.  |
| ```--locale <language-locale>``` | Facoltativa: modificare la lingua di visualizzazione dell'interfaccia utente per il programma di installazione. L'impostazione verrà resa persistente. |
| ```--nickname <name>``` | Facoltativa: definisce il nome alternativo da assegnare a un prodotto installato. La lunghezza del nome alternativo non può superare i 10 caratteri.  |
| ```--help, --?, -h, -?``` | Visualizza informazioni sull'uso del parametro. |

>Nota: quando si specificano più carichi di lavoro e componenti, è necessario ripetere l'opzione della riga di comando `--add` o `--remove` per ogni elemento.

| **Opzione avanzata della riga di comando** | **Descrizione** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | Facoltativa: ID del canale per l'istanza che verrà installata. È obbligatorio per il comando di installazione e viene ignorato per gli altri comandi se è specificata l'opzione --installPath. |
| ```--channelUri <uri>``` | Facoltativa: URI del manifesto del canale. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| ```--installChannelUri <uri>``` | Facoltativa: URI del manifesto del canale da usare per l'installazione. L'URI specificato da --channelUri (che deve essere specificata quando si specifica --installChannelUri) verrà usato per rilevare gli aggiornamenti. Se non si vuole ricevere gli aggiornamenti, è necessario specificare --channelUri senza un argomento. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| ```--installCatalogUri <uri>``` | Facoltativa: URI del manifesto del catalogo da usare per l'installazione. Se specificato, il gestore del canale tenterà di scaricare il manifesto del catalogo da questo URI prima di usare l'URI nel manifesto del canale di installazione. Questo parametro viene usato per supportare l'installazione offline, in cui verrà creata la cache di layout con il catalogo dei prodotti già scaricato. Può essere usato per il comando di installazione e viene ignorato per gli altri comandi. |
| ```--in <path>``` | Facoltativa: URI o percorso di un file di risposta.  |
| ```--addProductLang <language-locale>``` | Facoltativa: definisce la lingua di un elemento (gruppo, carico di lavoro o componente) da installare. Può apparire più volte nella riga di comando. L'opzione è facoltativa per i comandi di installazione e modifica e viene ignorata per i comandi di aggiornamento, ripristino e disinstallazione. Se non è presente, l'installazione userà le impostazioni locali del computer. |
| ```--removeProductLang <language-locale>``` | Facoltativa: definisce la lingua di un elemento (gruppo, carico di lavoro o componente) da rimuovere. Può apparire più volte nella riga di comando. L'opzione è facoltativa per i comandi di installazione e modifica e viene ignorata per i comandi di aggiornamento, ripristino e disinstallazione. |
| ```--wait``` | Facoltativa: il processo attenderà fino al completamento dell'installazione prima di restituire un codice di uscita. Ciò è utile nell'automazione delle installazioni quando è necessario attendere il completamento dell'installazione per gestire il codice da essa restituito. |
| ```--productKey``` | Facoltativa: definisce il codice Product Key da usare per un prodotto installato. È composto da 25 caratteri alfanumerici in formato 'xxxxx-xxxxx-xxxxx-xxxxx-xxxxx' o 'xxxxxxxxxxxxxxxxxxxxxxxxx'. |
## <a name="list-of-workload-ids-and-component-ids"></a>Elenco di ID di carichi di lavoro e ID di componenti
Per un elenco di ID di componenti e carichi di lavoro ordinati per prodotto Visual Studio, vedere la pagina [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids) (ID di carichi di lavoro e componenti di Visual Studio 2017).

> [!WARNING]
> Il parametro --layout ha esito negativo se il nome file di installazione con estensione exe include caratteri numerici. Per risolvere questo problema rimuovere i numeri dal nome file, ad esempio rinominare *vs_community__198521760.1486960229.exe* in ***vs_community.exe***.

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



> [!IMPORTANT]
> Sebbene Visual Studio 2017 RC in generale sia supportato per l'uso in un ambiente di produzione, i carichi di lavoro e i componenti contrassegnati come "Anteprima" o "Preview" nell'interfaccia utente di installazione non sono supportati per l'uso in un ambiente di produzione.

## <a name="see-also"></a>Vedere anche

 * [Installare Visual Studio](install-visual-studio.md)
 * [Create an offline installation of Visual Studio 2017](create-an-offline-installation-of-visual-studio.md) (Creare un'installazione offline di Visual Studio 2017)
 * [Come segnalare un problema con Visual Studio&2017; RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

