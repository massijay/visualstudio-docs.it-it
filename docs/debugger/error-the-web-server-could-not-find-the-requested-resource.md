---
title: "Errore: il server Web non &#232; in grado di trovare la risorsa richiesta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, errori dell'applicazione Web"
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Errore: il server Web non &#232; in grado di trovare la risorsa richiesta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ai fini della sicurezza, IIS ha restituito un errore generico.  
  
 Una causa possibile è la configurazione della sicurezza del server.  In IIS 6.0 e versioni precedenti veniva utilizzato un programma aggiuntivo, noto come URLScan, per filtrare le richieste sospette e non formattate correttamente.  In IIS 7.0 è predefinita una funzionalità di filtro delle richieste.  In entrambi i casi, una funzionalità di filtro delle richieste troppo restrittiva può impedire a Visual Studio di eseguire il debug del server.  
  
 Questo errore può essere avere numerose cause.  Alcune delle cause più comuni includono un problema di installazione o configurazione di IIS, di configurazione del sito Web o di autorizzazioni nel file system.  È possibile provare ad accedere alla risorsa con un browser.  A seconda della configurazione di IIS, potrebbe essere necessario utilizzare un browser locale nel server o analizzare il log degli errori di IIS per ottenere un messaggio di errore dettagliato.  
  
 Per ulteriori informazioni sulla risoluzione dei problemi di IIS, vedere [Gestione e amministrazione di IIS](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## Vedere anche  
 [Strumento di sicurezza UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Errore: il server Web è stato bloccato e blocca il verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)