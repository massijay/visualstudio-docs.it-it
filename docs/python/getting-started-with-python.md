---
title: "Introduzione a Python | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 11
caps.handback.revision: 10
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---
# Introduzione a Python
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft fornisce Python Tools for Visual Studio \(PTVS\), un potente plug\-in dell'IDE Python, gratuitamente come [progetto open source](https://github.com/Microsoft/ptvs).  
  
## Linguaggio Python  
 Python è stato per lungo tempo un linguaggio di programmazione molto diffuso, usato da molte società, informatici, programmatori occasionali e professionisti \(app, servizi cloud\/Web e siti Web\) e autori di app.  Python offre numerose caratteristiche positive:  
  
-   Affidabilità  
  
-   Utile generalmente per lo sviluppo di programmi rapidi, app, app desktop, server Web, servizi Web e nel calcolo scientifico  
  
-   Facile da imparare e con un buon design in modo da semplificare la scrittura di codice \(molte università lo usano per i corsi di programmazione introduttivi\)  
  
-   Supporta una varietà di stili di programmazione: imperativo, funzionale e orientato agli oggetti  
  
-   Open source gratuito che funziona bene con tutti i principali sistemi operativi  
  
-   Numerose librerie gratuite, utili e ben progettate  
  
-   Un elevato numero di esempi, documentazioni e guide disponibili su Internet  
  
 [Installazione di Python](http://python.org/download/)  
  
## PTVS  
 Microsoft fornisce Python Tools for Visual Studio \(PTVS\), un potente plug\-in dell'IDE Python, gratuitamente come progetto open source \([PTVS](http://pytools.codeplex.com/)\):  
  
 Alcune caratteristiche principali di PTVS:  
  
-   Supporta più interpreti: varie versioni di CPython, IronPython e IPython  
  
-   Sistema di progetto che rileva in modo implicito una struttura di directory del codice Python o che è possibile controllare in modo esplicito per distinguere chiaramente i vari elementi di codice dell'app, codice di test, pagine Web, JavaScript, script di compilazione e così via  
  
-   Modelli di progetto per programmi console, progetti Web, progetti Azure, progetti di data science e così via  
  
-   Azure SDK per Python \(vedere più avanti\)  
  
-   Funzionalità avanzate di modifica e comprensione del codice: colorazione, completamento in tutto il codice e le librerie, supporto firma, visualizzazione classi, opzione per passare alla definizione, opzione per trovare tutti i riferimenti, refactoring e così via  
  
-   Finestra interattiva \(REPL\) e IPython con visualizzazioni dei dati  
  
-   Supporto per IronPython e .NET\/WPF  
  
-   Debug avanzato senza progetto, collegamento a un eseguibile esistente, debug in modalità mista, debug remoto per Linux\/Windows\/Mac e debug all'interno della finestra interattiva  
  
-   Strumenti di profilatura  
  
-   Strumenti di test  
  
 [Home page di PTVS](https://www.visualstudio.com/en-us/explore/python-vs)  
  
 [Brevi video di introduzione e approfondimento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
  
 [Demo sull'installazione e le funzionalità \(27 minuti\)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
  
 [Documenti Wiki](http://pytools.codeplex.com/documentation)  
  
 [Installazione di PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation)  
  
## Azure  
 Azure SDK per Python semplifica l'utilizzo e la gestione dei servizi di Microsoft Azure.  Azure SDK per Python supporta Windows, Mac e Linux.  
  
 Il [centro per sviluppatori Python](http://azure.microsoft.com/en-us/develop/python/) offre moltissime guide dall'installazione alla documentazione con esercitazioni.  Seguono alcune delle principali caratteristiche:  
  
-   [BLOB di archiviazione](http://azure.microsoft.com/en-us/develop/python/how-to-guides/blob-service/)  
  
-   [Coda di archiviazione](http://azure.microsoft.com/en-us/develop/python/how-to-guides/queue-service/)  
  
-   [Tabella di archiviazione](http://azure.microsoft.com/en-us/develop/python/how-to-guides/table-service/)  
  
-   [Code del bus di servizio](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-queues/)  
  
-   [Argomenti\/Sottoscrizioni del bus di servizio](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-bus-topics/)  
  
-   [Gestione del servizio](http://azure.microsoft.com/en-us/develop/python/how-to-guides/service-management/)  
  
 L'[open source di Azure SDK per Python](https://github.com/Azure/azure-sdk-for-python) contiene [unit test](https://github.com/Azure/azure-sdk-for-python/tree/master/tests) che sono anche un'ottima fonte di informazioni sulle API.  
  
 **Installazione:** [Indice del pacchetto Python](https://pypi.python.org/pypi/azure) per l'uso di PIP o per altre informazioni e [programmi di installazione eseguibili di Azure](http://azure.microsoft.com/en-us/documentation/articles/python-how-to-install/) che includono facoltativamente Python.  
  
## Calcolo scientifico  
 Oltre a tutte e librerie del data scientist Python, PTVS supporta IPython e IPython Notebook \(che è possibile ospitare in Azure\).  È necessario ottenere IPython e le librerie di calcolo scientifico \(matplotlib, scipy, numpy e così via\) da una distribuzione \(non PyPi\), ad esempio [UCI](http://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  Per informazioni complete sull'installazione e su come configurare PTVS, vedere [Installazione e introduzione.](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS)  
  
## Vedere anche  
 [Introduzione a PTVS: Impostazione di Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)   
 [Introduzione a PTVS: Avviare la codifica \(progetti\)](../python/getting-started-with-ptvs-start-coding-projects.md)   
 [Introduzione a PTVS: Modifica del codice](../python/getting-started-with-ptvs-editing-code.md)   
 [Introduzione a PTVS: Debug](../python/getting-started-with-ptvs-debugging.md)   
 [Introduzione a PTVS: Python interattivo](../python/getting-started-with-ptvs-interactive-python.md)   
 [Introduzione a PTVS: Compilazione di un sito Web in Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)