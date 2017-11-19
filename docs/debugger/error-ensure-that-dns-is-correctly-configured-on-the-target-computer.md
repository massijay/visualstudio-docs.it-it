---
title: 'Errore: Assicurarsi che DNS sia configurato correttamente nel Computer di destinazione | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6711ae54c87e5e71a643fee3c019c8214294c09a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Errore: verificare che il DNS sia configurato correttamente nel computer di destinazione.
Quando si tenta di eseguire il debug remoto, potrebbe essere visualizzato il seguente messaggio di errore:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Questo errore si verifica quando il computer di destinazione non è in grado di risolvere il nome del computer host del debugger Visual Studio. Verificare le impostazioni DNS del computer di destinazione.  
  
-   Per informazioni sulla visualizzazione della configurazione del DNS in Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 o Windows Server 2008 R2, eseguire questa operazione: sul **avviare** menu, scegliere **Guida e supporto tecnico** , quindi cercare **impostazioni TCP/IP modifica**.  
  
-   Per ulteriori informazioni, visitare [sito web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) e cercare **impostazioni TCP/IP modifica**.  
  
 Se è possibile risolvere il problema DNS, è possibile provare a eseguire il debugger remoto con un account diverso. L'errore si verifica quando è in esecuzione il debugger remoto con l'account del sistema locale o l'account del servizio di rete. Se si esegue il debugger remoto con un altro account, è possibile usare l'autenticazione NTLM, che non richiede il DNS. . Per la procedura, vedere [errore: il servizio di Visual Studio Remote Debugger nel computer di destinazione non può connettersi a questo computer](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).