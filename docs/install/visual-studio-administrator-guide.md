---
title: Guida dell&quot;amministratore di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 69ac1327fa9233bf0ecc18be5e7d2f2a4f82b3b0
ms.lasthandoff: 03/07/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guida dell'amministratore di Visual Studio per Visual Studio 2017

È possibile distribuire Visual Studio in una rete purché ogni computer di destinazione soddisfi i [requisiti di installazione minimi](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). È possibile creare una condivisione di rete eseguendo il file di installazione con l'opzione --layout, come descritto nella pagina [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md), e quindi copiarla dal computer locale alla condivisione di rete.   

 Si noti che le installazioni eseguite da una condivisione di rete "ricordano" il percorso di origine da cui provengono. Ciò significa che per il ripristino di un computer client potrebbe essere necessario tornare alla condivisione di rete client da cui è stato installato in origine il client. Scegliere con attenzione il percorso di rete in modo che sia adeguato al periodo di tempo in cui si prevede di eseguire i client di Visual Studio 2017 nella propria organizzazione.

## <a name="tools"></a>Strumenti

 Sono disponibili vari strumenti per facilitare la gestione delle installazioni di Visual Studio:

* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): esempi di C# e C++ per consentire agli utenti di analizzare le istanze di Visual Studio nel proprio computer.
* [VSWhere](https://github.com/microsoft/vswhere): un eseguibile C++ utile per trovare gli strumenti principali di Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): potenti script di PowerShell per le attività di amministrazione comuni correlate all'installazione.


## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
* [Creare un'installazione offline di Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usare gli ID dei carichi di lavoro e dei componenti di Visual Studio per personalizzare l'installazione offline](workload-and-component-ids.md)
* [Come segnalare un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

