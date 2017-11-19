---
title: "Errore: Microsoft Visual Studio Remote Debugging Monitor nel computer remoto è in esecuzione come utente diverso | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3f2c9e0b3f88734d21ae06f1af48409c58766a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Errore: Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso
Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:  
  
 Microsoft Visual Studio Remote Debugging Monitor è in esecuzione sul computer remoto come utente diverso.  
  
## <a name="cause"></a>Causa  
 Questo messaggio viene visualizzato quando si esegue il debug in modalità Nessuna autenticazione e l'utente che ha avviato msvsmon non è lo stesso che esegue Visual Studio.  
  
## <a name="solution"></a>Soluzione  
 La soluzione ottimale, anche dal punto di vista della sicurezza, consiste nell'eseguire Remote Debugging Monitor (msvsmon.exe) utilizzando lo stesso account utente di Visual Studio. Se non è, è possibile eseguire Remote Debugging Monitor utilizzando l'altro account con il **consentire agli utenti di eseguire il debug** opzione selezionata in Remote Debugging Monitor **opzioni** la finestra di dialogo.  
  
> [!CAUTION]
>  Se si concede ad altri utenti l'autorizzazione per la connessione, è possibile che si verifichino problemi di connessione alla sessione di debug remoto errata. Debug in **Nessuna autenticazione** modalità non è sicura e deve essere utilizzata con cautela.
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Debug remoto](../debugger/remote-debugging.md)