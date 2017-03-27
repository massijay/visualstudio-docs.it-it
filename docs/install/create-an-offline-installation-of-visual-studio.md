---
title: Creare un programma di installazione offline per Visual Studio 2017 | Microsoft Docs
description: Informazioni su come creare un programma di installazione offline per Visual Studio.
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
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
ms.sourcegitcommit: 91fde66abf2f325ef0a6a0a2fd30e36981f44033
ms.openlocfilehash: acb47946c29d99cb53b34d67fe8a26f5611307f9
ms.lasthandoff: 03/08/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Creare un programma di installazione offline per Visual Studio 2017
Molti clienti hanno espresso l'esigenza di avere a disposizione un programma di installazione offline per [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067). Anche se Microsoft non offre un'immagine ISO, è facile creare una cartella utilizzabile per eseguire installazioni offline.

Ecco come fare.

## <a name="download-the-setup-file-you-want"></a>Scaricare il file del programma di installazione desiderato
**[Scaricare](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)** l'edizione di Visual Studio desiderata. Assicurarsi di fare clic su **Salva** e quindi su **Apri cartella**.

Il file di installazione o, per essere più specifici, il file di un programma di avvio automatico, sarà uno dei seguenti.

|Edizione | File|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Community di Visual Studio |**vs_community.exe**|

## <a name="create-an-offline-installation-folder"></a>Creare una cartella di installazione offline
Per creare un'installazione offline con tutte le lingue e tutte le funzionalità, usare uno dei comandi degli esempi seguenti.

(Assicurarsi di eseguire il comando dalla directory Download. In genere, il percorso di questa cartella è `C:\Users\<username>\Downloads` in un computer con Windows 10).

- Per Visual Studio Enterprise, eseguire: <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Per For Visual Studio Professional, eseguire: <br> ```vs_professional.exe --layout c:\vs2017offline```
- Per Visual Studio Community, eseguire: <br> ```vs_community.exe --layout c:\vs2017offline```

Per altri esempi, vedere la sezione [Come personalizzare il programma di installazione offline](#how-to-customize-your-offline- installer) in questa pagina.

## <a name="install-from-the-offline-installation-folder"></a>Eseguire l'installazione dalla cartella di installazione offline
È possibile scegliere di eseguire l'installazione in qualsiasi momento, ma quando si decide di procedere, seguire questa procedura.

  1. Installare i certificati disponibili nella cartella Certificati all'interno della cartella Layout. È sufficiente fare clic con il pulsante destro del mouse su ogni certificato per installarlo.

  2. Eseguire il file di installazione. Ad esempio, eseguire: <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>Altri suggerimenti per i programmi di installazione offline
È facile personalizzare o aggiornare il programma di installazione offline. Di seguito viene illustrato come. Nel caso si verifichino problemi con il programma di installazione offline, sono disponibili anche informazioni per la risoluzione dei problemi e di supporto.

### <a name="how-to-customize-your-offline-installer"></a>Come personalizzare il programma di installazione offline
Sono disponibili molte opzioni per personalizzare il programma di installazione offline. Ecco alcuni esempi di come personalizzarlo in base alle [impostazioni locali di lingua](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

 - Per scaricare tutti i carichi di lavoro e tutti i componenti per una sola lingua, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Per scaricare tutti i carichi di lavoro e tutti i componenti per più lingue, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Per scaricare un solo carico di lavoro per tutte le lingue, eseguire: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - Per scaricare due carichi di lavoro e un solo componente facoltativo per tre lingue, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ``` Per altre informazioni sulle opzioni disponibili per personalizzare l'installazione, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).


### <a name="how-to-update-an-offline-installer"></a>Come aggiornare un programma di installazione offline
Può diventare necessario aggiornare il programma di installazione offline in un secondo momento. Ecco come fare.
* Per aggiornare un'istanza di Visual Studio installata da una cartella di installazione offline, eseguire il programma di installazione di Visual Studio e quindi fare clic su **Aggiorna**.
* Per aggiornare la cartella di installazione offline in modo che includa gli aggiornamenti più recenti, eseguire di nuovo il comando ```--layout```. Assicurarsi di scegliere la stessa cartella usata in precedenza. In questo modo, verranno scaricati solo i componenti aggiornati dopo l'ultima esecuzione di ```--layout```.


Per aggiornare l'installazione offline, eseguire di nuovo il comando `--layout`. Assicurarsi di scegliere la stessa cartella usata in precedenza. In questo modo, verranno scaricati solo i componenti aggiornati dopo l'ultima esecuzione di `--layout`.

### <a name="how-to-troubleshoot-an-offline-installer"></a>Come risolvere i problemi di un programma di installazione offline
Non sempre tutto funziona correttamente. Ecco una tabella dei problemi noti e di alcune soluzioni che potrebbero essere utili.

| Problema       | Elemento                   | Soluzione |
| ----------- | ---------------------- | -------- |
| Viene visualizzato un messaggio di avviso che segnala che non è possibile installare alcuni componenti e pacchetti.  | Installazione di Android SDK (livello API) | Per includere pacchetti Android SDK (livello API), è necessario avere una connessione Internet a disposizione quando si crea il programma di installazione offline. Se si usa una rete con restrizioni, è necessario consentire l'accesso agli URL seguenti: <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Per ulteriori informazioni su come risolvere possibili problemi relativi alle impostazioni proxy, vedere il post di blog [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errori di installazione di Visual Studio (Android SDK) dietro un proxy).  |  
| Gli utenti non anno accesso ai file. | Autorizzazioni (ACL) | Assicurarsi di modificare le autorizzazioni (ACL) in modo da consentire l'accesso in lettura ad altri utenti *prima* di condividere l'installazione offline. |
| Non è possibile installare nuovi carichi di lavoro, componenti o lingue.  | `--layout`  | Assicurarsi di avere accesso a Internet se si esegue l'installazione da un layout parziale e si selezionano carichi di lavoro, componenti o lingue non disponibili nel layout precedente. |

### <a name="how-to-get-support-for-your-offline-installer"></a>Come ottenere supporto per il programma di installazione offline
Se si verifica un problema con l'installazione offline, è importante segnalarlo a Microsoft. Il modo migliore per farlo è tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Con questo strumento è possibile inviare a Microsoft i dati di telemetria e i log necessari per diagnosticare e risolvere il problema.

Sono disponibili anche altre opzioni per il supporto. Per un elenco, vedere la pagina [Comunicazioni con Microsoft](../ide/how-to-report-a-problem-with-visual-studio-2017.md).


## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)

