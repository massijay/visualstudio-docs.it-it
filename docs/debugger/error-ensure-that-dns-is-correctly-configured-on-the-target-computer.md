---
title: "Errore: verificare che il DNS sia configurato correttamente nel computer di destinazione. | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: verificare che il DNS sia configurato correttamente nel computer di destinazione.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Questo errore si verifica quando il computer di destinazione non è in grado di risolvere il nome del computer host del debugger Visual Studio.  Verificare le impostazioni DNS del computer di destinazione.  
  
-   Per informazioni sulla visualizzazione della configurazione del DNS in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 oppure Windows Server 2008 R2, fare clic sul pulsante **Start**, scegliere **Guida e supporto tecnico** e quindi cercare le impostazioni di modifica TCP\/IP.  
  
-   Per altre informazioni visitare il [sito Web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) e cercare le impostazioni di modifica TCP\/IP.  
  
 Se è possibile risolvere il problema DNS, è possibile provare a eseguire il debugger remoto con un account diverso.  L'errore si verifica quando è in esecuzione il debugger remoto con l'account del sistema locale o l'account del servizio di rete.  Se si esegue il debugger remoto con un altro account, è possibile usare l'autenticazione NTLM, che non richiede il DNS.  .  Per questa procedura vedere [Errore: il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).