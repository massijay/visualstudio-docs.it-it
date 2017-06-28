---
title: Installare Dotfuscator Community Edition (CE) | Microsoft Docs
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protezione, edizione community, offuscamento, .NET, gratuito, Visual Studio 2017, installare
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator installer
- Dotfuscator setup
- install Dotfuscator
- installing Dotfuscator
- set up Dotfuscator
description: Informazioni su come installare la versione gratuita di Dotfuscator Community Edition inclusa in Visual Studio 2017.
ms.assetid: f2146651-e24a-4e24-ade8-8ddee8ff4e43
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 507ff049dae50698d86e1536ed21ab982da1af85
ms.openlocfilehash: 4831a41cc82ecb1030d61263f46b1d41ec0c37a1
ms.lasthandoff: 02/22/2017

---

# <a name="install-dotfuscator-community-edition-ce"></a>Installare Dotfuscator Community Edition (CE)

Visual Studio 2017 introduce una nuova esperienza di installazione di basso impatto.
Di conseguenza, Dotfuscator Community Edition (Dotfuscator CE) non è installato automaticamente per impostazione predefinita.
È tuttavia facile installare Dotfuscator CE, anche se è già stato installato Visual Studio.

> [!NOTE]
> Oltre alle versioni di Dotfuscator CE incluse nelle versioni di Visual Studio, PreEmptive Solutions offre periodicamente anche versioni aggiornate sul proprio sito Web.
> Se si vuole scaricare la **versione più recente** direttamente anziché eseguire l'installazione da Visual Studio, ** [fare clic qui per passare alla pagina di download di Dotfuscator][download]**.

## <a name="within-visual-studio"></a>Da Visual Studio

È possibile installare Dotfuscator CE dall'IDE di Visual Studio:

1. Nella barra di ricerca dell'**Avvio veloce** (CTRL + Q) digitare `dotfuscator`. <br/> <br/> ![](media/install_from_vs_12.png) <br/> <br/>
2. Nei risultati visualizzati nell'Avvio veloce, sotto l'intestazione *Installa*, selezionare **PreEmptive Protection - Dotfuscator (Individual Component)**.
  * Se invece sotto l'intestazione *Menu* viene visualizzato **Strumenti → PreEmptive Protection - Dotfuscator** vuol dire che Dotfuscator CE è già installato. Per informazioni dettagliate sull'uso, vedere la [pagina introduttiva della Guida dell'utente completa di Dotfuscator CE][get-started].
3. Viene visualizzata la finestra del programma di installazione di Visual Studio, preconfigurato per installare Dotfuscator CE.
  * Potrebbe essere necessario specificare credenziali di amministratore per continuare.
4. Chiudere tutte le istanze dell'IDE di Visual Studio. <br/> <br/> ![](media/install_from_vs_345.png) <br/> <br/>
5. Fare clic su *Installa* nella finestra del programma di installazione di Visual Studio.

Al termine dell'installazione, è possibile iniziare a usare Dotfuscator CE. Per informazioni dettagliate, vedere la [pagina introduttiva della Guida dell'utente completa di Dotfuscator CE][get-started].

## <a name="during-visual-studio-installation"></a>Durante l'installazione di Visual Studio

Se non è ancora stato installato Visual Studio 2017, è possibile ottenere il programma di installazione dal [sito Web di Visual Studio][2017-install].
Durante l'esecuzione, verranno visualizzate le opzioni di installazione per l'edizione di Visual Studio selezionata.

![](media/install_ui.png)

È possibile quindi installare Dotfuscator CE come componente singolo di Visual Studio 2017:

1. Selezionare la scheda **Singoli componenti**.
2. In *Strumenti per il codice*, verificare l'elemento *PreEmptive Protection - Dotfuscator*.<br/> <br/> ![](media/install_individually_12.png) <br/> <br/>
3. Il pannello *Riepilogo* visualizza *PreEmptive Protection - Dotfuscator* sotto la sezione *Singoli componenti*. <br/> <br/> ![](media/install_individually_3.png) <br/> <br/>
4. Configurare le altre impostazioni di installazione come appropriato per l'ambiente.
5. Quando si è pronti per installare Visual Studio, fare clic sul pulsante *Installa*.

Al termine dell'installazione, è possibile iniziare a usare Dotfuscator CE. Per informazioni dettagliate, vedere la [pagina introduttiva della Guida dell'utente completa di Dotfuscator CE][get-started].

## <a name="see-also"></a>Vedere anche

[Questo argomento nella Guida dell'utente completa di Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[2017-install]: https://www.visualstudio.com/downloads/#vs-2017
[get-started]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/gui_getstarted.html

[download]: https://www.preemptive.com/products/dotfuscator/downloads

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/intro_install.html