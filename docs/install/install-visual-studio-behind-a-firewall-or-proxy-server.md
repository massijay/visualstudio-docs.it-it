---
title: Installazione di Visual Studio protetto da un firewall o un server proxy | Microsoft Docs
description: 
ms.custom: 
ms.date: 08/01/2017
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
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: f23906933add1f4706d8786b2950fb3b5d2e6781
ms.openlocfilehash: 0803ea25bd8f45d79d618ff481094fb5786b1acb
ms.contentlocale: it-it
ms.lasthandoff: 08/14/2017

---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Installazione di Visual Studio protetto da un firewall o un server proxy

Il programma di installazione Visual Studio scarica i file da vari domini e dai relativi server di download. In questa pagina sono elencati gli URL di dominio che si possono aggiungere all'elenco elementi consentiti come attendibili negli script di distribuzione.

Se è possibile nell'ambiente in uso, è consigliabile aggiungere i domini seguenti con i protocolli HTTP e HTTPS.

## <a name="microsoft-domains"></a>Domini Microsoft
| Dominio | Scopo |
| ------ | ------- |
| go.microsoft.com | Risoluzione degli URL di installazione |
| aka.ms | Risoluzione degli URL di installazione |
| download.visualstudio.microsoft.com | Percorso di download dei pacchetti di installazione |
| download.microsoft.com | Percorso di download dei pacchetti di installazione |
| download.visualstudio.com | Percorso di download dei pacchetti di installazione |
| dl.xamarin.com | Percorso di download dei pacchetti di installazione |
| visualstudiogallery.msdn.microsoft.com | Percorso di download delle estensioni di Visual Studio |
| www.visualstudio.com | Percorso della documentazione |
| docs.microsoft.com | Percorso della documentazione |
| msdn.microsoft.com | Percorso della documentazione |
| www.microsoft.com | Percorso della documentazione |
| *.windows.net | Percorso di accesso |
| *.microsoftonline.com | Percorso di accesso |
| *.live.com | Percorso di accesso |


## <a name="non-microsoft-domains"></a>Domini non Microsoft
| Dominio | Installa questi carichi di lavoro |
| ------ | ------- |
| archive.apache.org |  Sviluppo di app per dispositivi mobili con JavaScript <br />(Cordova) |
| cocos2d-x.org | Sviluppo di giochi con C++ <br />(Cocos) |
| download.epicgames.com | Sviluppo di giochi con C++ <br />(Unreal Engine) |
| download.oracle.com | Sviluppo di app per dispositivi mobili con JavaScript <br />(Java SDK) <br /><br />Sviluppo di app per dispositivi mobili con .NET <br />(Java SDK) |
| download.unity3d.com | Sviluppo di giochi con Unity <br />(Unity) |
| netstorage.unity3d.com | Sviluppo di giochi con Unity <br /> (Unity) |
| dl.google.com | Sviluppo di app per dispositivi mobili con JavaScript <br />(Android SDK e NDK, emulatore) <br /><br />Sviluppo di app per dispositivi mobili con .NET <br />(Android SDK e NDK, emulatore) |
| www.incredibuild.com | Sviluppo di giochi con C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Sviluppo di giochi con C++ <br />(IncrediBuild) |
| www.python.org | Sviluppo Python <br />(Python) <br /><br />Applicazioni analitiche e di analisi scientifica dei dati <br />(Python) |

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
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

