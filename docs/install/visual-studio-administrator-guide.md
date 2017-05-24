---
title: Guida dell&quot;amministratore di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 05/06/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
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
ms.translationtype: Human Translation
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: c88a932beac964117ac2fd6ffe171bf4256ac706
ms.contentlocale: it-it
ms.lasthandoff: 05/08/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Guida dell'amministratore di Visual Studio 2017

Negli ambienti aziendali, gli amministratori di sistema distribuiscono solitamente le installazioni nei computer degli utenti finali da una condivisione di rete o tramite software di gestione dei sistemi. Il motore di installazione di Visual Studio è stato progettato per supportare la distribuzione aziendale, che consente agli amministratori di sistema di creare un percorso di installazione di rete, preconfigurare valori di installazione predefiniti, distribuire codici Product Key durante il processo di installazione e gestire aggiornamenti di prodotto in seguito a una distribuzione eseguita correttamente. Questa guida dell'amministratore fornisce indicazioni basate sullo scenario per la distribuzione aziendale in ambienti di rete comuni.

## <a name="steps-for-deploying-visual-studio-2017-in-an-enterprise-environment"></a>Procedura per la distribuzione di Visual Studio 2017 in un ambiente aziendale

È possibile distribuire Visual Studio 2017 in workstation client purché ogni computer di destinazione soddisfi i [requisiti di installazione minimi](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). I passaggi tipici per la distribuzione di Visual Studio sono i seguenti, sia che si usi software come System Center o un file batch:

1. [Creare una condivisione di rete contenente i file di prodotto di Visual Studio](create-a-network-installation-of-visual-studio.md) in un percorso di rete;

2. [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md) da installare;

3. [Creare un file di risposta](automated-installation-with-response-file.md) contenente le opzioni di installazione predefinite. In alternativa, [creare uno script di installazione](use-command-line-parameters-to-install-visual-studio.md) usando parametri della riga di comando per controllare l'installazione;

4. Facoltativamente, includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md), in modo che gli utenti non debbano attivare il software separatamente;

5. Aggiornare il layout di rete per [controllare il momento in cui gli aggiornamenti di prodotto vengono messi a disposizione degli utenti finali](controlling-updates-to-visual-studio-deployments.md);

6. Facoltativamente, impostare le chiavi del Registro di sistema per [controllare gli elementi memorizzati nella cache delle workstation client](set-defaults-for-enterprise-deployments.md);

7. Usare la tecnologia di distribuzione desiderata per eseguire lo script generato nei passaggi precedenti nelle workstation di sviluppo di destinazione;

8. [Aggiornare il percorso di rete con gli aggiornamenti più recenti](update-a-network-installation-of-visual-studio.md) di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

> [!IMPORTANT]
> Si noti che le installazioni eseguite da una condivisione di rete "ricordano" il percorso di origine da cui provengono. Ciò significa che per il ripristino di un computer client potrebbe essere necessario tornare alla condivisione di rete client da cui è stato installato in origine il client. Scegliere con attenzione il percorso di rete in modo che sia adeguato al periodo di tempo in cui si prevede di eseguire i client di Visual Studio 2017 nella propria organizzazione.

## <a name="tools"></a>Strumenti
Sono stati resi disponibili diversi strumenti che consentono di [rilevare e gestire le istanze installate di Visual Studio](tools-for-managing-visual-studio-instances.md) nei computer client.

> [!TIP]
> Oltre alla documentazione inclusa nella guida dell'amministratore, anche gli articoli del [blog di Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) costituiscono un'ottima fonte di informazioni sull'installazione di Visual Studio 2017.

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Installare Visual Studio in ambienti offline](install-visual-studio-in-offline-environment.md)
* [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Come segnalare un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

