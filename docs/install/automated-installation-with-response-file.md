---
title: Automatizzare l&quot;installazione di Visual Studio con un file di risposta | Microsoft Docs
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
ms.assetid: 448C738E-121F-4B64-8CA8-3BC997817A14
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
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: c77f0321e50a27635e083d656cf6ba8011a4ef4d
ms.contentlocale: it-it
ms.lasthandoff: 05/11/2017

---
# <a name="how-to-define-settings-in-a-response-file"></a>Come definire impostazioni in un file di risposta
Gli amministratori che distribuiscono Visual Studio possono specificare un file di risposta usando il parametro `--in`, ad esempio:

```
vs_enterprise.exe --in customInstall.json
```

I file di risposta sono costituiti da file [JSON](http://json-schema.org/) i cui contenuti riflettono gli argomenti della riga di comando.  In generale, se un parametro della riga di comando non accetta argomenti (ad esempio `--quiet`, `--passive` e così via), il valore nel file di risposta deve essere true o false.  Se invece accetta un argomento (ad esempio `--installPath <dir>`), il valore nel file di risposta deve essere una stringa.  Se accetta un argomento e può apparire più di una volta nella riga di comando (ad esempio `--add <id>`), deve essere una matrice di stringhe.

I parametri specificati nella riga di comando sostituiscono le impostazioni ricavate dal file di risposta, tranne nel caso di parametri che accettano più input (ad esempio `--add`), in cui gli input specificati nella riga di comando vengono uniti con le impostazioni ottenute dal file di risposta.

# <a name="setting-a-default-configuration-for-visual-studio"></a>Impostazione di una configurazione predefinita per Visual Studio

Se è stata creata una cache di layout di rete con l'opzione `--layout`, nel layout viene creato un file `response.json` iniziale.

Gli amministratori che creano un layout possono modificare il file `response.json` nel layout per controllare le impostazioni predefinite che gli utenti visualizzeranno durante l'installazione di Visual Studio dal layout.  Se, ad esempio, un amministratore vuole che, per impostazione predefinita, vengano installati specifici carichi di lavoro e componenti, per aggiungerli può configurare il file `response.json`.

Se l'installazione di Visual Studio viene eseguita da una cartella di layout, verrà _automaticamente_ usato il file di risposta nella cartella di layout.  Non è necessario usare l'opzione `--in`.

È possibile aggiornare il file `response.json` creato in una cartella di layout offline per definire l'impostazione predefinita per gli utenti che eseguono l'installazione da questo layout. **È essenziale tuttavia lasciare invariate le proprietà esistenti definite al momento della creazione del layout.**

In un layout, il file `response.json` di base avrà un aspetto simile all'esempio seguente, ma con un valore adeguato al prodotto e al canale che si sta installando:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

## <a name="example-layout-response-file-content"></a>Esempio di contenuto del file di risposta del layout
In questo esempio verrà installato Visual Studio Enterprise con sei carichi di lavoro e componenti comuni, con interfaccia utente sia in inglese che in francese. È possibile usare questo esempio come modello, semplicemente sostituendo i carichi di lavoro e i componenti con quelli che si vuole installare.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```
## <a name="see-also"></a>Vedere anche
* [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md)

