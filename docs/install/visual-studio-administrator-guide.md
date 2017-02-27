---
title: "Guida di Visual Studio Administrator | Microsoft Docs"
ms.custom: ""
ms.date: "01/12/2017"
ms.prod: "visual-studio-dev15"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "installazione di rete, Visual Studio"
  - "guida dell'amministratore, Visual Studio"
  - "installazione di Visual Studio, guida dell'amministratore"
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
caps.handback.revision: 68
---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017-rc"></a>Guida dell'amministratore di Visual Studio per Visual Studio 2017 RC

È possibile distribuire Visual Studio in una rete purché ogni computer di destinazione soddisfi i [requisiti di installazione minimi](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). È possibile creare una condivisione di rete eseguendo il file di installazione con l'opzione --layout, come descritto nella pagina [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md), e quindi copiarla dal computer locale alla condivisione di rete.   

 Si noti che le installazioni eseguite da una condivisione di rete "ricordano" il percorso di origine da cui provengono. Ciò significa che per il ripristino di un computer client potrebbe essere necessario tornare alla condivisione di rete client da cui è stato installato in origine il client. Scegliere con attenzione il percorso di rete in modo che sia adeguato al periodo di tempo in cui si prevede di eseguire i client di Visual Studio 2017 nella propria organizzazione.  

 > [!IMPORTANT]
 > Sebbene Visual Studio 2017 RC in generale sia supportato per l'uso in un ambiente di produzione, i carichi di lavoro e i componenti contrassegnati come "Anteprima" o "Preview" nell'interfaccia utente di installazione non sono supportati per l'uso in un ambiente di produzione.

## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio 2017 RC](install-visual-studio.md)
* [Usare i parametri della riga di comando per installare Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md)
* [Create an offline installation of Visual Studio 2017](create-an-offline-installation-of-visual-studio.md) (Creare un'installazione offline di Visual Studio 2017)
* [Come segnalare un problema con Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->


