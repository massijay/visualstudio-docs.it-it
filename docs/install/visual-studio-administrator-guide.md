---
title: Guida dell'amministratore di Visual Studio | Microsoft Docs
description: Altre informazioni su come distribuire Visual Studio in un ambiente aziendale.
ms.custom: 
ms.date: 05/15/2017
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
ms.sourcegitcommit: d9de84bed187c62962a76424aabdc5f355dff4dc
ms.openlocfilehash: 220b41f44cdc91ea84bf08b8eec8181dc01c25c7
ms.contentlocale: it-it
ms.lasthandoff: 05/15/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Guida dell'amministratore di Visual Studio 2017

Negli ambienti aziendali, gli amministratori di sistema distribuiscono solitamente le installazioni nei computer degli utenti finali da una condivisione di rete o tramite software di gestione dei sistemi. Il motore di installazione di Visual Studio è stato progettato per supportare la distribuzione aziendale, che consente agli amministratori di sistema di creare un percorso di installazione di rete, preconfigurare valori di installazione predefiniti, distribuire codici Product Key durante il processo di installazione e gestire aggiornamenti di prodotto in seguito a una distribuzione eseguita correttamente. Questa guida dell'amministratore offre indicazioni basate sullo scenario per la distribuzione aziendale in ambienti di rete.

## <a name="deploying-visual-studio-2017-in-an-enterprise-environment"></a>Distribuzione di Visual Studio 2017 in un ambiente aziendale

È possibile distribuire Visual Studio 2017 in workstation client purché ogni computer di destinazione soddisfi i [requisiti di installazione minimi](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). I passaggi tipici per la distribuzione di Visual Studio sono i seguenti, sia che si usi software come System Center o un file batch:

1. [Creare una condivisione di rete contenente i file di prodotto di Visual Studio](create-a-network-installation-of-visual-studio.md) in un percorso di rete.

2. [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md) da installare.

3. [Creare un file di risposta](automated-installation-with-response-file.md) contenente le opzioni di installazione predefinite. In alternativa, [creare uno script di installazione](use-command-line-parameters-to-install-visual-studio.md) che usa parametri della riga di comando per controllare l'installazione.

4. Facoltativamente, includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md), in modo che gli utenti non debbano attivare il software separatamente.

5. Aggiornare il layout di rete per [controllare il momento in cui gli aggiornamenti di prodotto vengono messi a disposizione degli utenti finali](controlling-updates-to-visual-studio-deployments.md).

6. Facoltativamente, impostare le chiavi del Registro di sistema per [controllare gli elementi memorizzati nella cache delle workstation client](set-defaults-for-enterprise-deployments.md).

7. Usare la tecnologia di distribuzione desiderata per eseguire lo script generato nei passaggi precedenti nelle workstation di sviluppo di destinazione.

8. [Aggiornare il percorso di rete con gli aggiornamenti più recenti](update-a-network-installation-of-visual-studio.md) di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

> [!IMPORTANT]
> Si noti che le installazioni eseguite da una condivisione di rete "ricordano" il percorso di origine da cui provengono. Ciò significa che per il ripristino di un computer client potrebbe essere necessario tornare alla condivisione di rete client da cui è stato installato in origine il client. Scegliere con attenzione il percorso di rete in modo che sia adeguato al periodo di tempo in cui si prevede di eseguire i client di Visual Studio 2017 nella propria organizzazione.

## <a name="visual-studio-tools"></a>Strumenti di Visual Studio
Sono stati resi disponibili diversi strumenti che consentono di [rilevare e gestire le istanze installate di Visual Studio](tools-for-managing-visual-studio-instances.md) nei computer client.

> [!TIP]
> Oltre alla documentazione inclusa nella guida dell'amministratore, anche gli articoli del [blog di Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) costituiscono un'ottima fonte di informazioni sull'installazione di Visual Studio 2017.

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
  * [Informazioni di riferimento sugli ID dei carichi di lavoro e dei componenti](workload-and-component-ids.md)
* [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Considerazioni speciali per l'installazione di Visual Studio in un ambiente offline](install-visual-studio-in-offline-environment.md)
* [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md)
* [Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Impostare i valori predefiniti per le distribuzioni aziendali di Visual Studio](set-defaults-for-enterprise-deployments.md)
* [Disabilitare o spostare la cache dei pacchetti](disable-or-move-the-package-cache.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Controllare gli aggiornamenti delle distribuzioni di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Strumenti per il rilevamento e la gestione di istanze di Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Come segnalare un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

