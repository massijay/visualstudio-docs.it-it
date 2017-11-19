---
title: "Errore: Il computer remoto non è possibile avviare le comunicazioni DCOM | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 377211f0ca7e4095da58b169f113689db9c7b41e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Errore: il computer remoto non può avviare le comunicazioni DCOM
Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM. Il computer locale è il computer che  
  
 esegue Visual Studio. L'errore può essere determinato da numerose cause:  
  
-   Nel computer locale è stato attivato un firewall.  
  
-   L'autenticazione di Windows dal computer remoto al computer locale non funziona.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Se nel computer locale è abilitato Windows Firewall, vedere [il debug remoto](../debugger/remote-debugging.md) per istruzioni su come configurare il firewall per il debug locale.  
  
2.  Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.  
  
3.  Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer. Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)