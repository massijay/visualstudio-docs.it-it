---
title: "Procedura: eseguire il debug di client e server COM mediante il debug RPC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "client COM, debug"
  - "COM (server), debug"
  - "COM, debug"
  - "debug di RPC in-process"
  - "debug di RPC out-of-process"
  - "debug remoto, RPC (Remote Procedure Call)"
  - "RPC (Remote Procedure Call)"
  - "RPC (Remote Procedure Call), debug"
  - "RPC (Remote Procedure Call), debug di client e server COM"
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: eseguire il debug di client e server COM mediante il debug RPC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare il debug RPC \(Remote Procedure Call, chiamata a procedura remota\) per eseguire il debug delle applicazioni client\/server COM.  Per utilizzare tale debug, è necessario attivarlo.  Quando si chiama il server dal client con il debug RPC attivato, il debugger si connette al server e consente di eseguire il debug del codice.  Una volta stabilita la connessione al server, è possibile utilizzare tutte le funzionalità del debugger per i processi del client e del server.  
  
### Per attivare il debug RPC  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** fare clic sulla cartella **Debug**.  
  
3.  Fare clic sulla pagina **Nativo**.  
  
4.  Selezionare la casella di controllo **Debug RPC**.  
  
    > [!NOTE]
    >  Per eseguire il debug delle chiamate RPC, è necessario disporre dei privilegi di tipo Administrator o Power User.  
  
    > [!NOTE]
    >  L'esecuzione di chiamate RPC a un server remoto che esegue Microsoft Windows Vista funzionerà solo se un debugger nativo è connesso al server remoto.  In caso contrario, la chiamata RPC non verrà eseguita senza restituire alcun messaggio di errore  oppure verrà completata, ma non funzionerà.  
  
## Vedere anche  
 [Debug dei server e dei contenitori COM](../debugger/com-server-and-container-debugging.md)   
 [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)