---
title: Considerazioni speciali per l&quot;installazione di Visual Studio in un ambiente offline | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 05/09/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.openlocfilehash: b596b6b6f9cff58525d253157534b6b990c68fcd
ms.contentlocale: it-it
ms.lasthandoff: 05/09/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considerazioni speciali per l'installazione di Visual Studio in un ambiente offline

Visual Studio è progettato per essere installato da un computer connesso a Internet, poiché molti componenti vengono aggiornati regolarmente. Con alcuni passaggi aggiuntivi, tuttavia, è possibile distribuire Visual Studio anche in un ambiente in cui non è disponibile una connessione Internet.

## <a name="create-a-network-installation-layout"></a>Creare un layout di installazione di rete
* Per informazioni dettagliate, vedere [Creare un'installazione di rete di Visual Studio](create-a-network-installation-of-visual-studio.md)

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installare i certificati necessari per l'installazione offline di Visual Studio
Il motore di installazione di Visual Studio installa solo contenuti attendibili.  Verifica le firme Authenticode dei contenuti scaricati e, prima di installarli, ne controlla l'attendibilità.  I computer con accesso a Internet scaricano e installano automaticamente i certificati necessari per verificare le firme dei file.  Se si opera in un ambiente offline o si usa un sistema con connettività Internet scadente, tuttavia, questa operazione può non essere possibile.  In questi casi, è opportuno accertarsi che i certificati necessari vengano pre-installati.  Questi certificati vengono scaricati dal computer di esecuzione nella cartella "certificati" durante la creazione di un'installazione offline.

È possibile installare manualmente i certificati sul client facendo doppio clic sul file di certificato e seguendo la procedura guidata del gestore di certificati. Se viene richiesto di immettere una password, lasciare il campo vuoto.

Per creare uno script di installazione dei certificati, seguire questa procedura:

1. Copiare certmgr.exe nella condivisione di installazione (ad esempio, `\server\share\vs2017`). `certmgr.exe` è incluso in Windows SDK, che può essere installato come componente facoltativo del carico di lavoro _Sviluppo della piattaforma UWP (Universal Windows Platform)_. (Ad esempio: `"C:\Program Files (x86)\Windows Kits\10\bin\x86\certmgr.exe"`)

2. Creare un file batch con i comandi seguenti:

```cmd
\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

\\server\share\vs2017\certmgr.exe -add -c \\server\share\vs2017\certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
```

3. Eseguire il file batch sul client da una shell dei comandi per amministratore o un da processo con privilegi elevati.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Perché i certificati della cartella `certificates` non vengono installati automaticamente?
Se una firma viene verificata in un ambiente online, per scaricare e aggiungere i certificati al sistema vengono usate le API di Windows. È nel corso di questo processo che, tramite impostazioni amministrative, si verifica se il certificato è attendibile e consentito. Questo processo di verifica, tuttavia, non può aver luogo nella maggior parte degli ambienti offline. Con l'installazione manuale dei certificati, l'utente può verificare che i certificati siano attendibili e soddisfare i requisiti dell'amministratore.

## <a name="install-visual-studio"></a>Installare Visual Studio
Dopo aver installato i certificati, la distribuzione di Visual Studio può procedere offline senza altri passaggi speciali seguendo [queste istruzioni](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)

