---
title: Creare un&quot;installazione offline di Visual Studio 2017 RC | Microsoft Docs
description: Informazioni su come creare un&quot;installazione offline di Visual Studio.
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
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
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>Creare un'installazione offline di Visual Studio 2017 RC

## <a name="create-a-layout"></a>Creare un layout
Se si vuole installare [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) in un altro computer che non ha accesso a Internet, è possibile farlo creando prima di tutto un layout di installazione offline che contenga tutti i file e i componenti di Visual Studio necessari.

È quindi possibile installare Visual Studio nel computer di destinazione tramite il layout di installazione offline creato.     

> [!WARNING]
> Al momento, Android SDK non supporta un'esperienza di installazione offline. Se si installano gli elementi del programma di installazione di Android SDK in un computer non connesso a internet, l'installazione potrebbe non riuscire. Per altre informazioni, vedere la sezione [Risolvere i problemi di un'installazione offline](#tshootofflineinstall) in questo argomento.


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>Per creare un layout di installazione offline di Visual Studio
1. Scaricare il file eseguibile di installazione di Visual Studio in un'unità del computer locale.
  Ad esempio, [scaricare il file vs_enterprise.exe](https://www.visualstudio.com/vs/visual-studio-2017-rc/).
2. Dal prompt dei comandi eseguire `vs_enterprise.exe` con gli argomenti (opzioni) seguenti:

   a. Aggiungere `--layout <path>`, dove `<path>` è il percorso in cui si vuole scaricare il layout. Si noti che i percorsi relativi (ad esempio `..\vs2017`) non sono attualmente supportati. Per impostazione predefinita, vengono scaricate tutte le lingue. Vedere l'esempio A.

   b. Limitare il download a un subset delle lingue disponibili specificando l'argomento `--lang <language>`, dove `<language>` corrisponde a una o più impostazioni locali e lingue.  Vedere gli esempi B e C.

   c. Limitare il download a un subset di componenti e carichi di lavoro specificando l'argomento `--add <package ID>`. In questo modo verranno scaricati solo i carichi di lavoro e i componenti (con le relative dipendenze) specificati. Vedere gli esempi D ed E.

   Per un elenco completo di ID di componenti e carichi di lavoro ordinati per prodotto Visual Studio, vedere la pagina [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids) (ID di carichi di lavoro e componenti di Visual Studio 2017).

### <a name="examples"></a>Esempi
**Esempio A**: download di tutti i carichi di lavoro e di tutti i componenti per tutte le lingue
  > ```vs_enterprise.exe --layout C:\vs2017```

**Esempio B**: download di tutti i carichi di lavoro e di tutti i componenti per una sola lingua  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**Esempio C**: download di tutti i carichi di lavoro e di tutti i componenti per più lingue
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**Esempio D**: download di un solo carico di lavoro per tutte le lingue
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**Esempio E**: download di due carichi di lavoro e di un solo componente facoltativo per tre lingue
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > Il parametro --layout ha esito negativo se il nome file di installazione con estensione exe include caratteri numerici. Per risolvere questo problema rimuovere i numeri dal nome file&mdash;ad esempio, rinominare *vs_community__198521760.1486960229.exe* come ***vs_community.exe***.

### <a name="language-locales"></a>Impostazioni locali delle lingue

| Impostazioni locali | Linguaggio |
| -----   | ----- |
| cs-CZ    | Ceco |
| de-DE    | Tedesco |
| it-IT    | Inglese |
| es-ES    | Spagnolo |
| fr-FR    | Francese |
| it-IT    | Italiano |
| ja-JP    | Giapponese |
| ko-KR    | Coreano |
| pl-PL    | Polacco |
| pt-BR    | Portoghese (Brasile) |
| ru-RU    | Russo |
| tr-TR    | Turco |
| zh-CN    | Cinese semplificato |
| zh-TW    | Cinese tradizionale |


## <a name="install-from-a-layout"></a>Installare da un layout
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>Per installare Visual Studio da un layout di installazione offline
1. Nel computer di destinazione passare alla cartella **Certificati** nella cartella Layout.
2. **Certificati** facendo clic con il pulsante destro del mouse su ognuno.

  Se dopo l'installazione di un certificato viene richiesta una password, fare clic su **Continua**.  
3. Eseguire `vs_enterprise.exe` dalla cartella **Layout**.

Nota: se si esegue l'installazione da un layout parziale e si selezionano carichi di lavoro, componenti o lingue non disponibili nel layout, il programma di installazione tenterà di scaricarli.  Se non è disponibile l'accesso a Internet, non sarà possibile installare questi elementi.

> [!CAUTION]
> Il layout di installazione offline attualmente crea alcuni file con autorizzazioni limitate (ACL) che evitano l'accesso da parte di tutti gli utenti.  Assicurarsi di modificare le autorizzazioni (ACL) in modo da consentire l'accesso in lettura ad altri utenti *prima* di condividere l'installazione offline.

## <a name="update-an-installation-layout"></a>Aggiornare un layout di installazione
Quando sono disponibili aggiornamenti di Visual Studio 2017 RC, è possibile eseguire di nuovo il comando `--layout`, facendo riferimento alla stessa cartella del layout, per assicurarsi che questa contenga i componenti più recenti. Verranno scaricati solo i componenti aggiornati dopo l'ultima esecuzione di `--layout`.

## <a id="tshootofflineinstall"> </a>Risolvere i problemi di un layout di installazione
Durante l'installazione offline dalla cache di installazione offline potrebbero essere visualizzati messaggi di avviso relativi all'impossibilità di installare alcuni componenti e pacchetti. La tabella seguente include soluzioni possibili per questi scenari.

| Componente o pacchetto | Soluzione |
| -------------------- | -------- |
|Installazione di Android SDK (livello API)| Per installare pacchetti Android SDK (livello API) è necessaria una connessione Internet. Se si usa una rete con restrizioni, per installare Visual Studio è necessario consentire l'accesso agli URL seguenti: <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Per ulteriori informazioni su come risolvere possibili problemi relativi alle impostazioni proxy, vedere il post di blog [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errori di installazione di Visual Studio (Android SDK) dietro un proxy).  |  

 > [!IMPORTANT]
 > Mentre Visual Studio 2017 RC in generale è supportato per l'uso in un ambiente di produzione, i carichi di lavoro e i componenti contrassegnati come "Anteprima" o "Preview" nell'interfaccia utente di installazione non sono supportati per l'uso in un ambiente di produzione.

 ## <a name="see-also"></a>Vedere anche
 * [Install Visual Studio](install-visual-studio.md) (Installare Visual Studio)
 * [Use command-line parameters to install Visual Studio](use-command-line-parameters-to-install-visual-studio.md) (Usare i parametri della riga di comando per installare Visual Studio)
 * [Report a problem with Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md) (Segnalare un problema di Visual Studio)

