---
title: "Debug di applicazioni ASP.NET e AJAX | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
  - "debug [ASP.NET], informazioni sul debug di ASP.NET"
  - "debug di applicazioni Web ASP.NET"
  - "debug, WCF"
  - "WCF, debug"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug di applicazioni ASP.NET e AJAX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug di applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è simile a quello di Windows Form o qualsiasi altra applicazione Windows poiché entrambi i tipi di applicazione impiegano controlli ed eventi.  Tuttavia, esistono anche differenze sostanziali tra i due tipi di applicazioni:  
  
-   Tenere traccia dello stato è un'operazione più complessa in un'applicazione Web.  
  
-   In un'applicazione Windows, il codice di cui eseguire il debug si trova essenzialmente in un punto, mentre per un'applicazione Web il codice può essere sul client e sul server.  Mentre il codice [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è tutto sul server, il codice JavaScript o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] potrebbe trovarsi anche sul client.  
  
## In questa sezione  
 [Preparazione al debug di ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Vengono descritti i passaggi necessari per attivare il debug di applicazioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Debug di applicazioni Web](../debugger/debugging-web-applications.md)  
 Viene discusso come eseguire il debug di un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], incluse le applicazioni script compatibili con AJAX.  
  
## Sezioni correlate  
 [Gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md)  
 Viene spiegato perché è necessario attivare l'opzione Just My Code per il debug di eccezioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 Vengono illustrati alcuni strumenti e tecniche che possono agevolare il debug del codice AJAX.  
  
 [Utilizzo di IntelliTrace](../debugger/intellitrace.md)  
 Eseguire il debug del codice più rapidamente utilizzando IntelliTrace per registrare e verificare la cronologia dello stato dell'applicazione senza riavviare l'applicazione con frequenza.  È possibile visualizzare le informazioni sugli eventi e le chiamate che si verificano durante l'esecuzione dell'applicazione e avviare il debug da questi punti nel tempo.  Richiede Visual Studio Ultimate.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)