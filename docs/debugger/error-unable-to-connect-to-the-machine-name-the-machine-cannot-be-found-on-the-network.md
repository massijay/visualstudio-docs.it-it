---
title: "Errore: impossibile connettersi al computer &lt;nome&gt;. Impossibile trovare il computer nella rete. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, Impossibile connettersi (errore)"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Errore: impossibile connettersi al computer &lt;nome&gt;. Impossibile trovare il computer nella rete.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questo messaggio di errore viene visualizzato quando si verifica una delle seguenti condizioni:  
  
-   La connessione stabilita al computer remoto è stata interrotta.  
  
-   L'account utente utilizzato per la connessione al computer remoto è stato disabilitato.  
  
-   La password utilizzata per la connessione al computer remoto è scaduta.  
  
### Per risolvere questo comportamento  
  
-   Assicurarsi che il computer locale e il computer remoto si trovino nella stessa rete.  A tale scopo, utilizzare Esplora risorse o Esplora file per tentare di accedere al computer remoto.  
  
     \- e \-  
  
-   Assicurarsi che l'account utente utilizzato per la connessione al computer remoto sia attivato.  
  
     \- e \-  
  
-   Assicurarsi che la password utilizzata per la connessione al computer remoto sia valida e non scaduta.  
  
## Vedere anche  
 [Impostare Remote Tools sul dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)