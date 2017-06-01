---
title: Aggiornare un&quot;installazione di rete di Visual Studio | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 05/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 1AF69C0E-0AC9-451B-845D-AE4EDBCEA65C
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
ms.openlocfilehash: 75c65d75ab751058ac435d62f253ead149ccfe42
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---
# <a name="update-a-network-based-installation-of-visual-studio"></a>Aggiornare un'installazione di rete di Visual Studio

È possibile aggiornare un layout di installazione di rete di Visual Studio con gli ultimi aggiornamenti di prodotto in modo che possa essere usato sia come punto di installazione per l'aggiornamento più recente di Visual Studio sia per gestire installazioni già distribuite in workstation client.

## <a name="how-to-update-a-network-layout"></a>Come aggiornare un layout di rete
Per aggiornare la condivisione di installazione di rete in modo che includa gli aggiornamenti più recenti, eseguire lo stesso comando `--layout` eseguito durante la creazione iniziale del layout per scaricare in modo incrementale i pacchetti aggiornati.

Se si è scelto di selezionare un layout parziale al momento della creazione del layout di rete, assicurarsi di usare gli stessi parametri della riga di comando usati durante la prima creazione del layout di installazione di rete (ad esempio, gli stessi carichi di lavoro e le stesse lingue). Se si scelgono opzioni diverse, il secondo comando `--layout` non aggiornerà i pacchetti che non sono stati specificati per la seconda volta.

Se si inserisce un layout in una condivisione file, si consiglia di aggiornare una copia privata del layout (ad esempio `c:\vs2017offline`) e, al termine del download del contenuto aggiornato, copiarlo nella condivisione file (ad esempio `\\server\products\VS2017`).  In caso contrario, se un utente esegue l'installazione durante l'aggiornamento del layout, è probabile che non sia in grado di ottenere tutto il contenuto del layout perché non è ancora stato interamente aggiornato.

## <a name="how-to-deploy-an-update-to-client-machines"></a>Come distribuire un aggiornamento in computer client
A seconda del tipo di configurazione dell'ambiente di rete, un aggiornamento può essere distribuito da un amministratore aziendale o avviato da un computer client. 

- Gli utenti possono aggiornare un'istanza di Visual Studio installata da una cartella di installazione offline:
  - Eseguire il programma di installazione di Visual Studio.
  - Fare clic su **Aggiorna**.

- Gli amministratori possono aggiornare distribuzioni client di Visual Studio senza alcuna interazione da parte dell'utente con due comandi separati:
  - Aggiornare prima il programma di installazione di Visual Studio: <br>```vs_enterprise.exe --quiet --update```
  - Aggiornare quindi l'applicazione Visual Studio: <br>```vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" --quiet --wait --norestart```

> [!NOTE]
> Usare il [comando vswhere.exe](tools-for-managing-visual-studio-instances.md) per identificare il percorso di installazione di un'istanza esistente di Visual Studio in un computer client.

> [!TIP]
> Per informazioni dettagliate su come controllare il momento in cui le notifiche di aggiornamento vengono visualizzate agli utenti, vedere [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).


## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)

