---
title: "Errore: il server Web non &#232; configurato in modo corretto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.remote.projnotconfigured"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, errori dell'applicazione Web"
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Errore: il server Web non &#232; configurato in modo corretto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alcune cause possibili di questo errore sono:  
  
-   Tentativo di eseguire il debug di un'applicazione Web .NET copiata in un computer diverso, rinominato manualmente o spostato.  
  
-   Indisponibilità di un numero sufficiente di connessioni IIS. Per altre informazioni su come distribuire un sito Web in IIS, vedere [Creare un sito Web](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Se si prova a eseguire il debug di un'applicazione ASP.NET, vedere [Pubblicazione in IIS](https://docs.asp.net/en/latest/publishing/iis.html) per istruzioni su come eseguire la distribuzione in un computer remoto che esegue IIS 8 o versione successiva oppure [Debug remoto di ASP.NET in un computer remoto con IIS 7.5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) per istruzioni su come eseguire la distribuzione in un computer remoto che esegue IIS 7.5.  
  
## Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)