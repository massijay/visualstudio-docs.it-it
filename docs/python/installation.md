---
title: Installazione per Python in Visual Studio | Microsoft Docs
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
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 613af31a2e44cc447980b68de4b0b5642dde1262
ms.contentlocale: it-it
ms.lasthandoff: 07/18/2017

---

# <a name="installing-python-support-in-visual-studio-on-windows"></a>Installazione del supporto di Python in Visual Studio in Windows

Per installare il supporto Python per Visual Studio, seguire le istruzioni nella sezione corrispondente alla versione in uso di Visual Studio:

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 e versioni precedenti](#visual-studio-2013-and-earlier)

Per Visual Studio 2015 e versioni precedenti è anche necessario installare separatamente un interprete Python a scelta. Per informazioni dettagliate, vedere [Ambienti Python](python-environments.md).

Per testare rapidamente il supporto Python dopo aver eseguito la procedura di installazione, aprire la finestra interattiva di Python premendo ALT+I e quindi immettere `2+2`. Se non viene visualizzato l'output `4`, eseguire nuovamente la procedura.

> [!Tip]
> Il carico di lavoro Python include l'utile estensione Cookiecutter, che offre un'interfaccia utente grafica per individuare modelli, inserire opzioni del modello e creare progetti e file. Per informazioni dettagliate, vedere [Uso dell'estensione Cookiecutter](cookiecutter.md).

> [!Note]
> Il supporto Python non è attualmente disponibile in Visual Studio per Mac, ma viene offerto su Mac e Linux tramite Visual Studio Code. Vedere [Domande e risposte](python-in-visual-studio.md#questions-and-answers).

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. Installare Visual Studio 2017 da [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/).

1. Nel programma di installazione di Visual Studio selezionare il carico di lavoro **Web e cloud > Sviluppo Python**.

    ![Carico di lavoro Sviluppo Python nel programma di installazione di Visual Studio](media/installation-python-workload.png)

    > [!Note]
    > Python è incluso anche nel carico di lavoro **Applicazioni analitiche e di analisi scientifica dei dati**.

1. Sul lato destro del programma di installazione selezionare gli interpreti Python e altri strumenti correlati da includere. Ad esempio, se si prevede di sviluppare estensioni C++ per Python, includere l'opzione **Strumenti di sviluppo nativi Python**.

    ![Opzioni di sviluppo Python nel programma di installazione di Visual Studio](media/installation-python-options.png)

1. Se nel computer in uso sono già installati interpreti, vedere [Creazione di un ambiente per un interprete esistente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. Per eseguire il programma di installazione di Visual Studio, scegliere **Pannello di controllo > Programmi e funzionalità**, selezionare **Microsoft Visual Studio 2015** e quindi **Cambia**.

1. Nel programma di installazione selezionare **Modifica**.

1. Selezionare **Linguaggi di programmazione > Python Tools for Visual Studio** e quindi **Avanti**:

    ![Opzione PTVS nel programma di installazione di Visual Studio 2015](media/installation-vs2015.png)    

1. Una volta completata l'installazione di Visual Studio, [installare un interprete Python a scelta](python-environments.md#selecting-and-installing-python-interpreters). Se è già installato un interprete, vedere [Creazione di un ambiente per un interprete esistente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 e versioni precedenti

1. Installare la versione appropriata di Python Tools for Visual Studio per la versione in uso di Visual Studio:

    - Visual Studio 2013: [PTVS 2.2 for Visual Studio 2013](https://github.com/Microsoft/PTVS/releases/v2.2). È possibile accedere rapidamente a questo processo dalla finestra di dialogo **File > Nuovo progetto** di Visual Studio 2013.
    - Visual Studio 2012: [PTVS 2.1 for Visual Studio 2012](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [PTVS 2.1 for Visual Studio 2010](https://pytools.codeplex.com/downloads/get/920479)

1. [Installare un interprete Python a scelta](python-environments.md#selecting-and-installing-python-interpreters). Se è già installato un interprete, vedere [Creazione di un ambiente per un interprete esistente](python-environments.md#creating-an-environment-for-an-existing-interpreter).

## <a name="install-locations"></a>Percorsi di installazione

Per impostazione predefinita, il supporto Python viene installato per tutti gli utenti di un computer.

Per Visual Studio 2017, il carico di lavoro Python è installato in `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`, dove &lt;VS_edition&gt; corrisponde a Community, Professional o Enterprise.

Per Visual Studio 2015 e versioni precedenti, i percorsi di installazione sono i seguenti:

- 32 bit:
  - Percorso: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Chiave del Registro di sistema relativa al percorso: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64 bit:
  - Percorso: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - Chiave del Registro di sistema relativa al percorso: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

dove:

- &lt;VS_ver&gt; corrisponde a:    
    - 14.0 per Visual Studio 2015
    - 12.0 per Visual Studio 2013
    - 11.0 per Visual Studio 2012
    - 10.0 per Visual Studio 2010
- &lt;PTVS_ver&gt; corrisponde a un numero di versione, ad esempio 2.2, 2.1, 2.0, 1.5, 1.1 o 1.0.

### <a name="user-specific-installations-15-and-earlier"></a>Installazioni specifiche dell'utente (versione 1.5 e versioni precedenti)

Con Python Tools for Visual Studio 1.5 e versioni precedenti è consentita l'installazione solo per l'utente corrente. In tal caso, il percorso di installazione è `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>` dove i valori di &lt;VS_ver&gt; e &lt;PTVS_ver&gt; sono uguali a quelli descritti in precedenza.

