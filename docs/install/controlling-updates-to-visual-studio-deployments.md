---
title: Controllare gli aggiornamenti delle distribuzioni di Visual Studio | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 7267b279a94094eb58fe51edd1ad36cd8967c711
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio

In molti casi, gli amministratori aziendali creano un layout e lo inseriscono in una condivisione file di rete per poter essere distribuito agli utenti finali.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Controllo della posizione in cui Visual Studio cerca gli aggiornamenti
Per impostazione predefinita, Visual Studio continua a cercare gli aggiornamenti online anche se l'installazione è stata distribuita da una condivisione di rete. Se è disponibile un aggiornamento, l'utente può installarlo. Eventuali contenuti aggiornati non disponibili nel layout offline sono scaricati dal Web.

Per controllare direttamente le posizioni in cui Visual Studio cerca gli aggiornamenti, è possibile modificare il percorso in cui avviene la ricerca. È inoltre possibile controllare la versione dell’aggiornamento degli utenti. A tale scopo, attenersi alla seguente procedura:

 1. Creare un layout offline:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Copiarlo nella condivisione file in cui si vuole inserirlo:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modificare il file response.json nel layout e cambiare il valore `channelUri` in modo che punti a una copia del file channelManifest.json controllato dall'amministratore.

  Assicurarsi di usare le barre rovesciate come carattere di escape nel valore, come illustrato nell’esempio seguente:

  ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
  ```

 Gli utenti finali possono ora eseguire l'installazione da questa condivisione per installare Visual Studio.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```

Quando un amministratore aziendale stabilisce che per gli utenti finali è il momento di eseguire l'aggiornamento a una versione più recente di Visual Studio, è possibile [aggiornare la posizione di layout](update-a-network-installation-of-visual-studio.md) in cui incorporare i file aggiornati, come segue.

 1. Utilizzare un comando simile a quello che segue:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 2. Verificare che il file response.json nel layout aggiornato contenga ancora le personalizzazioni, in particolare la modifica del valore channelUri, come segue:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 Le installazioni esistenti di Visual Studio da questo layout eseguono la ricerca degli aggiornamenti in `\\server\share\VS2017\ChannelManifest.json`. Se il file channelManifest.json è più recente rispetto a quello installato dall'utente, Visual Studio informerà l'utente che è disponibile un aggiornamento.

 Le nuove installazioni installano automaticamente la versione aggiornata di Visual Studio direttamente dal layout.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Controllo delle notifiche nell'IDE di Visual Studio
Come descritto in precedenza, Visual Studio controlla l'eventuale presenza di aggiornamenti nel percorso da cui è stato installato (ad esempio, la condivisione di rete o Internet). Se è disponibile un aggiornamento, Visual Studio ne informa l'utente con un flag di notifica nell'angolo superiore destro della finestra.

 ![Flag di notifica per gli aggiornamenti](media/notification-flag.png)

Se si preferisce non informare gli utenti della disponibilità di aggiornamenti, è possibile disabilitare le notifiche. Ad esempio, se si distribuiscono gli aggiornamenti attraverso un meccanismo di distribuzione centrale del software, è possibile voler disabilitare queste notifiche.

Poiché Visual Studio 2017 [archivia le voci del Registro di sistema in un registro privato](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), non è possibile modificare direttamente il Registro di sistema nel modo consueto. Visual Studio include, tuttavia, un’utility `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0 
```
Accertarsi di sostituire la directory in modo che coincida con l'istanza installata che si vuole modificare.

> [!TIP]
> Usare [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) per trovare un'istanza specifica di Visual Studio in una workstation client.

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)

