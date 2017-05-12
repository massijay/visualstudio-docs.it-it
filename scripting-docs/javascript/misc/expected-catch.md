---
title: "Previsto &#39;catch&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1033"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Previsto &#39;catch&#39;
Hai utilizzato il blocco **try**  di gestione delle eccezioni, ma non hai scritto l'istruzione collegata **catch**.  Il meccanismo di gestione delle eccezioni richiede che insieme al codice che non deve essere eseguito se si verifica un'eccezione, venga eseguito il wrapping del codice che può generare un errore in un blocco **try**.  Le eccezioni vengono generate dal blocco **try** mediante l'istruzione **throw** e vengono intercettate all'esterno del blocco **try** con una o più istruzioni **catch** .  
  
### Per correggere l'errore  
  
-   Aggiungere il blocco collegato **catch** .  
  
-   Provare a utilizzare un blocco **finally** anziché un blocco **catch**.  
  
## Vedere anche  
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)