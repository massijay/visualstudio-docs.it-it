---
title: Eseguire l&quot;installazione in ambienti di rete con larghezza di banda ridotta o non affidabili | Microsoft Docs
description: Descrive il funzionamento del programma di installazione di Visual Studio in condizioni di rete non affidabili e illustra come scaricare i file di installazione prima di iniziare la procedura di installazione.
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
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
ms.openlocfilehash: 9dbe70bce6c246416df64de304b06cd211320f2a
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Installare Visual Studio 2017 in ambienti di rete con larghezza di banda ridotta o non affidabili
Il nuovo programma di installazione di Visual Studio 2017 è stato progettato per funzionare correttamente in computer e reti in condizioni di qualsiasi tipo.

- I file necessari per installare Visual Studio vengono distribuiti in una rete di distribuzione globale e possono essere quindi recuperati da un server locale;
- Durante il processo di installazione, vengono provate tre diverse tecnologie di download (WebClient, BITS e WinInet) per ridurre al minimo le interferenze con software proxy e anti-virus;
- Il nuovo modello basato sul carico di lavoro consente di installare un minor numero di componenti rispetto alle precedenti versioni di Visual Studio.

È consigliabile quindi provare il nuovo programma di installazione Web, che assicura risultati molto soddisfacenti. Se, tuttavia, prima di iniziare il processo di installazione di Visual Studio si vuole avere la certezza che i file di installazione siano stati correttamente scaricati, è possibile soddisfare questa esigenza usando la riga di comando per creare una cache locale dei file necessari prima dell'inizio dell'installazione.

Ecco come fare.

## <a name="download-the-visual-studio-bootstrapper"></a>Scaricare il programma di bootstrap di Visual Studio
Iniziare scaricando il programma di bootstrap relativo all'edizione di Visual Studio selezionata.

Il file di installazione o, per essere più specifici, il file di un programma di bootstrap, corrisponderà o sarà simile a uno dei file seguenti.

| Edizione                    | File                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Community di Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>Creare una cache di installazione locale
Per creare un layout locale, aprire un prompt dei comandi e usare uno dei comandi presenti negli esempi seguenti. Negli esempi seguenti si presuppone che sia stato scaricato il bootstrapper della community di Visual Studio: modificare il comando per adattarlo all'edizione in uso.

- Per lo sviluppo per Web .NET e desktop .NET, eseguire:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
  ```
- Per lo sviluppo per desktop .NET e Office, eseguire:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
  ```
- Per lo sviluppo per desktop C++, eseguire:
  ```
  vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
  ```

- Per creare un layout locale completo con tutte le funzionalità (dato l'_elevato_ numero di funzionalità, questa operazione richiederà molto tempo), eseguire:
  ```
  vs_community.exe --layout c:\vs2017layout --lang en-US
  ```

Se si vuole installare una lingua diversa dall'inglese, nell'elenco in fondo alla pagina modificare `en-US` con impostazioni locali diverse. Usare l'[elenco di componenti e carichi di lavoro disponibili](workload-and-component-ids.md) per personalizzare ulteriormente la cache di installazione in base alle proprie esigenze.

## <a name="install-from-the-local-cache"></a>Eseguire l'installazione dalla cache locale
Quando si esegue l'installazione da una cache locale, si usano le versioni locali di ogni file. Se, tuttavia, durante l'installazione si selezionano componenti non contenuti nella cache, si tenterà di scaricarli da Internet.

Per assicurarsi che vengano installati solo i file scaricati, usare le stesse opzioni della riga di comando usate per creare la cache di layout. Ad esempio, se è stata creata una cache di layout con il comando seguente:

```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

Usare questo comando per eseguire l'installazione:

```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>Elenco delle impostazioni locali delle lingue
| **Impostazioni locali** | **Lingua** |
| ----------------------- | --------------- |  
| cs-CZ | Ceco |
| de-DE | Tedesco |
| it-IT | Inglese |
| es-ES | Spagnolo |
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

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

