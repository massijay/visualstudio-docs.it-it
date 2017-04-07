---
title: "Simboli per il debug in modalità mista con Python Tools for Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Installazione dei simboli di debug per interpreti Python

Per offrire un'esperienza di debug completa, il [debugger in modalità mista](debugging-mixed-mode.md) in Python Tools for Visual Studio (PTVS) deve analizzare numerose strutture di dati interne nell'interprete Python in uso. A questo scopo sono necessari i simboli di debug per l'interprete in questione. Ad esempio, il file di simboli corrispondenti per python27.dll è python27.pdb.

Quando PTVS rileva che sono necessari i simboli, richiede di selezionare una cartella contenente i file di simboli o di eseguirne il download:

![Richiesta dei simboli durante il debug in modalità mista](media/mixed-mode-debugging-symbols-required.png) 

È possibile scaricare i file di simboli dalla pagina di [distribuzione ufficiale](#official-distribution) o da [Enthought Canopy](#enthought-canopy) come descritto di seguito. Se si usa una distribuzione Python di terze parti, ad esempio ActiveState Python, sarà necessario contattare gli autori di tale distribuzione e richiedere loro di fornire i simboli. WinPython, tuttavia, incorpora l'interprete Python standard senza modifiche, quindi usare i simboli dalla distribuzione ufficiale per il numero di versione corrispondente.

Dopo aver ottenuto i file con estensione pdb per l'interprete, è necessario fare in modo che vengano riconosciuti da PTVS come indicato di seguito, per ottenere il caricamento automatico all'avvio delle sessioni di debug:

1. Selezionare il comando di menu **Strumenti > Opzioni** e quindi passare a **Debug > Simboli**:

![Opzioni per i simboli del debugger in modalità mista](media/mixed-mode-debugging-symbols.png)

1. Selezionare il pulsante Aggiungi sulla barra degli strumenti (il pulsante all'estrema sinistra illustrato in precedenza, a destra dell'icona !), passare alla cartella contenente i file con estensione pdb e selezionare **OK**.


## <a name="official-distribution"></a>Distribuzione ufficiale

Con Python 3.5 e versioni successive, è possibile includere i simboli di debug tramite il programma di installazione (sia tramite una nuova installazione che modificandone una esistente). Selezionare **Custom installation** (Installazione personalizzata), selezionare **Next** (Avanti) per passare ad **Advanced Options** (Opzioni avanzate) e quindi selezionare le caselle "Download debugging symbols**(Scarica simboli di debug) e**Download debug binaries**(Scarica file binari di debug):

![Programma di installazione di Python 3.x con l'opzione per includere i simboli di debug](media/mixed-mode-debugging-symbols-installer35.png)

Per Python 3.4.x e versioni precedenti, i simboli sono disponibili come file ZIP scaricabili. Dopo il download, estrarre questi file in una cartella e seguire le istruzioni nella sezione precedente per registrarli in PTVS.

| Versione di Python | Download | 
| --- | --- | 
| 3.4.4 | [32 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 bit](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 bit](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 bit](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 bit](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 bit](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 bit](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 bit](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 bit](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 bit](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 bit](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 bit](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 bit](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 bit](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy fornisce i simboli per i relativi file binari a partire dalla versione 1.2. I simboli vengono installati automaticamente insieme alla distribuzione, ma è comunque necessario aggiungere manualmente la cartella che li contiene al percorso dei simboli come descritto in precedenza. Per un'installazione tipica per utente di Canopy, i simboli si trovano in `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` per la versione a 64 bit e in `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts` per la versione a 32 bit.

Enthought Canopy 1.1 e versioni precedenti, così come Enthought Python Distribution (EPD), non forniscono simboli per l'interprete e pertanto non sono compatibili con il debug in modalità mista.
