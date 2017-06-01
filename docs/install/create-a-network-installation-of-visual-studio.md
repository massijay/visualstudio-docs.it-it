---
title: Creare un&quot;installazione di rete di Visual Studio | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: timsneath
ms.author: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: c8c48a92ba4ba75e87d947364919688032842265
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---

# <a name="create-a-network-installation-of-visual-studio-2017"></a>Creare un'installazione di rete di Visual Studio 2017

Un amministratore aziendale crea solitamente un punto di installazione di rete per distribuire il software nelle workstation client. Visual Studio 2017 è stato progettato per consentire la memorizzazione dei file di installazione iniziale e di tutti gli aggiornamenti di prodotto in un'unica cartella (operazione talvolta denominata _creazione di un layout_), in modo che le workstation client possano usare lo stesso percorso di rete per gestire l'installazione anche se non hanno ancora eseguito l'aggiornamento di manutenzione più recente.

> [!NOTE]
> Se nell'azienda sono in uso più versioni di Visual Studio (ad esempio, Visual Studio Professional e Visual Studio Enterprise), è necessario creare una condivisione di installazione di rete separata per ogni edizione.

## <a name="download-the-visual-studio-bootstrapper"></a>Scaricare il programma di bootstrap di Visual Studio
**Scaricare** l'edizione di Visual Studio desiderata. Assicurarsi di fare clic su **Salva** e quindi su **Apri cartella**.

Il file eseguibile di installazione o, per essere più specifici, il file di un programma di bootstrap, sarà uno dei seguenti.

|Edizione | Download|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Community di Visual Studio | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

Altri programmi di bootstrap supportati includono [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) e [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Creare una cartella di installazione offline
Per creare un'installazione offline con tutte le lingue e tutte le funzionalità, usare uno dei comandi degli esempi seguenti.

(Assicurarsi di eseguire il comando dalla directory Download. In genere, il percorso di questa cartella è `C:\Users\<username>\Downloads` in un computer con Windows 10).

- Per Visual Studio Enterprise, eseguire:
  ```
  vs_enterprise.exe --layout c:\vs2017offline
  ```
- Per For Visual Studio Professional, eseguire:
  ```
  vs_professional.exe --layout c:\vs2017offline
  ```
- Per Visual Studio Community, eseguire:
  ```
  vs_community.exe --layout c:\vs2017offline
  ```

## <a name="modify-the-responsejson-file"></a>Modificare il file response.json
È possibile modificare il file response.json per impostare i valori predefiniti da usare quando viene eseguito il programma di installazione.  È possibile ,ad esempio, configurare il file `response.json` per selezionare un set specifico di carichi di lavoro selezionato in modo automatico.
Per informazioni dettagliate, vedere [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Copiare il layout in una condivisione di rete

Inserire il layout in una condivisione di rete affinché possa essere eseguito anche da altri computer.
* Esempio:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```
    
## <a name="customizing-the-network-layout"></a>Personalizzazione del layout di rete
Sono disponibili varie opzioni per personalizzare il layout di rete. È possibile, ad esempio, creare un layout parziale che contenga solo un set specifico di [impostazioni locali delle lingue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [carichi di lavoro, componenti e relative dipendenze consigliate o facoltative](workload-and-component-ids.md). Questa soluzione può essere utile se si prevede di distribuire nelle workstation client solo un subset di carichi di lavoro. I parametri della riga di comando più comuni per la personalizzazione del layout includono:

 - ```--add``` per specificare ID di [carico di lavoro o di componente](workload-and-component-ids.md).  Se si usa `--add`, verranno scaricati solo i carichi di lavoro e i componenti specificati con `--add`.  Se non si usa `--add`, verranno scaricati tutti i carichi di lavoro e i componenti.
 - ```--includeRecommended``` per includere tutti i componenti consigliati per gli ID di carico di lavoro specificati.
 - ```--includeOptional``` per includere tutti i componenti consigliati e facoltativi per gli ID di carico di lavoro specificati.
 - ```--lang``` per specificare le [impostazioni locali delle lingue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).
 
Gli esempi seguenti illustrano come creare un layout parziale personalizzato.

 - Per scaricare tutti i carichi di lavoro e tutti i componenti per una sola lingua, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Per scaricare tutti i carichi di lavoro e tutti i componenti per più lingue, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Per scaricare un solo carico di lavoro per tutte le lingue, eseguire: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
 - Per scaricare due carichi di lavoro e un solo componente facoltativo per tre lingue, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
 - Per scaricare due carichi di lavoro e tutti i relativi componenti consigliati, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
 - Per scaricare due carichi di lavoro e tutti i relativi componenti consigliati e facoltativi, eseguire: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```


## <a name="deploying-from-a-network-installation"></a>Distribuzione da un'installazione di rete
Gli amministratori possono distribuire Visual Studio nelle workstation client nell'ambito di uno script di installazione. In alternativa, gli utenti che hanno i diritti di amministratore possono installare Visual Studio nel proprio computer direttamente dalla condivisione.

- Gli utenti possono installare il programma eseguendo: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Gli amministratori possono installare il programma in modalità automatica eseguendo: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Se Visual Studio viene eseguito nell'ambito di un file batch, l'opzione `--wait` garantisce che il processo `vs_enterprise.exe` attenda il completamento dell'installazione prima di restituire un codice di uscita. Questa opzione è particolarmente utile se l'amministratore aziendale vuole eseguire altre azioni sull'installazione completa (ad esempio, [applicare un codice Product Key a un'installazione eseguita correttamente](automatically-apply-product-keys-when-deploying-visual-studio.md)) o se è necessario attendere il completamento dell'installazione per poter gestire il codice restituito.  Se non si usa l'opzione `--wait`, il processo vs_enterprise.exe verrà terminato prima del completamento dell'installazione e non verrà restituito un codice di uscita esatto che rappresenti lo stato dell'operazione di installazione.

### <a name="error-codes"></a>Codici di errore
Se è stato usato il parametro `--wait`, a seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` verrà impostata su uno dei valori seguenti:

  | **Valore** | **Risultato** |
  | --------- | ---------- |
  | 0 | L'operazione è riuscita |
  | 3010 | L'operazione è riuscita, ma è necessario riavviare per poter usare l'installazione |
  | Altro | Si è verificata una condizione di errore. Per altre informazioni, vedere i log |

## <a name="updating-a-network-install-layout"></a>Aggiornamento di un layout di installazione di rete
Man mano che diventano disponibili nuovi aggiornamenti di prodotto, è possibile scegliere di [aggiornare il layout di installazione di rete](update-a-network-installation-of-visual-studio.md) in modo da integrare i pacchetti aggiornati.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Come creare un layout per una versione precedente di Visual Studio 2017
**Nota**: i programmi di bootstrap di Visual Studio 2017 disponibili in http://www.visualstudio.com scaricano e installano la versione più recente di Visual Studio 2017 ogni volta che vengono eseguiti. Se si scarica un programma di bootstrap di Visual Studio oggi e lo si esegue tra sei mesi, verrà installata la versione di Visual Studio 2017 disponibile in quel momento. Se invece si crea un layout, l'installazione di Visual Studio dal layout installerà la versione specifica di Visual Studio presente nel layout, anche nel caso in cui sia disponibile online una versione più recente.

Se è necessario creare un layout per una versione precedente di Visual Studio 2017, è possibile accedere all'indirizzo https://my.visualstudio.com e scaricare le versioni "fixed" dei programmi di bootstrap di Visual Studio 2017 per le versioni supportate, che consentono di creare un layout di installazione di rete per una versione precedente. 

### <a name="how-to-get-support-for-your-offline-installer"></a>Come ottenere supporto per il programma di installazione offline
Se si verifica un problema con l'installazione offline, è importante segnalarlo a Microsoft. Il modo migliore per farlo è tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Con questo strumento è possibile inviare a Microsoft i dati di telemetria e i log necessari per diagnosticare e risolvere il problema.

Sono disponibili anche altre opzioni per il supporto. Per un elenco, vedere la pagina [Comunicazioni con Microsoft](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)

