---
title: Strumenti per il rilevamento e la gestione di istanze di Visual Studio | Microsoft Docs
description: '{{PLACEHOLDER}}'
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
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
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
ms.openlocfilehash: a6c3aa65a2c0198c856f09f6f16f58bf16945d58
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Strumenti per il rilevamento e la gestione di istanze di Visual Studio

## <a name="detecting-existing-visual-studio-instances"></a>Rilevamento di istanze di Visual Studio esistenti
Sono stati resi disponibili diversi strumenti che consentono di rilevare e gestire le istanze installate di Visual Studio nei computer client:

* [VSWhere](https://github.com/microsoft/vswhere): un eseguibile C++ utile per individuare il percorso degli strumenti principali di Visual Studio da un'istanza installata del prodotto.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): script PowerShell che usano l'API di configurazione del programma di installazione per identificare le istanze installate di Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): esempi C# e C++ che illustrano come usare l'API di configurazione del programma di installazione per eseguire query su un'installazione esistente.

L'[API di configurazione del programma di installazione](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) include inoltre interfacce per gli sviluppatori che intendono creare utilità personalizzate per eseguire interrogazioni sulle istanze di Visual Studio.

>[!TIP]
>Per altre informazioni sull'installazione di Visual Studio 2017, vedere gli [articoli del blog di Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Modifica del Registro di sistema per un'istanza di Visual Studio
In Visual Studio 2017 le impostazioni del Registro di sistema vengono archiviate in un percorso privato, che consente la presenza nello stesso computer di più istanze side-by-side della stessa versione di Visual Studio.

Questi elementi non vengono archiviati nel Registro di sistema globale ed è quindi necessario seguire istruzioni speciali per usare l'editor del Registro di sistema per apportare modifiche alle impostazioni del registro:

1. Se si ha un'istanza aperta di Visual Studio 2017, chiuderla.
2. Avviare `regedit.exe`.
3. Selezionare il nodo `HKEY_LOCAL_MACHINE`.
4. Nel menu principale di Regedit selezionare **File -> Carica hive...**  e quindi selezionare il file di registro privato archiviato nella cartella **AppData\Local**. Ad esempio:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` corrisponde all'istanza di Visual Studio che si vuole trovare.

Verrà chiesto di fornire un nome di hive, che diventerà il nome dell'hive isolato. Al termine dell'operazione sarà possibile trovare il Registro di sistema nell'hive isolato appena creato.

> [!IMPORTANT]
> Prima di avviare nuovamente Visual Studio, è necessario scaricare l'hive isolato appena creato. A questo scopo, nel menu principale di Regedit selezionare File -> Scarica Hive. Se non si esegue questa operazione, il file rimarrà bloccato e non sarà possibile avviare Visual Studio.

