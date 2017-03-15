---
title: "Errore: il computer remoto non pu&#242; avviare le comunicazioni DCOM | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_callback_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: il computer remoto non pu&#242; avviare le comunicazioni DCOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando il computer remoto ha tentato di comunicare con il computer locale si è verificato un errore DCOM.  Il computer locale è il computer che  
  
 esegue Visual Studio.  L'errore può essere determinato da numerose cause:  
  
-   Nel computer locale è stato attivato un firewall.  
  
-   L'autenticazione di Windows dal computer remoto al computer locale non funziona.  
  
### Per correggere l'errore  
  
1.  Se nel computer locale è abilitato Windows Firewall, vedere [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) per le istruzioni di configurazione del firewall per il debug locale.  
  
2.  Testare l'autenticazione di Windows tentando di aprire una condivisione di file nel computer locale dal server remoto.  
  
3.  Per ripristinare l'autenticazione di Windows, provare a riavviare entrambi i computer.  Controllare se nel log eventi del computer locale e di quello remoto sono segnalati errori di Kerberos e contattare gli amministratori di dominio in caso di problemi noti.  
  
## Vedere anche  
 [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)