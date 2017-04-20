---
title: Guida dell&quot;amministratore di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 04/03/2017
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
translationtype: Human Translation
ms.sourcegitcommit: af9699b63fdfb81a274affb78856817520c38b05
ms.openlocfilehash: fb7a87b720ad29252c602d9be5b958d8417ab93e
ms.lasthandoff: 04/03/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guida dell'amministratore di Visual Studio per Visual Studio 2017

 È possibile distribuire Visual Studio in una rete purché ogni computer di destinazione soddisfi i [requisiti di installazione minimi](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).

 I passaggi tipici per la distribuzione di Visual Studio sono i seguenti, sia che si usi software come System Center o un file batch:

1. [Creare la cache di layout del prodotto Visual Studio e memorizzarla](create-an-offline-installation-of-visual-studio.md) in un percorso di rete.

2. [Selezionare i carichi di lavoro e i componenti](workload-and-component-ids.md) da installare.

3. [Creare uno script di installazione](use-command-line-parameters-to-install-visual-studio.md) usando gli elementi selezionati e altri parametri della riga di comando per controllare l'installazione.

4. Facoltativamente, includere nello script di installazione le istruzioni per [applicare un codice Product Key per contratti multilicenza](automatically-apply-product-keys-when-deploying-visual-studio.md), in modo che gli utenti non debbano attivare il software separatamente.

5. Usare la tecnologia di distribuzione desiderata per eseguire lo script generato nei passaggi precedenti nelle workstation di sviluppo di destinazione.

6. Aggiornare il percorso di rete con gli aggiornamenti più recenti di Visual Studio eseguendo regolarmente il comando usato nel passaggio 1 in modo da aggiungere i componenti aggiornati.

> [!IMPORTANT]
>  Si noti che le installazioni eseguite da una condivisione di rete "ricordano" il percorso di origine da cui provengono. Ciò significa che per il ripristino di un computer client potrebbe essere necessario tornare alla condivisione di rete client da cui è stato installato in origine il client. Scegliere con attenzione il percorso di rete in modo che sia adeguato al periodo di tempo in cui si prevede di eseguire i client di Visual Studio 2017 nella propria organizzazione.

## <a name="tools"></a>Strumenti

 Sono stati resi disponibili diversi strumenti che consentono di rilevare e gestire le istanze installate di Visual Studio nei computer client:

* [VSWhere](https://github.com/microsoft/vswhere): un eseguibile C++ utile per individuare il percorso degli strumenti principali di Visual Studio da un'istanza installata del prodotto.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): script PowerShell che usano l'API di configurazione del programma di installazione per identificare le istanze installate di Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): esempi C# e C++ che illustrano come usare l'API di configurazione del programma di installazione per eseguire query su un'installazione esistente.

L'[API di configurazione del programma di installazione](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) include inoltre interfacce per gli sviluppatori che intendono creare utilità personalizzate per eseguire interrogazioni sulle istanze di Visual Studio.

>[!TIP]
>Per altre informazioni sull'installazione di Visual Studio 2017, vedere gli [articoli del blog di Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Creare un programma di installazione offline per Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Come segnalare un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

