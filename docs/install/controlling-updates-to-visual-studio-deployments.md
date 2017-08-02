---
title: Controllare gli aggiornamenti delle distribuzioni di Visual Studio | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 05/06/2017
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
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio

In molti casi, gli amministratori aziendali creano un layout e lo inseriscono in una condivisione file di rete per poter essere distribuito agli utenti finali.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Controllo della posizione in cui Visual Studio cerca gli aggiornamenti
Per impostazione predefinita, Visual Studio continua a cercare gli aggiornamenti online anche se l'installazione è stata distribuita da una condivisione di rete. Se è disponibile un aggiornamento, l'utente potrà installarlo; eventuali contenuti aggiornati non disponibili nel layout offline verranno scaricati dal Web.

Se si vuole controllare direttamente la posizione in cui Visual Studio cerca gli aggiornamenti, nonché la versione a cui gli utenti vengono aggiornati, è possibile modificare il percorso in cui Visual Studio cerca gli aggiornamenti seguendo questa procedura:

 1. Creare un layout offline:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Copiarlo nella condivisione file in cui si vuole inserirlo:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Modificare il file response.json nel layout e cambiare il valore `channelUri` in modo che punti a una copia del file channelManifest.json controllato dall'amministratore. <b>Nota:</b> assicurarsi di usare le barre rovesciate come carattere di escape nel valore, come illustrato di seguito.
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. Gli utenti finali possono ora eseguire l'installazione da questa condivisione per installare Visual Studio.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. Quando un amministratore aziendale stabilisce che per gli utenti finali è il momento di eseguire l'aggiornamento a una versione più recente di Visual Studio, è possibile [aggiornare la posizione di layout](update-a-network-installation-of-visual-studio.md) in cui incorporare i file aggiornati con un comando simile al seguente:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. Verificare che il file response.json nel layout aggiornato contenga ancora le personalizzazioni, in particolare la modifica del valore channelUri:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. Le installazioni esistenti di Visual Studio da questo layout eseguiranno la ricerca degli aggiornamenti in `\\server\share\VS2017\ChannelManifest.json`. Se questo file channelManifest.json è più nuovo rispetto a quello installato dall'utente, Visual Studio informerà l'utente che è disponibile un aggiornamento.
 8. Le nuove installazioni installeranno automaticamente la versione aggiornata di Visual Studio direttamente dal layout.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Controllo delle notifiche nell'IDE di Visual Studio
Come descritto in precedenza, Visual Studio controlla l'eventuale presenza di aggiornamenti nel percorso da cui è stato installato (ad esempio, la condivisione di rete o Internet). Se è disponibile un aggiornamento, per impostazione predefinita Visual Studio ne informa l'utente con un flag di notifica nell'angolo superiore destro della finestra: ![flag di notifica per gli aggiornamenti](~/install/media/notification-flag.png)

Se si preferisce non informare gli utenti della disponibilità di aggiornamenti (ad esempio, se si distribuiscono gli aggiornamenti attraverso un meccanismo di distribuzione centrale del software), è possibile disabilitare queste notifiche.

Dal momento in cui Visual Studio 2017 [archivia le voci del Registro di sistema in un registro privato](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), non è possibile modificare direttamente il Registro di sistema nel modo consueto. Visual Studio include tuttavia un comando `vsregedit.exe` che consente di modificare le impostazioni di Visual Studio. È possibile disattivare le notifiche con il comando seguente:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

Sostituire la directory nel comando precedente in modo che coincida con l'istanza installata che si vuole modificare. 

> [!TIP]
> Usare [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) per trovare un'istanza specifica di Visual Studio in una workstation client. 

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)

