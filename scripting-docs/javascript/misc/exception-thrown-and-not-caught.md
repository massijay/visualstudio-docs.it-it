---
title: "Eccezione generata e non intercettata | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5022"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Eccezione generata e non intercettata
Un'istruzione `throw` è stata inclusa nel codice, ma non è stata racchiusa in un blocco **try** o non era presente alcun blocco **catch** associato per intercettare l'errore.  Le eccezioni vengono generate all'interno del blocco **try** mediante l'istruzione **throw** e vengono intercettate all'esterno del blocco **try** con un'istruzione **catch**.  
  
### Per correggere l'errore  
  
-   Racchiudere il codice che può generare un'eccezione in un blocco **try** e verificare l'esistenza di un blocco **catch** corrispondente.  
  
-   Assicurarsi che l'istruzione catch preveda la forma corretta di eccezione.  
  
-   Se l'eccezione viene generata nuovamente, assicurarsi che sia presente un'altra istruzione catch corrispondente.  
  
## Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)   
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)