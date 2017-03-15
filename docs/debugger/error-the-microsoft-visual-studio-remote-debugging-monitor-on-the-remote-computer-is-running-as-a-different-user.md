---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor &#232; in esecuzione sul computer remoto come utente diverso | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "anyuser (opzione)"
  - "-anyuser (opzione)"
  - "msvsmon.exe"
  - "Remote Debugging Monitor"
  - "debug remoto, Remote Debugging Monitor"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: Microsoft Visual Studio Remote Debugging Monitor &#232; in esecuzione sul computer remoto come utente diverso
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:  
  
 Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso.  
  
## Causa  
 Questo messaggio viene visualizzato quando si esegue il debug in modalità Nessuna autenticazione e l'utente che ha avviato msvsmon non è lo stesso che esegue Visual Studio.  
  
## Soluzione  
 La soluzione ottimale, anche dal punto di vista della sicurezza, consiste nell'eseguire Remote Debugging Monitor \(msvsmon.exe\) utilizzando lo stesso account utente di Visual Studio.  Se non è possibile, eseguire Remote Debugging Monitor utilizzando l'altro account con l'opzione **Consenti di eseguire il debug a qualunque utente** nella finestra di dialogo **Opzioni** di Remote Debugging Monitor.  
  
> [!CAUTION]
>  Se si concede ad altri utenti l'autorizzazione per la connessione, è possibile che si verifichino problemi di connessione alla sessione di debug remoto errata.  Il debug in modalità **Nessuna autenticazione** non offre alcun livello di sicurezza e deve essere utilizzato con cautela.  
  
 Per ulteriori informazioni, vedere [Avvio di Remote Debugging Monitor](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  
  
## Vedere anche  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)