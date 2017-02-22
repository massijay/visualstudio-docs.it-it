---
title: "Errore: impossibile eseguire automaticamente l&#39;istruzione sul server | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug remoto, errore di notifica"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: impossibile eseguire automaticamente l&#39;istruzione sul server
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il testo del messaggio di errore è il seguente:  
  
 Impossibile eseguire automaticamente l'istruzione sul server. Il debugger non ha ricevuto alcuna notifica prima dell'esecuzione della routine remota.  
  
 Questo errore può verificarsi quando si tenta di eseguire un servizio Web. Per altre informazioni, vedere [Accesso a un servizio Web XML](http://msdn.microsoft.com/it-it/8e67de38-bf5f-41cc-a457-1b88ce63d764). L'errore è dovuto a una configurazione non corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 Possibili cause:  
  
-   Nel file web.config dell'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non viene impostato il debug su "true" \(vedere [Modalità debug nelle applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)\).  
  
-   Una versione di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è stata installata dopo l'installazione di Visual Studio. Installare [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] prima di Visual Studio. Per risolvere il problema, accedere al **Pannello di controllo** di Windows e scegliere **Programmi e funzionalità** per ripristinare l'installazione di Visual Studio.  
  
## Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)