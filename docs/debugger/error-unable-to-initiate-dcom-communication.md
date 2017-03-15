---
title: "Errore: impossibile avviare la comunicazione DCOM | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_server_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: impossibile avviare la comunicazione DCOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si è verificato un errore DCOM quando il computer locale ha tentato di comunicare con il computer remoto.  Questo errore è causato dalla presenza di un firewall nel server remoto oppure dall'interruzione dell'autenticazione di Windows nel computer remoto.  
  
### Per correggere l'errore  
  
-   Se nel computer remoto è abilitato Windows Firewall, vedere [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) per le istruzioni di configurazione del firewall per il debug locale.  
  
-   Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer.  Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)