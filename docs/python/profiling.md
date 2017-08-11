---
title: Misurazione delle prestazioni del codice Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2723d4d0-89c8-4279-bfc2-27c0834a997e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: f01c42f073859e2e609123eb67cc9df8e26cef75
ms.contentlocale: it-it
ms.lasthandoff: 07/18/2017

---

# <a name="profiling-python-code"></a>Profilatura del codice Python

In Visual Studio è possibile eseguire la profilatura di un'applicazione Python quando si usano interpreti basati su CPython.

Per avviare la profilatura, si usa il comando di menu **Analizza > Avvia profilatura Python**, che consente di aprire una finestra di dialogo di configurazione:

![Finestra di dialogo di configurazione della profilatura](media/profiling-start.png)

Quando si fa clic su **OK**, viene eseguito il profiler e si apre un report di prestazioni che illustra in che modo viene impiegato il tempo nell'applicazione:

![Report di prestazioni del profiler](media/profiling-results.png)

Per una panoramica, vedere l'argomento seguente.

Per una procedura dettagliata dimostrativa, vedere il video [Profiling with Python Tools for Visual Studio](http://www.youtube.com/watch?v=K-KqkFkp55k) (Profilatura con Python Tools for Visual Studio) (durata: 8 minuti e 52 secondi).

> [!VIDEO https://www.youtube.com/embed/K-KqkFkp55k]

## <a name="profiling-for-ironpython"></a>Profilatura per IronPython

Dal momento che IronPython non è un interprete basato su CPython, la funzionalità di profilatura illustrata sopra non funziona.

Usare invece il profiler di Visual Studio .NET avviando direttamente `ipy.exe` come applicazione di destinazione e usando gli argomenti appropriati per eseguire lo script di avvio. Includere `-X:Debug` nella riga di comando per forzare il debug e la profilatura per tutto il codice Python. Questo argomento genera un report di prestazioni che include il tempo impiegato sia nel runtime di IronPython che nel codice. Per identificare il codice, vengono usati nomi modificati.

In alternativa, IronPython presenta alcune funzionalità di profilatura incorporate, per le quali però non esiste ancora alcun visualizzatore adeguato. Per informazioni sulle opzioni disponibili, vedere [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Profiler per IronPython) nei blog di MSDN.
