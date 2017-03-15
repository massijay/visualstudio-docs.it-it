---
title: "Debug di F# | Microsoft Docs"
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
helpviewer_keywords: 
  - "Debug [F#]"
  - "F#, debug"
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug di F# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug di F \#è simile al debug di qualsiasi linguaggio gestito, con alcune eccezioni:  
  
-   Nella finestra **Auto** non vengono visualizzate le variabili F\#.  
  
-   La modifica e la continuazione non sono supportate per F\#.  La modifica del codice F\# durante una sessione di debug è possibile ma deve essere evitata.  Poiché le modifiche al codice non vengono applicate durante la sessione di debug, la modifica del codice F\# durante il debug provocherà una mancata corrispondenza tra il codice sorgente e il codice in fase di debug.  
  
-   Il debugger non riconosce le espressioni F\#.  Per immettere un'espressione in una finestra o una finestra di dialogo del debugger durante il debug di F\#, è necessario tradurre l'espressione nella sintassi C\#.  Quando si traduce un'espressione F\# in C\#, ricordare che C\# utilizza \=\= come operatore di confronto per uguaglianza e che F\# utilizza un solo \=.  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)