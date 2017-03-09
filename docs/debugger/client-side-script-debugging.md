---
title: "Debug di script sul lato client | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "debug [Visual Studio], script lato client"
  - "script lato client, debug"
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug di script sul lato client
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debugger di Visual Studio offre un ambiente di debug completo per l'individuazione e la correzione degli errori negli script lato client delle pagine ASP.NET.  
  
## Apertura di documenti di script  
 È possibile usare **Esplora soluzioni** per visualizzare elenchi di documenti script lato server e client. È possibile aprire qualsiasi documento di script da **Esplora soluzioni**. Per altre informazioni, vedere [Procedura: visualizzare documenti script](../debugger/how-to-view-script-documents.md).  
  
## Mapping dei punti di interruzione  
 In Visual Studio non è possibile eseguire direttamente il debug di codice lato server, ma è possibile impostare un punto di interruzione in un file lato server. Visual Studio esegue automaticamente il mapping del punto di interruzione a un percorso corrispondente del file lato client e crea un punto di interruzione associato nel codice lato client.  
  
## Connessione manuale o automatica a script  
 Per avviare il debug di script in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il debugger deve essere connesso allo script del quale si desidera eseguire il debug. Questa operazione può essere eseguita manualmente o automaticamente.  
  
 È possibile eseguire la connessione manualmente utilizzando l'interfaccia del debugger [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per scegliere il processo di script in esecuzione desiderato. Per altre informazioni, vedere [Procedura: connettersi a file script](../debugger/how-to-attach-to-script.md).  
  
 Il debugger si connette automaticamente allo script quando si verifica uno dei seguenti casi:  
  
-   Rilevamento di punti di interruzione impostati nello script.  
  
-   Rilevamento di un'istruzione `Stop` VBScript o un'istruzione `debugger` JScript nel codice script.  
  
-   Rilevamento di un errore di sintassi o di runtime nello script da parte del browser o del server. In tal caso, verrà visualizzata una finestra di dialogo con l'opzione per iniziare il debug.  
  
 In caso di connessione manuale allo script, l'esecuzione del processo di script continua fino a quando viene nuovamente arrestato. È possibile arrestarlo scegliendo **Interrompi** dal menu **Debug**.  
  
 Quando il debugger viene connesso automaticamente, l'esecuzione degli script viene arrestata nella riga dove si rileva il punto di interruzione, l'istruzione `Stop` o l'istruzione `debugger` o un errore, o nel punto scelto per iniziare il debug in Internet Explorer.  
  
 A tal punto, è possibile utilizzare le comuni utilità del debugger per iniziare il debug. Ad esempio, è possibile utilizzare i comandi **Esegui** per continuare a eseguire il codice riga per riga. Per visualizzare e controllare il flusso di script è possibile utilizzare la finestra **Stack di chiamate**. Per visualizzare o modificare le variabili e le proprietà utilizzare le finestre delle variabili o la finestra di **controllo immediato**.  
  
## Messaggi di errore avanzati per il debug di script  
 Visual Studio offre messaggi di errore avanzati per problemi di debug di script comuni. Questi messaggi vengono visualizzati solo in caso di connessione manuale a Internet Explorer. Se si verifica una condizione di errore all'apertura automatica di Internet Explorer, provare la connessione manuale in modo da poter vedere i messaggi di errore.  
  
## Debug di applicazioni script AJAX  
 Nelle applicazioni Web che supportano AJAX viene fatto largo uso di codice script e vengono poste serie problematiche di debug. Per informazioni sulle tecniche di debug AJAX, vedere  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md).  
  
## Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitazioni del debug di script](../debugger/limitations-on-script-debugging.md)   
 [Finestre delle variabili](../Topic/Variable%20Windows.md)   
 [Finestra di controllo immediato](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)