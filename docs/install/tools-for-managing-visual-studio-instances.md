---
title: Strumenti per il rilevamento e la gestione di istanze di Visual Studio | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 08/14/2017
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
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 1e81071d8a67fd5b8c38bcf87629604efe6fa4a5
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---

# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Strumenti per il rilevamento e la gestione di istanze di Visual Studio

## <a name="detecting-existing-visual-studio-instances"></a>Rilevamento di istanze di Visual Studio esistenti
Sono stati resi disponibili diversi strumenti che consentono di rilevare e gestire le istanze installate di Visual Studio nei computer client:

* [VSWhere](https://github.com/microsoft/vswhere): un file eseguibile incorporato in Visual Studio o disponibile per una distribuzione separata che consente di trovare il percorso di tutte le istanze di Visual Studio in un computer specifico.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): script PowerShell che usano l'API di configurazione del programma di installazione per identificare le istanze installate di Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): esempi C# e C++ che illustrano come usare l'API di configurazione del programma di installazione per eseguire query su un'installazione esistente.

L'[API di configurazione del programma di installazione](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) include inoltre interfacce per gli sviluppatori che intendono creare utilità personalizzate per eseguire interrogazioni sulle istanze di Visual Studio.

## <a name="using-vswhereexe"></a>Uso di vswhere.exe
`vswhere.exe` è automaticamente incluso in Visual Studio 2017 versione 15.2 o versione successiva oppure è possibile scaricarlo dalla [pagina dei rilasci](https://github.com/Microsoft/vswhere/releases). Usare `vswhere -?` per ottenere informazioni sullo strumento. Ad esempio, questo comando mostra tutti i rilasci di Visual Studio, incluse le versioni precedenti del prodotto e le versioni non definitive e restituisce i risultati in formato JSON:

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

>[!TIP]
>Per altre informazioni sull'installazione di Visual Studio 2017, vedere gli [articoli del blog di Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Modifica del Registro di sistema per un'istanza di Visual Studio
In Visual Studio 2017 le impostazioni del Registro di sistema vengono archiviate in un percorso privato, che consente la presenza nello stesso computer di più istanze side-by-side della stessa versione di Visual Studio.

Questi elementi non vengono archiviati nel Registro di sistema globale ed è quindi necessario seguire istruzioni speciali per usare l'editor del Registro di sistema per apportare modifiche alle impostazioni del registro:

1. Se si ha un'istanza aperta di Visual Studio 2017, chiuderla.
2. Avviare `regedit.exe`.
3. Selezionare il nodo `HKEY_LOCAL_MACHINE`.
4. Nel menu principale di Regedit selezionare **File -> Carica hive... ** e quindi selezionare il file di registro privato archiviato nella cartella **AppData\Local**. Ad esempio:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` corrisponde all'istanza di Visual Studio che si vuole trovare.

Verrà chiesto di fornire un nome di hive, che diventerà il nome dell'hive isolato. Al termine dell'operazione sarà possibile trovare il Registro di sistema nell'hive isolato appena creato.

> [!IMPORTANT]
> Prima di avviare nuovamente Visual Studio, è necessario scaricare l'hive isolato appena creato. A questo scopo, nel menu principale di Regedit selezionare File -> Scarica Hive. (Se non si esegue questa operazione, il file rimarrà bloccato e non sarà possibile avviare Visual Studio).

