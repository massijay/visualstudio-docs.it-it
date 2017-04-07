---
title: Python in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
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
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: 746dd25dde790d5e262e25a3702b49721edc3510
ms.lasthandoff: 03/22/2017

---

# <a name="working-with-python-in-visual-studio"></a>Uso di Python in Visual Studio

Python è un linguaggio di programmazione molto diffuso affidabile, flessibile, facile da imparare, utilizzabile gratis in tutti i sistemi operativi e supportato da un'attiva community di sviluppatori e da numerose librerie gratuite. Python supporta tutte le modalità di sviluppo, tra cui applicazioni Web, servizi Web, app desktop, script e calcolo scientifico. Viene usato in molte università, nonché da scienziati, sviluppatori professionisti e non professionisti. Per altre informazioni sul linguaggio, vedere [python.org](https://www.python.org) e [Python for Beginners](https://www.python.org/about/gettingstarted/) (Python per principianti).

Visual Studio offre supporto [open source](https://github.com/Microsoft/ptvs) per Python tramite il carico di lavoro Python (Visual Studio 2017) e l'estensione gratuita Python Tools for Visual Studio (Visual Studio 2015 e versioni precedenti). 

Seguire le [istruzioni di installazione](installation.md) per configurare il carico di lavoro Python, quindi usare i collegamenti seguenti per saperne di più sulle funzionalità correlate a Python, nonché sulle funzionalità di Visual Studio stesso.

| Funzionalità | Descrizione | Documentazione generale su Visual Studio | 
| --- | --- | --- |
| [Sistema del progetto di Visual Studio](python-projects.md) | Rileva in modo implicito una struttura di cartelle del codice Python consentendo anche un controllo esplicito per distinguere chiaramente i vari elementi di codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via. | [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Modelli di progetto](python-projects.md#project-templates) | Consente di creare rapidamente la struttura del progetto per console, Web, Azure, analisi scientifica dei dati e altri tipi di progetti. | [Modelli di Visual Studio](../ide/creating-project-and-item-templates.md#visual-studio-templates) |
| Supporto per più interpreti | Supporta diverse versioni di CPython e IronPython. | n/d |
| Supporto di IPython | Include il supporto per IPython/Jupyter in REPL per grafici inline, .NET e Windows Presentation Foundation (WPF). | n/d |
| [Modifica avanzata, IntelliSense e comprensione del codice](code-editing.md) | Colorazione della sintassi, completamento automatico in tutto il codice e in tutte le librerie, [formattazione del codice](code-formatting.md), supporto per la firma, visualizzazione delle classi, accesso alle definizioni, opzione per trovare tutti i riferimenti, frammenti di codice, [refactoring](code-refactoring.md), [PyLint](code-pylint.md) e altro ancora. | [Scrittura di codice nell'Editor di testo e del codice](../ide/writing-code-in-the-code-and-text-editor.md) |
| [Finestra interattiva](interactive-repl.md) | Fornisce un'esperienza rapida di REPL per Python e consente di evidenziare facilmente una parte del codice e di inviarla alla finestra interattiva. | n/d |
| [Debug con funzionalità complete](debugging.md) | Il debug può essere eseguito con o senza un progetto di Visual Studio. Include funzionalità per il collegamento a un eseguibile esistente, il [debug Python/C++ in modalità mista](debugging-mixed-mode.md), il [debug remoto](debugging-cross-platform-remote.md) in Linux/Windows/Mac, il [debug remoto in Azure](debugging-azure-remote.md) e il debug all'interno della finestra interattiva. | [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md) |
| [Strumenti di profilatura con funzionalità complete di creazione report](profiling.md) | Esamina l'uso del tempo nell'applicazione e consente di confrontare le prestazioni tra diverse esecuzioni della profilatura. | [Strumenti di profilatura](../profiling/profiling-tools.md) (non tutte le funzionalità di profilatura di Visual Studio sono disponibili per Python) |
| [Strumenti per unit test](unit-testing.md) | Consentono di individuare, eseguire e gestire i test in Esplora test di Visual Studio e di eseguire facilmente il debug di unit test. | [Eseguire unit test del codice](../test/unit-test-your-code.md) |

Il carico di lavoro Python include anche [Azure SDK per Python](azure-sdk-for-python.md), che semplifica l'utilizzo dei servizi Azure e offre il supporto per Windows, Mac OS X e Linux.

Vedere anche la serie di [video introduttivi e di approfondimento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff) su YouTube, che offrono una panoramica delle funzionalità principali.

[![Video su Python Tools](media/video-general.png)](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

## <a name="features-matrix"></a>Matrice delle funzionalità

È possibile installare il supporto per Python nelle edizioni seguenti di Visual Studio, come descritto nella [guida all'installazione](installation.md):

- [Visual Studio 2017 Preview](https://www.visualstudio.com/vs/preview)
- [Visual Studio 2015 (tutte le edizioni)] (https://www.visualstudio.com/it-it/downloads/visual-studio-2015-downloads-vs)
- [Visual Studio 2013 Community Edition] (https://www.visualstudio.com/it-it/products/visual-studio-community-vs.aspx)
- [Visual Studio 2013 Express per il Web, Update 2 o versione successiva](http://www.microsoft.com/en-us/download/details.aspx?id=40747)
- [Visual Studio 2013 Express per Desktop, Update 2 o versione successiva](http://www.microsoft.com/en-us/download/details.aspx?id=40787)
- Visual Studio 2013 (Professional Edition o versione successiva)
- Visual Studio 2012 (Professional Edition o versione successiva)
- Visual Studio 2010 SP1 (Professional Edition o versione successiva; richiede .NET 4.5)

Funzionalità supportate in base alla versione e all'edizione di Visual Studio:

| Supporto per Python | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Gestione di più interpreti | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rilevamento automatico degli interpreti più comuni | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Aggiunta di interpreti personalizzati | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Ambienti virtuali | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Installazione Pip/semplificata | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Sistema del progetto | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Nuovo progetto da codice esistente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Mostra tutti i file | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Controllo del codice sorgente | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Integrazione con Git | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004;<sup>1</sup> | &#10007; |
<br/>

| Modifica | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Evidenziazione della sintassi | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Completamento automatico | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Supporto per la firma | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Informazioni rapide | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Visualizzatore oggetti/Visualizzazione classi | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Barra di navigazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Vai a definizione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Passa a | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Trova tutti i riferimenti | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Rientro automatico | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Formattazione del codice | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Ridenominazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Estrazione del metodo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Refactoring - Aggiunta/rimozione dell'importazione | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| PyLint | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Finestra interattiva | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Finestra interattiva | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| IPython con grafici inline | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Desktop | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Applicazione console/Windows | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| WPF IronPython (con finestra di progettazione XAML) | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Windows Form IronPython | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Web | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Progetto Web Django | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web Bottle | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web Flask | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Progetto Web generico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Azure | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Distribuzione Web in sito Web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004;<sup>2</sup> |
| Distribuzione Web in ruolo Web | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Distribuzione Web in ruolo di lavoro | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Esecuzione nell'emulatore di Azure | ? | ? | ? | &#10007; | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> | &#10007; |
| Debug remoto | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> | &#10007; |
| Collegamento a Esplora server | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> | &#10007; | &#10007; |
<br/>

| Modelli Django | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debug | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; | &#10004; |
| Completamento automatico | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004; | &#10004; |
| Completamento automatico per CSS e JavaScript | &#10004; | &#10004; | &#10004; | &#10007; | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007; | &#10007; |
<br/>

| Debug | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Debug | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debug senza progetto | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
| Debug - Collegamento a modifica | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Debug in modalità mista | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debug remoto (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; | &#10004; | &#10004; | &#10004; |
| Finestra Debug interattivo | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; |
<br/>

| Profilatura | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | ---|
| Profilatura | &#10004; | &#10004; | &#10004; | &#10007; | &#10007; | &#10004; | &#10004; | &#10004; |
<br/>

| Test | 2017 | 2015 | 2013 Community | 2013 Desktop | 2013 Web | 2013 Professional e successive | 2012 Professional e successive | 2010 SP1 Professional e successive |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Esplora test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Esegui test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
| Debug di test | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10004; | &#10007; |
<br/>

1. Il supporto GIT per Visual Studio 2012 è incluso nell'estensione Visual Studio Tools for Git, disponibile in [Visual Studio Gallery](http://visualstudiogallery.msdn.microsoft.com/abafc7d6-dcaa-40f4-8a5e-d6724bdb980c).

2. Per la distribuzione nel sito Web di Azure è necessario [Azure SDK per .NET 2.1 - Visual Studio 2010 SP1](http://go.microsoft.com/fwlink/?LinkId=313855).  Visual Studio 2010 non è supportato nelle versioni successive.

3. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkId=323511) o versione successiva.

4. Per il supporto per il ruolo di lavoro e il ruolo Web di Azure è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

5. L'editor di modelli Django in Visual Studio 2013 presenta alcuni problemi noti che vengono risolti installando l'Update 2.

6. Richiede Windows 8 o versione successiva. La finestra Collega a processo non è disponibile in Visual Studio 2013 Express per il Web, ma è comunque possibile eseguire il debug remoto del sito Web di Azure usando il comando Collega debugger (Python) in Esplora server. Per questo comando è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

7. Richiede Windows 8 o versione successiva. Per il comando Collega debugger (Python) in Esplora server è richiesto [Azure SDK per .NET 2.3 - Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkId=323510) o versione successiva.

8. Richiede Windows 8 o versione successiva.

## <a name="additional-resources"></a>Risorse aggiuntive

- [Writing Kinect games with Python using PyKinect](https://github.com/Microsoft/PTVS/wiki/PyKinect) (Uso di PyKinect per scrivere di giochi Kinect con Python) (wiki GitHub)
- [WFastCGI bridge between IIS and Python](https://pypi.python.org/pypi/wfastcgi) (Ponte WFastCGI tra IIS e Python) (python.org)

