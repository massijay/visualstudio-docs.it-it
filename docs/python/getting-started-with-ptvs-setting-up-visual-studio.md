---
title: "Introduzione a PTVS: Impostazione di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-python"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec491c1d-bdb2-4c2b-a390-bd808cec635a
caps.latest.revision: 5
caps.handback.revision: 4
author: "kraigb"
ms.author: "kraigb"
manager: "ghogen"
---
# Introduzione a PTVS: Impostazione di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'installazione di PTVS e delle librerie correlate risulta più rapida se si dispone di Visual Studio.  Se non si dispone di Visual Studio, è possibile ottenere una copia gratuita di una versione di qualità professionale.  
  
 Queste istruzioni sono illustrate in un brevissimo [video youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).  
  
 I passaggi di alto livello prevedono l'installazione di Visual Studio, l'installazione di PTVS, l'installazione di Python e delle librerie dati \(Anaconda, Canopy\) e infine la verifica dell'installazione.  
  
 Il primo elemento necessario è Visual Studio.  I singoli sviluppatori o gli sviluppatori open source possono usare Visual Studio [Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs), che è gratuito e funzionale per i professionisti.  È possibile usare la Community Edition anche in un'organizzazione, purché sia usata per corsi di formazione, ricerca accademica o per contribuire allo sviluppo di progetti open source.  Gli studenti e le startup devono esaminare i programmi DreamSpark e BizSpark per verificare se possono ottenere l'accesso gratuito oppure è possibile chiedere al proprio datore di lavoro se si dispone di un abbonamento MSDN.  
  
 Dopo aver installato Visual Studio, sarà necessario [installare PTVS](http://pytools.codeplex.com/wikipage?title=PTVS%20Installation).  Si tratta di un'estensione autonoma gratuita, che è completamente supportata da Microsoft e sviluppata apertamente con i contributi della community.  
  
 È necessario ora [installare Python](http://python.org/download/).  Python è completamente gestito dalla community e la relativa home page è python.org.  Continuum Analytics produce un bundle gratuito chiamato Anaconda che contiene Python e molte librerie utili \(soprattutto per l'elaborazione dati e il data science\) ed Enthought rilascia Canopy che è un bundle simile.  È necessario installarne solo uno dei due.  Se non si è certi di quale installare, iniziare con [Anaconda](http://continuum.io/downloads), che contiene la versione aggiornata di Python e la maggior parte dei pacchetti difficili da installare.  
  
 Avviare Visual Studio e verificare che tutto funzioni.  Scegliere Altre finestre dal menu Visualizza.  Verrà visualizzato un elemento denominato ambienti Python.  Questa finestra visualizza tutte le installazioni di Python rilevate da PTVS e tutti i pacchetti installati.  La finestra controlla anche l'aggiornamento del database per la visualizzazione dei completamenti durante la modifica del codice.  Questo processo di aggiornamento richiede un po' di tempo e una quantità elevata di CPU e memoria, ma al termine PTVS può visualizzare informazioni più utili sui pacchetti.  
  
 Se si desidera usare IPython con PTVS, seguire queste [istruzioni](http://pytools.codeplex.com/wikipage?title=Using%20IPython%20with%20PTVS).  
  
 Queste istruzioni sono illustrate in un brevissimo [video youtube](https://www.youtube.com/watch?v=_okUV47eM5c&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=1).  
  
## Vedere anche  
 [Video di introduzione e approfondimento di PTVS](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)